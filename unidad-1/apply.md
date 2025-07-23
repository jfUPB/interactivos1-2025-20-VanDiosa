# Unidad 1

## 🛠 Fase: Apply

### 📚 Actividad 05 - Interacción básica con micro:bit
💡En tu bitácora: explica cómo funciona el sistema físico interactivo que acabamos de crear.

Para el MICRO BIT
+ Inputs:
  + El boton A
+ Outputs:
  + Informacion serial que se envia al PC
+ Procesamiento: Revisar o leer si el boton se esta presionando, en caso tal envia A y de lo contrario envia N
  
Para el PC
+ Inputs:
  + Boton conectar al micro:bit
  + Informacion recibida por el serial
+ Outputs:
  + El cambio de color del cuadrado, rojo si le llego A y verde si le llego N
+ Procesamiento: Se lee la informacion recibida y cambia el output dependiendo de la letra que le llego


### 📚 Actividad 06 - Control de movimiento con micro:bit
[🌟 Ver mi programa en p5.js](https://editor.p5js.org/VanDiosa/sketches/y62ebcBxG)

🌟Codigo del programa en p5.js
```javascript
let port; 
let connectBtn; 
let connectionInitialized = false;
let posInitX=200 //posicion inicial del circulo

function setup() {
    createCanvas(400, 400); 
    background(220); 
    port = createSerial(); 
    connectBtn = createButton('Connect to micro:bit'); 
    connectBtn.position(80, 300); 
    connectBtn.mousePressed(connectBtnClick); 
}

function draw() {
  background(220);
  
    if (port.opened() && !connectionInitialized) { 
      port.clear();
      connectionInitialized = true;
    }
  
  if (port.availableBytes() > 0) { 
      let dataRx = port.read(1); 
      if (dataRx == "A") {
        posInitX -= 10 //restarle 10 a la vrble global 
      } else if (dataRx == "B") {
        posInitX += 10 //sumarle 10 a la vrble global
      }
    }
  
  ellipse(posInitX, height / 2, 50); // posicion en x, posicion en y, diametro
  fill("purple");
  
  if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  
}
  
  
function connectBtnClick() {
    if (!port.opened()) { 
        port.open('MicroPython', 115200); 
        connectionInitialized = false; 
    } else {
        port.close();
    }
}
```

🌟Codigo del micro:bit
```python
from microbit import *

uart.init(baudrate=115200)
display.show(Image.COW) #para verificar si la informacion si esta funcionando

while True:
    if button_a.is_pressed():
        uart.write('A') 
    elif button_b.is_pressed():
        uart.write('B') 
    sleep(100)
```

