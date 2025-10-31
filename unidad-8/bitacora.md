
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
Este proyecto lo inicie usando el [codigo de la actividad anterior](https://github.com/VanDiosa/Pulse-of-Swan), un visualizador de audio con tres circulos concentricos que reaccionaban al ritmo de una cancion (Black Swan de BTS). Esta versión inicial me servio como punto de partida para incorporar el microbit

En la primera clase de esta unidad:

1. Revise el codigo, que estuviera funcionando correctamente, lo clone y subi a un nuevo repo de github
2. Los primeros prompts q le mande a chat fueron los siguientes, copiare lo mas relevante para no saturar la bitacora:    
”Hola chat, necesito ayuda para modificar el codigo de la unidad 7 de sistemas fisicos, para generar una nueva version del proyecto para mi unidad 8 ESTE ES EL PROYECTO DEL CUAL PARTIREMOS:       
    Boceto e idea 🌟       
    El visualizador esta inspirado en Black Swan de BTS. En el desktop, se encuentran tres circulos concentricos q representan las capas del sonido (voz, altos y bajos) que reaccionan visualmente al ritmo de la cancion. Desde el celular, el usuario puede interactuar en tiempo real: deslizar horizontalmente cambia la paleta de colores, y deslizar verticalmente acerca o separa los circulos, fusionándolos de 3 espectros a 1 solo       
    Codigos 💻       
    *(Le mande los codigos del apply de la unidad 7)*    
    Porfa confirmame que entendiste“
   
    “Sí, Vanesa, entendí perfectamente 💡    
    Este es tu proyecto **“Pulse of Swan 🦢”** de la **unidad 7**, que consiste en:     
    *(resumen hecho por chat)*    
    Así que trabajaremos sobre esa base para generar una **nueva versión del proyecto** para tu **unidad 8** ✅”    

    “La nueva version sera la siguiente:      
    *(Le copie todo lo que habia escrito en la actividad 1 de esta unidad 8)*    
    Confirmame si lo entendiste, si guardaste los codigos base y si guardaste la informacion de la nueva version”     
    
    “Perfectamente entendido, Vanesa 💡
    (…)
    ✨ En resumen: ya tengo **guardados el código base** y toda la **información conceptual y funcional** de la nueva versión (unidad 8).
    ¿Quieres que el siguiente paso sea que empecemos a **modificar el código del servidor, desktop y móvil** para implementar esta nueva versión paso a paso?”

    Ya con chat contextualizado clone el proyecto y cree un nuevo repositorio

3. Antes de la nueva interaccion me quise tomar el tiempo de poner mas bonita la interfaz del celular, ya que, solo era el fondo negro con un texto en el centro que decia deslizaste a tal lado o capas fusionadas o no…    
    
    Entonces le coloque a chat:    
    “Lo primero que quiero hacer es modificar la interfaz del mobile, teniendo en cuenta mi boceto y descripcion    
    *(le reenvie el codigo del sketch del mobile)*“    
    
    Estos fue lo que le agrego al codigo base:   
    ```jsx
    let triTop, triLeft, triRight;
    let circlePos; 
    let dragging = false;
    ```
    
    ```jsx
    // En la funcion draw()
    triangle(triTop.x, triTop.y, triLeft.x, triLeft.y, triRight.x, triRight.y);
    ```
    
    ```jsx
    // En la funcion touchMoved()
    if (dragging) {
      circlePos.y = constrain(mouseY, minY, maxY);
      let fusionLevel = map(circlePos.y, minY, maxY, 0, 1);
      socket.emit('fusionControl', { value: fusionLevel });
    }
    ```
    
    ```jsx
    // --- Detección punto dentro de triángulo ---
    function pointInTriangle(px, py, v1, v2, v3) {
      const areaOrig = abs((v2.x - v1.x) * (v3.y - v1.y) - (v3.x - v1.x) * (v2.y - v1.y));
      const area1 = abs((v1.x - px) * (v2.y - py) - (v2.x - px) * (v1.y - py));
      const area2 = abs((v2.x - px) * (v3.y - py) - (v3.x - px) * (v2.y - py));
      const area3 = abs((v3.x - px) * (v1.y - py) - (v1.x - px) * (v3.y - py));
      return abs(area1 + area2 + area3 - areaOrig) < 0.5;
    }
    ```
    
    ```jsx
    function touchEnded() {
      dragging = false;
    }
    ```

Se logro tener el triangulo del slider, pero era meramente visual no funcional, y la punta quedo hacia arriba (en el boceto la imagine hacia abajo). Ademas sentia q el canva era muy pequeño entonces lo cambie para que se adaptara al tamaño de la pantalla dependiendo del celular usando:  `createCanvas(windowWidth, windowHeight);`. Entonces le coloque esto a chat:    
“me gusta como se ve, pero el slider del triangulo es meramente visual, o sea lo que yo queria es que al arrastrar el circulo ps se fusionaran o no los espectros. Ademas, quiero que la punta este hacia abajo pq hacia abajo es fusionado, y que la base este hacia arriba pq hacia arriba es que sean 3 espectros     
te mando nuevamente todos los codigos, para que me pases una nueva version del codigo:     
*(le pase nuevamente los codigos)*”     

“La idea es que, además de los gestos, puedas **controlar el nivel de fusión (0–1)** con un slider, y que este valor se envíe al escritorio en tiempo real.     
P5.js tiene `createSlider()`, que podemos usar fácilmente.”     

Estos fue lo que le agrego al codigo:

```jsx
// en la funcion setup:

// Crear el slider para fusión
    fusionSlider = createSlider(0, 100, 0);
    fusionSlider.position(width / 2 - 100, height / 2);
    fusionSlider.size(200);
    fusionSlider.style('accent-color', '#ffffff');

    fusionLabel = createP('Nivel de fusión: 0%');
    fusionLabel.style('color', 'white');
    fusionLabel.position(width / 2 - 80, height / 2 + 30);
```

```jsx
//funcion draw:

		// Leer valor del slider
    let fusionValue = fusionSlider.value();

    // Solo enviar si cambia el valor
    if (fusionValue !== lastFusionValue) {
        socket.emit('message', { type: 'fusion', value: fusionValue / 100 });
        fusionLabel.html(`Nivel de fusión: ${fusionValue}%`);
        lastFusionValue = fusionValue;
    }
```

Y me sugirio eliminar lo siguiente: `triTop`, `triLeft`, `triRight`, `circlePos` . Función `pointInTriangle()`. Variable `dragging` y lógica de arrastre. Etiquetas visuales dentro del canvas. Evento `fusionControl` (reemplazado por `message` tipo `"fusion"`)      

Como pudo ver chat me comento que P5.js tiene un elemento deslizante: `createSlider()`  pero al usar lo se me generaba de forma horizontal por lo que se formaba un conflicto con el cambio de color que se controlaba tmb de forma horizontal. Entonces chat realizo las siguientes modificaciones:    

```jsx
let fusionValue = 0; // Nivel de fusión (0–1)
let sliderY; // Posición vertical del control
let sliderDragging = false;
```

```jsx
//En la funcion draw ():

// --- Control de fusión (slider vertical) ---
    let sliderX = width * 0.85;
    let sliderTop = height * 0.3;
    let sliderBottom = height * 0.8; 

// Línea del slider
    stroke(100);
    strokeWeight(4);
    line(sliderX, sliderTop, sliderX, sliderBottom);

    // Perilla del slider
    let handleY = map(fusionValue, 0, 1, sliderBottom, sliderTop);
    noStroke();
    fill(255);
    circle(sliderX, handleY, 20);

    // Etiqueta del valor
    noStroke();
    textSize(14);
    text(`${Math.round(fusionValue * 100)}%`, sliderX, sliderBottom + 25);

    // Enviar valor si cambia
    if (frameCount % 5 === 0 && socket && socket.connected) {
        socket.emit('message', { type: 'fusion', value: fusionValue });
    }
```

```jsx
// En la funcion touchStarted()
if (dist(mouseX, mouseY, sliderX, map(fusionValue, 0, 1, height * 0.8, height * 0.3)) < 30) {
    sliderDragging = true;
}
```

```jsx
//En la funcion touchMoved():
if (sliderDragging) {
    fusionValue = map(mouseY, sliderBottom, sliderTop, 0, 1);
    fusionValue = constrain(fusionValue, 0, 1);
    return false;
}
```

Y en esta version se eliminaron todos los elementos HTML (`createSlider`, `createP`). Los `fusionSlider`, `fusionLabel`, `lastFusionValue`. El condicional `if (fusionValue !== lastFusionValue)`      

Pero como le dije a chat “ese slider esta muy estorboso, deberia de estar centrado y dejar un espacio abajo para poder uno hacer el movimiento horizontal para cambiar el color. ademas al deslizar el circulo todo hacia arriba no se fusiona, es como q hace el intento pero se enloquece”.      

El me respondio:

“Perfecto Vanesa 💡 —ya entiendo exactamente lo que quieres:      
el slider debe sentirse **integrado al centro visual del móvil**, no como un control aparte.     
Además, el **movimiento horizontal (color)** debe tener espacio libre **en la parte inferior**.     
Y por supuesto, el **slider debe moverse suave** y **controlar bien la fusión**, sin “enloquecerse”.      
Vamos a corregir todo eso 👇     
🎯 Cambios que se harán        
✅ Centrar el slider verticalmente (en el medio de la pantalla).     
✅ Dejar una **zona inferior libre (~150 px)** para los gestos horizontales.    
✅ Corregir el movimiento del círculo para que no rebote ni se trabe.    
✅ Hacer que el slider emita el valor de fusión **solo cuando cambia realmente** (suave).    
✅ Darle un look más minimalista, acorde al estilo *Pulse of Swan*.”      

Entonces chat realizo las siguientes modificaciones:

```jsx
// En la función draw():

// --- Títulos actualizados y reposicionados ---
fill(255);
textSize(22);
text('Pulse of Swan 🦢', width / 2, height * 0.12);
textSize(15);
text('↑↓ Controla la fusión | ←→ Cambia el color', width / 2, height * 0.18);

// --- Zona del slider (ahora centrada en pantalla) ---
let sliderX = width / 2;
let sliderTop = height * 0.25;
let sliderBottom = height * 0.75;

// Línea del slider (más delgada)
stroke(80);
strokeWeight(3);
line(sliderX, sliderTop, sliderX, sliderBottom);

// Perilla del slider (más grande)
noStroke();
let handleY = map(fusionValue, 0, 1, sliderBottom, sliderTop);
fill(255);
circle(sliderX, handleY, 28);

// Etiqueta del valor más descriptiva
noStroke();
fill(200);
textSize(14);
text(`Fusión: ${Math.round(fusionValue * 100)}%`, sliderX, sliderBottom + 35);

// --- Nueva zona inferior para gestos horizontales ---
fill(255, 40);
rect(0, height - 150, width, 150);
noStroke();
fill(255, 100);
textSize(12);
text('Zona de gestos horizontales (color)', width / 2, height - 80);

```

```jsx
// En la función touchStarted():

// Ahora el slider se detecta en el centro de la pantalla
let handleY = map(fusionValue, 0, 1, height * 0.75, height * 0.25);
if (dist(mouseX, mouseY, width / 2, handleY) < 30) {
    sliderDragging = true;
}
```

```jsx
// En la función touchMoved():

// Si se arrastra el slider vertical, se actualiza y envía solo si hay cambio significativo
if (sliderDragging) {
    let sliderTop = height * 0.25;
    let sliderBottom = height * 0.75;
    let newFusion = map(mouseY, sliderBottom, sliderTop, 0, 1);
    newFusion = constrain(newFusion, 0, 1);

    if (abs(newFusion - fusionValue) > 0.01) {
        fusionValue = newFusion;
        socket.emit('message', { type: 'fusion', value: fusionValue });
    }
    return false;
}

// Nuevo bloque: gestos horizontales en la zona inferior (cambio de color)
if (mouseY > height - 150) {
    const now = millis();
    if (now - lastSendTime < cooldown) return false;

    let dx = mouseX - lastTouchX;
    if (abs(dx) > threshold) {
        let direction = dx > 0 ? "right" : "left";
        socket.emit('message', { type: 'touch', direction });

        fill(255);
        textSize(16);
        text(direction === "right" ? "→ Color cálido" : "← Color frío", width / 2, height - 40);

        lastSendTime = now;
        lastTouchX = mouseX;
    }
}
```

En esta version se elimino:  El uso de `sliderY` (ya no era necesario). El bloque que enviaba el valor de fusión cada 5 frames: `if (frameCount % 5 === 0 && socket && socket.connected) {socket.emit('message', { type: 'fusion', value: fusionValue });}`. Todo el manejo de gestos en 4 direcciones (`up`, `down`, `left`, `right`) dentro de `touchMoved()`. Los mensajes de texto dinámicos (→ “Cambio de color”, ⬆ “Separando capas”, etc.). Y las referencias al `sliderX` lateral (`width * 0.85`) y sus etiquetas asociadas   

En este punto visualmente ya me estaba agrandando mucho ya que se veia asi:     
<img src="https://github.com/user-attachments/assets/a4794b1c-39c3-4c2f-9830-37ce19abfc0c" width="250">

Pero se presentaba lo siguiente:

“bien, en cuanto a distribucion vamos mejorando. pero al estar en 100% la fusion no se fusionan es como que al mover el slide se hace la transicion pero en lugar de pasar de 3 a 1 pasa de 3 a 3”

“Perfecto 🫶 Vanesa, ya entendí clarito lo que pasa:
el *slider visual* sí está mandando valores de fusión al servidor, pero el **código del escritorio (`desktop/sketch.js`) todavía no interpreta esos valores** —solo reacciona a “up” o “down”.     
Por eso, aunque el slider cambie `fusionValue` (de 0 a 1), el desktop sigue leyendo solo `true` o `false` en `fusion`, lo que hace que la animación se quede “congelada” entre tres espectros.      
Vamos a solucionarlo totalmente:     
✅ el *mobile* enviará un valor de fusión continuo (`0–1`),    
✅ el *desktop* lo recibirá como `fusionValue` y     
✅ se usará directamente para interpolar el estado visual.”     

Ahora pasamos a modificar el sketch del desktop, todo lo anterior fue solo en el mobile:

```jsx
// Se reemplazo el control booleano de fusion por un valor numerico continuo (de 0 a 1) para permitir control mediante slider desde el movil
let fusionValue = 0;

```

```jsx
// En la funcion setup() se cambio el listener del socket 
socket.on('message', handleControl);
```

```jsx
function handleControl(data) {
    if (data.type === 'touch') {
        if (data.direction === "left") hueShift -= 10;
        else if (data.direction === "right") hueShift += 10;
    }
    
    if (data.type === 'fusion') {
        fusionValue = constrain(data.value, 0, 1);
    }
}

// En la version anterior solo respondia a direcciones (up/down/left/right) sin valores numericos

```

```jsx
// En la funcion draw():

let transition = lerp(0, 1, fusionValue);

// Ahora, el estado de transicion se calcula de forma continua, y se dibujan ambos de acuerdo al valor numerico recibido

if (transition < 0.98) { /* tres espectros */ }
if (transition > 0.02) { /* uno fusionado */ }

```

En general se elimino: La vrble'fusion' (booleana), la vrble 'transition' como estado local (ahora es derivada). El bloque de 'handleTouch' y sus condicionales de dirección 'up'/'down'. La dependencia de gestos táctiles para activar/desactivar la fusión     

Y ps en este punto lo ultimo que hice fue agregar el triangulo detras del slider, solo como una decoracion que tenia pensada desde el boceto de la siguiente forma:

```jsx
// En la funcion draw():
 // Triángulo decorativo
    noStroke();
    fill(160, 100, 255, 80); // RGBA
    const triHeight = 420;
    const triWidth = 350;
    const cx = width / 2;
    const cy = height / 2;
    triangle(cx - triWidth / 2, cy - triHeight / 2, cx + triWidth / 2, cy - triHeight / 2, cx, cy + triHeight / 2); // Triángulo apuntando hacia abajo

```

Asi quedo la interfaz del mobile:     
<img src="https://github.com/user-attachments/assets/967be90d-86d7-4cbf-8a98-cef15cca107f" width="250">

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











