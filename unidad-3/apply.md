# Unidad 3


## 🛠 Fase: Apply

### 📚 Actividad 06 - Crear la bomba en p5.js   
[🌟 Ver mi programa en p5.js](https://editor.p5js.org/VanDiosa/sketches/4kntLSOGZ)

🌟Codigo del programa en p5.js
```javascript
// ESTADO DE LA BOMBA - equivale a class BombTask: def __init__(self)
let password = ['A','B','A'];
let keyEntered = []; // clave ingresada
let keyIndex = 0; // indice clave
let count = 20;
let startTime;
let state = "CONFIG"; // estado inicial

function setup () { // tmb de class BombTask: def __init__(self)
  createCanvas(400, 400); 
  background(220);
  startTime = millis();
  textAlign(CENTER, CENTER);
  textSize(40)
}

function draw () { // def update(self)
  background(0);
  
  if (state === "CONFIG") { // ESTADO
    fill(0, 0, 200);
    text("⚙️CONFIG⚙️", width / 2, height / 3);
    text(count, width / 2, height / 2);
  }
  
  else if (state === "ARMED") { // ESTADO
    fill(200, 0, 0);
    text("💣ARMED💣", width / 2, height / 3);

    if (millis() - startTime > 1000) { // cada segundo baja el contador
      count--; //
      startTime = millis();
    }

    text(count, width / 2, height / 2);

    if (count <= 0) {
      state = "EXPLODED";
    }
  }

  else if (state === "EXPLODED") {// ESTADO
    fill(0, 200, 0);
    text("💀 EXPLODED 💀", width / 2, height / 2);
  }
  
}


function keyPressed() { // equivalente a class ButtonTask
  let k = key.toUpperCase(); // convierte la tecla a mayuscula siempre
  if (state === "CONFIG") { // === es comparacion estricta
    if (k === 'A') {
      count = min(count + 1, 60); // lo de min es tipo menor que, numero_actual = min(numero_actual + 1, 60)
    }
    if (k === 'B') {
      count = max(count - 1, 10);
    }
    if (k === 'S') { // shake
      state = "ARMED";
      startTime = millis();
    }
  }
  
  else if (state === "ARMED") {
    if (k === 'A' || k === 'B') {
      passwordInput(k);
    }
  }
  
  else if (state === "EXPLODED") {
    if (k === 'R') { // volver a config
      count = 20;
      state = "CONFIG";
      startTime = millis();
    }
  }
}

// FUNCION PARA MANEJAR LA CLAVE
function passwordInput(k) {
  keyEntered [keyIndex] = k;
  keyIndex++;

  if (keyIndex === password.length) {
    let passIsOK = true;
    for (let i = 0; i < password.length; i++) {
      if (keyEntered [i] !== password[i]) {
        passIsOK = false;
        break;
      }
    }

    if (passIsOK) {
      count = 20;
      state = "CONFIG";
    }
    // reinicia la secuencia siempre
    keyIndex = 0;
    keyEntered  = [];
  }
}
```

### 📚 Actividad 07 - Bomba en p5.js + controles del micro:bit    
[🌟 Ver mi programa en p5.js](https://editor.p5js.org/VanDiosa/sketches/cOxq7s-EG)

🌟Codigo del programa en p5.js   
```javascript
// ESTADO DE LA BOMBA
let state = "CONFIG";      // "CONFIG", "ARMED", "EXPLODED"
let count = 20;            // tiempo de la bomba
let startTime;             // para medir el tiempo
let password = ['A','B','A'];
let keyBuffer = [];        // secuencia ingresada
let keyIndex = 0;

//WEB SERIAL
let serial;        // instancia de p5.WebSerial
let portButton;    // boton elegir puerto


function setup() {
  createCanvas(400, 400);
  textAlign(CENTER, CENTER);
  textSize(32);
  startTime = millis();
  
  serial = new p5.WebSerial();    // crear objeto serie    
  
  // DETECCION DE CONECTAR Y DESCONECTAR DIPOSITIVOS
  navigator.serial.addEventListener("connect", portConnect);
  navigator.serial.addEventListener("disconnect", portDisconnect);
  
  // VER PUERTOS DISPONIBLES
  serial.getPorts();
  serial.on("noport", makePortButton);   // si no hay puerto seleccionado, muestra el boton
  serial.on("portavailable", openPort);  // si hay un puerto, lo abre
  serial.on("requesterror", portError);
  serial.on("data", onSerialData);       // cuando llega datos, lee una linea
  serial.on("close", makePortButton);    // si se cierra, vuelve a mostrar el boton
}

function draw() {
  background(0);

  if (state === "CONFIG") {
    fill(0, 200, 0);
    text("CONFIG", width / 2, height / 3);
    text(count, width / 2, height / 2);
  }

  else if (state === "ARMED") {
    fill(255, 200, 0);
    text("ARMED", width / 2, height / 3);

    // cada segundo bajar el contador
    if (millis() - startTime > 1000) {
      count--;
      startTime = millis();
    }

    text(count, width / 2, height / 2);

    if (count <= 0) {
      state = "EXPLODED";
    }
  }

  else if (state === "EXPLODED") {
    fill(255, 0, 0);
    text("💀 EXPLODED 💀", width / 2, height / 2);
  }
}

// BOTON ELEGIR PUERTO
function makePortButton() {
  if (!portButton) {
    portButton = createButton("Elegir puerto");
    portButton.position(10, 10);
    portButton.mousePressed(() => serial.requestPort());
  } else {
    portButton.show();
  }
}

function openPort() {
  serial.open({ baudRate: 115200 }).then(() => { // Micro:bit en MicroPython suele ir a 115200
    console.log("Puerto abierto");
  });
  if (portButton) portButton.hide();
}

function portConnect() {
  console.log("Dispositivo conectado");
  serial.getPorts();
}

function portDisconnect() {
  console.log("Dispositivo desconectado");
  serial.close();
}

function portError(err) {
  alert("Error de puerto: " + err);
}


// LECTURA PARA EL MICROBIT
function onSerialData() {
  let line = serial.readLine();   // lee lo recibido por el microbit hasta \n (salto de linea)
  if (!line) return;
  line = line.trim().toUpperCase(); // A, B, S, R...

  // Despacha como si fueran teclas del micro:bit
  if (line === "A" || line === "B" || line === "S" || line === "R") {
    keyPressedMicro(line);
  }
}

// CONTROL PARA EL TECLADO
function keyPressed() {
  let k = key.toUpperCase();

  if (state === "CONFIG") {
    if (k === 'A') {
      count = min(count + 1, 60);
    }
    if (k === 'B') {
      count = max(count - 1, 10);
    }
    if (k === 'S') { // simula el "shake"
      state = "ARMED";
      startTime = millis();
    }
  }

  else if (state === "ARMED") {
    if (k === 'A' || k === 'B') {
      passwordInput(k);
    }
  }

  else if (state === "EXPLODED") {
    if (k === 'R') { // reset
      count = 20;
      state = "CONFIG";
      startTime = millis();
    }
  }
}

// CONTROL PARA EL MICROBIR
function keyPressedMicro(k) {
  if (state === "CONFIG") {
    if (k === 'A') {
      count = min(count + 1, 60);
    }
    if (k === 'B') {
      count = max(count - 1, 10);
    }
    if (k === 'S') { // agitar = iniciar bomba
      state = "ARMED";
      startTime = millis();
    }
  }

  else if (state === "ARMED") {
    if (k === 'A' || k === 'B') {
      passwordInput(k);
    }
  }

  else if (state === "EXPLODED") {
    if (k === 'R') { // reset
      count = 20;
      state = "CONFIG";
      startTime = millis();
    }
  }
}


// FUNCION PARA MANEJAR LA CLAVE
function passwordInput(k) {
  keyBuffer[keyIndex] = k;
  keyIndex++;

  if (keyIndex === password.length) {
    let passIsOK = true;
    for (let i = 0; i < password.length; i++) {
      if (keyBuffer[i] !== password[i]) {
        passIsOK = false;
        break;
      }
    }

    if (passIsOK) {
      count = 20;
      state = "CONFIG";
    }
    // reiniciar secuencia siempre
    keyIndex = 0;
    keyBuffer = [];
  }
}
```

🌟Codigo del micro:bit
```python
from microbit import *

uart.init(baudrate=115200)

while True:
    if button_a.was_pressed():
        uart.write("A\n")   # subir tiempo
    if button_b.was_pressed():
        uart.write("B\n")   # bajar tiempo
    if accelerometer.was_gesture("shake"):
        uart.write("S\n")   # armar (iniciar cuenta)
    # opcional: reset con logo
    if pin_logo.is_touched():
        uart.write("R\n")
        sleep(300)
```
