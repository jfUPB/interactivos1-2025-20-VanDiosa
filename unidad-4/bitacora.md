# Evidencias de la unidad 4

## Código

[Enlace a la aplicación a modificar](https://editor.p5js.org/generative-design/sketches/P_2_0_03)

Código a modificar:

``` js
// P_2_0_03
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

/**
 * drawing with a changing shape by draging the mouse.
 *
 * MOUSE
 * position x          : length
 * position y          : thickness and number of lines
 * drag                : draw
 *
 * KEYS
 * 1-3                 : stroke color
 * del, backspace      : erase
 * s                   : save png
 */
'use strict';

var strokeColor;

function setup() {
  createCanvas(720, 720);
  colorMode(HSB, 360, 100, 100, 100);
  noFill();
  strokeWeight(2);
  strokeColor = color(0, 10);
}

function draw() {
  if (mouseIsPressed && mouseButton == LEFT) {
    push();
    translate(width / 2, height / 2);

    var circleResolution = int(map(mouseY + 100, 0, height, 2, 10));
    var radius = mouseX - width / 2;
    var angle = TAU / circleResolution;

    stroke(strokeColor);

    beginShape();
    for (var i = 0; i <= circleResolution; i++) {
      var x = cos(angle * i) * radius;
      var y = sin(angle * i) * radius;
      vertex(x, y);
    }
    endShape();

    pop();
  }
}

function keyReleased() {
  if (keyCode == DELETE || keyCode == BACKSPACE) background(0, 0, 100);
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');

  if (key == '1') strokeColor = color(0, 10);
  if (key == '2') strokeColor = color(192, 100, 64, 10);
  if (key == '3') strokeColor = color(52, 100, 71, 10);
}

```

[Enlace a la aplicación modificada](https://editor.p5js.org/VanDiosa/sketches/Gl-causBp)

Código modificado:

``` js
/**
ACELERÓMETRO
 En x: Radio o tamaño de la figura
 En y: # de lados de la figura
 
BOTONES
 A: Funciona como el click izq, se usa para dibujar
 B: Si se mantiene presionado, el color base (que era negro) se cambia a color azul. Luego del primer cambio a azul, mientras el boton este libre el color de las lineas sera amarillo
*/

'use strict';

// ======================VARIABLES GLOBALES======================

var strokeColor; // vrble para el color de la linea

// vrbles para la comunicacion serial: 
let port; // objeto conexion serial
let connectBtn; // ''  boton interfaz
let microBitConnected = false;
let connectionInitialized = false;

// vrbles para los datos del microbit:
let microBitX = 0; // acelerometro en X
let microBitY = 0; // '' en Y
let microBitAState = false; // boton A estado actual
let microBitBState = false; // boton B '' ''
let prevmicroBitAState = false; // boton A estado anterior
let prevmicroBitBState = false; // boton B '' ''

// def de los estados de la aplicacion:
const STATES = {
  WAIT_MICROBIT_CONNECTION: "WAITMICROBIT_CONNECTION",
  RUNNING: "RUNNING",
};
let appState = STATES.WAIT_MICROBIT_CONNECTION; // estado inicial

// ======================FUNCIONES PRINCIPALES======================

// funcion boton de conexion
function connectBtnClick() { // funcion al dar clic al boton
  if (!port.opened()) { // abre o cierra el puerto serial
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}

function setup() { // se ejecuta una vez al inicio
  createCanvas(720, 720);
  colorMode(HSB, 360, 100, 100, 100);
  noFill(); // formas sin relleno
  strokeWeight(2); // grosor de las lineas
  strokeColor = color(0, 10); // color inicial de las lineas
  
  // configuracion de la conexion serial
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit"); // se crea el boton
  connectBtn.position(10, 10); // se posiciona
  connectBtn.mousePressed(connectBtnClick); // se le asigna la funcion
}

function draw() {  //se ejecuta continuamente
  // estado del boton de conexion:
  if (!port.opened()) { //si el puerto NO esta abierto
    connectBtn.html("Connect to micro:bit");
    microBitConnected = false;
  } else {
    microBitConnected = true;
    connectBtn.html("Disconnect");

    if (port.opened() && !connectionInitialized) { // si el puerto esta abierto y NO esta conectado
      port.clear();
      connectionInitialized = true;
    }

    // lectura de los datos del microbit:
    if (port.availableBytes() > 0) {
      let data = port.readUntil("\n"); // lee hasta un salto de linea
      if (data) {
        data = data.trim(); // eliminar espacios en blanco
        let values = data.split(","); //separa la cadena de texto recibida en una de valores
        if (values.length == 4) { // se verifica q se recibieron los 4 datos y se convierten 
          microBitX = int(values[0]); // enteros
          microBitY = int(values[1]);
          microBitAState = values[2].toLowerCase() === "true"; // booleano
          microBitBState = values[3].toLowerCase() === "true";
          updateButtonStates(microBitAState, microBitBState); // se llama la funcion del manejo de los botones
        } 
        else {
          print("No se están recibiendo 4 datos del micro:bit");
        }
      }
    }
  }

  // logica de la maquina de estados:
  switch (appState) {
    case STATES.WAIT_MICROBIT_CONNECTION:
      if (microBitConnected === true) {
        print("Micro:bit conectado, cambiando a estado RUNNING");
        appState = STATES.RUNNING; // si el microbit se conecta, cambio de estado
      }
      break;

    case STATES.RUNNING:
      if (microBitConnected === false) {
        print("Micro:bit desconectado, volviendo a estado WAIT_MICROBIT_CONNECTION");
        appState = STATES.WAIT_MICROBIT_CONNECTION; // si el microbit se desconecta, volvemos al estado de espera
      }

      if (microBitAState === true) { // reemplazamos 'mouseIsPressed && mouseButton == LEFT' con 'microBitAState'. boton A presionado, se dibuja
        push(); // guarda el estado actual del lienzo
        translate(width / 2, height / 2); // movemos el punto de origen al centro del lienzo

        var circleResolution = int(map(microBitY, -1024, 1024, 2, 10)); // inclinacion en y, # de lados de la figura.  map(): escalar. 2:linea 10:decalogo.
        var radius = map(microBitX, -1024, 1024, 0, width / 2); // inclinacion en x, radio o tamaño de la figura
        var angle = TAU / circleResolution; // angulo entre vertices. TAU: 2pi o sea circulo completo / numero de lados

        stroke(strokeColor); // color de la linea

        beginShape(); // comienza a dibujar forma
        for (var i = 0; i <= circleResolution; i++) {
          var x = cos(angle * i) * radius;
          var y = sin(angle * i) * radius;
          vertex(x, y); // +1 vertice
        }
        endShape(); // termina de dibujar forma
cl
        pop(); // restaura el estado del lienzo guardado
      }
      break;
  }
}

// ======================FUNCIONES DE EVENTOS======================

function updateButtonStates(newAState, newBState) { // detectar cambios en el estado de los botones A y B del microbit, A es para dibujar y B para cambios de color

  if (newBState === true && prevmicroBitBState === false) { // boton B presionado, reemplaza la tecla 2
    strokeColor = color(192, 100, 64, 10);
    print("Botón B presionado: color 2");
  }

  if (newBState === false && prevmicroBitBState === true) { // boton B libre, reemplaza la tecla 3
    strokeColor = color(52, 100, 71, 10);
    print("Botón B liberado: color 3");
  }

  // actualizacion de los estados para el proximo ciclo
  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}

function keyReleased() { // se ejecuta cuando una tecla es liberada
  if (keyCode == DELETE || keyCode == BACKSPACE) background(0, 0, 100);
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
}
```

## Video

[Video demostrativo](https://www.youtube.com/watch?v=ud8JtxL-RI4)






