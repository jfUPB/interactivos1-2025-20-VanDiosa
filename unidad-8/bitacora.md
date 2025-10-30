
# Evidencias de la unidad 8

## 🔎 Fase: Seek

### 📚Actividad 01   

#### 🧐 Referencias    
Como referencia y punto de partida inicial tome el proyecto de la unidad anterior que se ve asi:     
<img width="316" height="313" alt="Captura de pantalla 2025-10-17 002443" src="https://github.com/user-attachments/assets/e0b85b40-1e8c-4cc0-89e8-8183766e8bda" />
<img width="312" height="310" alt="Captura de pantalla 2025-10-17 002430" src="https://github.com/user-attachments/assets/6caa89e4-f476-4514-b7df-de5475138f6e" />

En esta nueva version, para la interfaz del movil, me gustaria añadir un boton deslizante para el cambio de 3 espectros a 1, no se pq pero me imagino algo como el modificador de tipo de cuerpo de la opcion de editar avatar en roblox:
<img width="858" height="465" alt="Captura de pantalla 2025-10-24 104357" src="https://github.com/user-attachments/assets/01218d85-3fcb-4b12-b420-61cf7d9276fe" />

En el desktop me gustaria que al sacudir el microbit salieran y se expandieran un tipo ondas. Y si lo logro me gustaria que fueran brillantes
<img width="320" height="341" alt="videoframe_27" src="https://github.com/user-attachments/assets/7022de77-2618-424e-a5bb-d87f0db7e85e" />
<img src="https://github.com/user-attachments/assets/670049c6-bbd6-41b6-a863-40a5f5f1c57b" width="400" />

#### 🧐 Concepto    
El visualizador interactivo Pulse of BTS esta inspirado en Black Swan y Fake Love de BTS:
+ En el modo Black Swan se muestran tres circulos concentricos que representan las capas del sonido (voz altos y bajos) reaccionando al ritmo de la cancion
+ En Fake Love la cancion se cambia y el fondo pasa de azul oscura a un tono magenta transformando de esa forma la atmosfera visual

Desde el celular el usuario puede deslizar horizontalmente para cambiar la paleta de colores y verticalmente para modificar la distancia entre los espectros fusionandolos. Con el microbit se podra alternar entre canciones con los botones A y B y al detectar movimiento con el acelerometro generar destellos tipo explosion expandiendo ondas luminosas desde el centro

#### 🧐 Explicación control movil y microbit
Movil-Touch: 
+ Deslizamiento horizontal: cambia la gama de colores de los espectros
+ Deslizamiento vertical: fusiona o separa las capas (de tres espectros a uno)

Microbit:
+ Boton A: cambia la musica de Black Swan a Fake Love, variando de un fondo azul oscuro a uno magenta
+ Boton B: regresa al modo Black Swan
+ Acelerometro: al detectar movimiento, emite unos aros de luz que parten desde el centro de los espectros y se expande en el lienzo

#### ✍️ Bocetos    
Este es el boceto de como me imagine las interfaces:
<img width="1920" height="1080" alt="BocetoSistemas" src="https://github.com/user-attachments/assets/a41d626e-7986-4fe7-a9f3-69f8ab5a2648" />


#### ✍️ Diagrama
<img width="5647" height="1594" alt="Diagramas Sistemas Fisicos" src="https://github.com/user-attachments/assets/d054bed8-aace-4df5-9015-044ba5054fbb" />


## 🛠 Fase: Apply

### 📚Actividad 02  
#### ✍️ Proceso de Construcción
Este proyecto lo inicie usando el codigo de la actividad anterior, un visualizador de audio con tres circulos concentricos que reaccionaban al ritmo de una cancion (Black Swan de BTS). Esta versión inicial me servio como punto de partida para incorporar el microbit

En la primera clase de esta unidad:

1. Revise el codigo, que estuviera funcionando correctamente, lo clone y subi a un nuevo repo de github
2. Antes de la nueva interaccion me quise tomar el tiempo de poner mas bonita la interfaz del celular, ya que, solo era el fondo negro con un texto en el centro que decia deslizaste a tal lado o capas fusionadas o no…
- Primero se logro tener el triangulo del slider, pero era meramente visual no funcional, y la punta quedo hacia arriba (en el boceto la imagine hacia abajo). Ademas sentia q el canva era muy pequeño entonces lo cambie para que se adaptara al tamaño de la pantalla dependiendo del celular usando:  `createCanvas(windowWidth, windowHeight);`
- Chat me comento que P5.js tiene un elemento deslizante: `createSlider()`  pero al usar lo se me generaba de forma horizontal por lo que se formaba un conflicto con el cambio de color que se controlaba tmb de forma horizontal
- Entonces dividi el canva en 3 zonas, una para el titulo, otra para el slider y abajo una zona para el cambio de color. Tmb opte por no usar el elemento antes mencionado, entonces se creo una linea y una perilla. Aqui se me presento otra situacion. Hasta el momento solo estaba modificando el codigo del sketch del mobile pero entonces para que el slider funcionara tmb modifique unas vrbles en el sketch del desktop, para que la fusion ya no dependiera de recibir que se movio de arriba a abajo si no de una vrblae entre 0 y 1. En este momento ya funcionaba todo bien. Pero no tenia el triangulo entonces simplemente lo añadi detras del slider como algo meramente estetico
- Tmb use emojis para que no se sintiera una interfaz tan plana, y asi quedo:
<img src="https://github.com/user-attachments/assets/82106d9b-4f2b-4537-b446-e8be518a7b69" width="300">

#### Codigos 💻
Sketch.js/mobile:
```javascript
let socket;
let lastTouchX = null;
let lastTouchY = null;
let lastSendTime = 0;
const threshold = 30; // movimiento mínimo para detectar un gesto
const cooldown = 300; // milisegundos entre gestos

let fusionValue = 0; // nivel de fusion(0–1)
let sliderDragging = false;

function setup() {
    createCanvas(windowWidth, windowHeight);
    socket = io();

    textAlign(CENTER, CENTER);
    noStroke();

    socket.on('connect', () => console.log('Conectado al servidor'));
    socket.on('disconnect', () => console.log('Desconectado'));
}

function draw() {
    background(20, 10, 30);

    //Titulos
    fill(255);
    textSize(22);
    text('💜Pulse of BTS💜', width / 2, height * 0.12);
    textSize(15);
    text('↑↓ Controla la fusión | ←→ Cambia el color', width / 2, height * 0.18);
    
    // Triángulo decorativo
    noStroke();
    fill(160, 100, 255, 80); // RGBA
    const triHeight = 420;
    const triWidth = 350;
    const cx = width / 2;
    const cy = height / 2;
    triangle(cx - triWidth / 2, cy - triHeight / 2, cx + triWidth / 2, cy - triHeight / 2, cx, cy + triHeight / 2); // Triángulo apuntando hacia abajo

    //Zona y linea del slider
    let sliderX = width / 2;
    let sliderTop = height * 0.25;
    let sliderBottom = height * 0.75;
    stroke(80);
    strokeWeight(3);
    line(sliderX, sliderTop, sliderX, sliderBottom);
    // Perilla
    noStroke();
    let handleY = map(fusionValue, 0, 1, sliderBottom, sliderTop);
    fill(255);
    circle(sliderX, handleY, 28);
    // Etiqueta dinamica
    noStroke();
    fill(200);
    textSize(14);
    text(`Fusión: ${Math.round(fusionValue * 100)}%`, sliderX, sliderBottom + 35);

    // Espacio inferior para gestos del cambio de color
    fill(255, 40);
    rect(0, height - 150, width, 150);
    noStroke();
    fill(255, 100);
    textSize(18);
    text('Zona Cambio de Color 🎨', width / 2, height - 80);
}

function touchStarted() {
    lastTouchX = mouseX;
    lastTouchY = mouseY;

    // Slider:
    let handleY = map(fusionValue, 0, 1, height * 0.75, height * 0.25);
    if (dist(mouseX, mouseY, width / 2, handleY) < 30) {
        sliderDragging = true;
    }
}

function touchMoved() {
    if (!socket || !socket.connected) return false;

    if (sliderDragging) { // Si se arrastra el slider
        let sliderTop = height * 0.25;
        let sliderBottom = height * 0.75;

        let newFusion = map(mouseY, sliderBottom, sliderTop, 0, 1);
        newFusion = constrain(newFusion, 0, 1);

        if (abs(newFusion - fusionValue) > 0.01) { // Solo enviar datos si hay cambio significativo
            fusionValue = newFusion;
            socket.emit('message', { type: 'fusion', value: fusionValue });
        }
        return false;
    }

    if (mouseY > height - 150) { // Si desliza en la zona de color
        const now = millis();
        if (now - lastSendTime < cooldown) return false;

        let dx = mouseX - lastTouchX;
        if (abs(dx) > threshold) {
            let direction = dx > 0 ? "right" : "left";
            socket.emit('message', { type: 'touch', direction });
            lastSendTime = now;
            lastTouchX = mouseX;
        }
    }

    return false;
}

function touchEnded() {
    sliderDragging = false;
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}

```

Codigo microbit:
```python
# Imports go at the top
from microbit import *

uart.init(115200)
display.show(Image.HEART)

while True:
    xValue = accelerometer.get_x()
    yValue = accelerometer.get_y()
    aState = button_a.is_pressed()
    bState = button_b.is_pressed()
    data = "{},{},{},{}\n".format(xValue, yValue, aState,bState)
    uart.write(data)
    sleep(100) # Envia datos a 10 Hz
```

#### Enlace al repositorio 🔗
https://github.com/VanDiosa/Pulse-of


## ⭐ Autoevaluación








