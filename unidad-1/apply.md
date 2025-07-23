<img width="539" height="31" alt="image" src="https://github.com/user-attachments/assets/46a4de91-6f10-44b8-b960-3411b3b3c2d4" /># Unidad 1

## 🛠 Fase: Apply

### 📚 Actividad 05 - Interacción básica con micro:bit
💡En tu bitácora: explica cómo funciona el sistema físico interactivo que acabamos de crear.

Para el MICRO BIT
+ Inputs:
  + 
+ Outputs:
  + 
+ Proceso: 
  
Para el PC
+ Inputs:
  + 
+ Outputs:
  + 
+ Proceso: 


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

