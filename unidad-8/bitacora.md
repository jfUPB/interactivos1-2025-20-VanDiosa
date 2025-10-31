
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

##### Primera clase de la unidad:        

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

4.  Con la interfaz del mobile terminada pase a editar la del desktop:
	”Listo los codigos estan asi:
	*(codigos actualizados)*
	Ahora lo que quiero es organizar la interfaz del desktop.
	Poner el titulo a la derecha. y a la izquierda tres botones. para iniciar, pausar y parar, te mando el boceto
	(le anexe el boceto del desktop)
	cuando tengamos eso listo, podremos empezar a integrar el microbit”
	
	Esto fue lo que se le agrego al codigo del sketch del desktop:
	
	```jsx
	let playButton, pauseButton, stopButton;
	```
	
	```jsx
	// En la funcion setup():
	createCanvas(1900, 800);
	(...)
	socket.on('message', handleTouch);
	
	 // --- Controles de música ---
	playButton = createButton('▶');
	pauseButton = createButton('⏸');
	stopButton = createButton('⏹');
	
	 // Posiciones
	styleButton(playButton, width - 120, height / 2 - 100);
	styleButton(pauseButton, width - 120, height / 2);
	styleButton(stopButton, width - 120, height / 2 + 100);
	
	playButton.mousePressed(() => {
	    if (!song.isPlaying()) song.loop();
	  });
	
	  pauseButton.mousePressed(() => {
	    if (song.isPlaying()) song.pause();
	  });
	
	  stopButton.mousePressed(() => {
	    song.stop();
	  });
	```
	
	```jsx
	function styleButton(btn, x, y) {
	    btn.position(x, y);
	    btn.size(60, 60);
	    btn.style('font-size', '28px');
	    btn.style('border', 'none');
	    btn.style('border-radius', '50%');
	    btn.style('background', 'rgba(100, 0, 200, 0.4)');
	    btn.style('color', 'white');
	    btn.style('cursor', 'pointer');
	    btn.style('backdrop-filter', 'blur(4px)');
	    btn.mouseOver(() => btn.style('background', 'rgba(150, 0, 255, 0.6)'));
	    btn.mouseOut(() => btn.style('background', 'rgba(100, 0, 200, 0.4)'));
	}
	```
	
	```jsx
	//En la funcion draw():
	// --- Título ---
	push();
	resetMatrix(); // Restablece el sistema de coordenadas
	textAlign(LEFT, CENTER);
	textSize(64);
	fill(255);
	text("Pulse of BTS", 100, height / 2 - 25);
	pop();
	```

 ##### Segunda clase de la unidad:       

5. Y ahora con las dos interfaces mas bonitas, le reenvie los codigos actualizados a chat y tmb le puse lo siguiente:
    
    “ AHORA TOCA INTEGRAL EL MICROBIT, ASI QUE TE RECUERDO LA IDEA:     
    Explicación control movil y microbit      
    Movil-Touch:     
    Deslizamiento horizontal: cambia la gama de colores de los espectros      
    Deslizamiento vertical: fusiona o separa las capas (de tres espectros a uno)     
    Microbit:       
    Boton A: cambia la musica de Black Swan a Fake Love, variando de un fondo negro a uno claro, y cambiando los espectos de circulos a triangulos      
    Boton B: regresa al modo Black Swan      
    Acelerometro: al detectar movimiento, emite unos aros de luz que parten desde el centro de los espectros y se expande en el lienzo      

   SI QUIERES PRIMERO HAGAMOS LO DE LOS BOTONES QUE ES MAS FACIL CREO YO       
    EN ACTIVIDADES ANTERIORES HEMOS PROGRAMADO EL MICROBIT ASI:      
    #Imports go at the top    
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
    sleep(100) # Envia datos a 10 Hz”        
    
    “Perfecto Vanesa 💜 excelente organización — el sistema ya está muy limpio y modular, así que integrar el **micro:bit** te va a salir súper fluido.    
    Y sí, empezamos por lo **más fácil: los botones A y B**, antes de pasar al acelerómetro.      
    Primero necesitas instalar `serialport`: `npm install serialport` “       
    
    Despues de como 5 versiones q no encuentro ya que lo tuve que hacer en otro chat pq en el que estaba trabajando se me acabo la version gratuita, esto fue lo que se habia agregado al server:
    
    ```jsx
    // --- NUEVA LÓGICA DE DIFUSIÓN ---
    parser.on('data', line => {
        const [x, y, a, b] = line.trim().split(',');
        const data = { x, y, a, b };
        io.emit('microbit', data); // 🔁 Enviar a TODOS los clientes
    });
    ```
    
    ```jsx
    // --- NUEVA ESCUCHA DE MENSAJES ENTRE CLIENTES ---
    socket.on('message', (message) => {
        console.log('Mensaje recibido =>', message);
        socket.broadcast.emit('message', message);
    });
    ```
    
    ```jsx
    // --- NUEVOS LOGS INFORMATIVOS ---
    console.log('📡 Servidor iniciado en http://localhost:3000');
    console.log('🔌 Esperando datos del micro:bit en COM8...');
    ```
    
    Se elimino el envio individual con `socket.emit`, para manejar todo con `io.emit`, permitiendo difusion global. Se reorganizo la seccion del parser para que la lectura del microbit no dependa de una conexion específica. Ahora siempre escucha y transmite datos

   Pero al tratar de ejecutar el programa me salio el siguiente error:

	```jsx
	Vanesa@IdeaPad-Van MINGW64 ~/Desktop/UNIVERSIDAD/SEMESTRE 8/SISTEMA FISICOS INTERACTIVOS/Unidad8/PulseOf (main) 
	$ npm start 
	> sfinteractivesocketiodesktopmobile@1.0.0 start 
	> node server.js 
	C:\Users\Vanesa\Desktop\UNIVERSIDAD\SEMESTRE 8\SISTEMA FISICOS INTERACTIVOS\Unidad8\PulseOf\server.js:17 
	const microbitPort = new SerialPort('COM8', { baudRate: 115200 }); 
	^ 
	TypeError: SerialPort is not a constructor 
		at Object.<anonymous> 
	(C:\Users\Vanesa\Desktop\UNIVERSIDAD\SEMESTRE 8\SISTEMA FISICOS INTERACTIVOS\Unidad8\PulseOf\server.js:17:22) 
		at Module._compile (node:internal/modules/cjs/loader:1706:14) 
		at Object..js (node:internal/modules/cjs/loader:1839:10) 
		at Module.load (node:internal/modules/cjs/loader:1441:32) 
		at Function._load (node:internal/modules/cjs/loader:1263:12) 
		at TracingChannel.traceSync (node:diagnostics_channel:322:14) 
		at wrapModuleLoad (node:internal/modules/cjs/loader:237:24) 
		at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:171:5) 
		at node:internal/main/run_main_module:36:49
	```
	
	Se soluciono el error pero, despues si usaba el microbit el mobile no funcionaba y viceversa, pero entonces llegamos al siguiente codigo para el server:
	
	```jsx
	const express = require('express');
	const http = require('http');
	const { Server } = require("socket.io");
	const { SerialPort } = require('serialport');
	const { ReadlineParser } = require('@serialport/parser-readline');
	
	const app = express();
	const server = http.createServer(app);
	const io = new Server(server);
	const port = 3000;
	
	app.use(express.static('public'));
	
	// ===== Microbit =====
	const microbitPort = new SerialPort({ path: 'COM8', baudRate: 115200 });
	const parser = microbitPort.pipe(new ReadlineParser({ delimiter: '\n' }));
	
	parser.on('data', (line) => {
	    const [x, y, a, b] = line.trim().split(',');
	    const data = {
	        x: Number(x),
	        y: Number(y),
	        buttonA: a === 'True' || a === '1',
	        buttonB: b === 'True' || b === '1'
	    };
	
	    if (data.buttonA) io.emit('microbit', { button: 'A' });
	    if (data.buttonB) io.emit('microbit', { button: 'B' });
	});
	
	// ===== Socket.io =====
	io.on('connection', (socket) => {
	    console.log('Nuevo cliente conectado');
	
	    // Mobile → desktop
	    socket.on('message', (data) => {
	        io.emit('message', data); // <- IMPORTANTE: emit a TODOS, no broadcast
	    });
	
	    socket.on('disconnect', () => {
	        console.log('Cliente desconectado');
	    });
	});
	
	server.listen(port, () => {
	    console.log(`Server listening on http://localhost:${port}`);
	});
	
	```
	
	En esta version se unifico completamente la comunicacion entre el microbit y todos los clientes conectados. Asi los datos seriales del microbit se procesan globalmente y se emiten mediante `io.emit`, permitiendo que cualquier navegador reciba los eventos de los botones A y B en tiempo real. Ademas, se simplifico la logica del servidor para que los mensajes enviados desde cualquier cliente se reenvien a todos (no solo a otros), asegurando sincronizacion total entre dispositivos. Tambien se optimizo el parser para interpretar valores tanto en formato `'True'/'False'` como `'1'/'0'`, mejorando la compatibilidad de lectura del microbit

	De igual forma se hicieron las respectivas modificaciones al sketch del desktop:

	```jsx
	let songBlackSwan, songFakeLove, song;
	let fft;
	let socket;
	
	let hueShift = 0;
	let rotationAngles = [0, 0, 0];
	let baseRadius = 140;
	let spacing = 90;
	let fusionValue = 0; // 0 = tres anillos, 1 = uno solo
	
	let currentMode = 'BlackSwan'; // Cancion inicial
	
	let playButton, pauseButton, stopButton; // Botones de reproduccion musica
	
	function preload() {
	    soundFormats('mp3');
	    songBlackSwan = loadSound('blackswan.mp3');
	    songFakeLove = loadSound('fakelove.mp3');
	    song = songBlackSwan;
	}
	
	function setup() {
	    createCanvas(1900, 800);
	    colorMode(HSB);
	    fft = new p5.FFT();
	    socket = io();
	
	    // Botones de control
	    playButton = createButton('▶');
	    pauseButton = createButton('⏸');
	    stopButton = createButton('⏹');
	
	    styleButton(playButton, width - 120, height / 2 - 100);
	    styleButton(pauseButton, width - 120, height / 2);
	    styleButton(stopButton, width - 120, height / 2 + 100);
	
	    playButton.mousePressed(() => { if (!song.isPlaying()) song.loop(); });
	    pauseButton.mousePressed(() => { if (song.isPlaying()) song.pause(); });
	    stopButton.mousePressed(() => { song.stop(); });
	
	    userStartAudio();
	
	    // Microbit datos
	    socket.on('microbit', (data) => {
	        if (data.button === 'A') switchToFakeLove();
	        if (data.button === 'B') switchToBlackSwan();
	    });
	
	    // Mobile datos
	    socket.on('message', handleTouch);
	}
	
	function styleButton(btn, x, y) {
	    btn.position(x, y);
	    btn.size(60, 60);
	    btn.style('font-size', '28px');
	    btn.style('border', 'none');
	    btn.style('border-radius', '50%');
	    btn.style('background', 'rgba(100,0,200,0.4)');
	    btn.style('color', 'white');
	    btn.style('cursor', 'pointer');
	    btn.style('backdrop-filter', 'blur(4px)');
	    btn.mouseOver(() => btn.style('background', 'rgba(150,0,255,0.6)'));
	    btn.mouseOut(() => btn.style('background', 'rgba(100,0,200,0.4)'));
	}
	
	function switchToFakeLove() {
	    if (currentMode === 'FakeLove') return;
	    let currentTime = song.currentTime();
	    currentMode = 'FakeLove';
	    song.stop();
	    song = songFakeLove;
	    song.jump(currentTime);
	    song.loop();
	    hueShift = 0;
	}
	
	function switchToBlackSwan() {
	    if (currentMode === 'BlackSwan') return;
	    let currentTime = song.currentTime();
	    currentMode = 'BlackSwan';
	    song.stop();
	    song = songBlackSwan;
	    song.jump(currentTime);
	    song.loop();
	    hueShift = 0;
	}
	
	function handleTouch(data) {
	    if (data.type === 'touch') {
	        hueShift += data.direction === 'right' ? 10 : -10; // Antes decia: if (data.type === 'touch') { if (data.direction === "left") hueShift -= 10; else if (data.direction === "right") hueShift += 10;}
	    }
	    if (data.type === 'fusion') {
	        fusionValue = constrain(data.value, 0, 1);
	    }
	}
	
	function draw() {
	    background(currentMode === 'BlackSwan' ? 0 : color(280, 80, 30, 0.2));
	    translate(width / 2, height / 2); // Mover origen
	    noFill();
	
	    let spectrum = fft.analyze(); //Para dividir en frecuencias (graves, medios y agudos)
	
	    // Rotaciones independientes (el del medio gira al revés)
	    rotationAngles[0] += 0.005;
	    rotationAngles[1] -= 0.006;
	    rotationAngles[2] += 0.007;
	
	    // Valores de fusión
	    let transition = lerp(0, 1, fusionValue);
	    let mergeOffset = spacing * transition;
	    let alphaOuter = 255 * (1 - transition);
	    let scaleCentral = 1 + 0.4 * transition;
	
	    // Título
	    push();
	    resetMatrix();
	    textAlign(LEFT, CENTER);
	    textSize(64);
	    fill(255);
	    text("Pulse of BTS", 100, height / 2 - 25);
	    pop();
	
	    // Dibujo de los tres anillos (se acercan al centro)
	    if (transition < 0.98) {
	        push();
	        strokeWeight(2);
	        drawBars(spectrum, getRainbowColor(0), baseRadius - mergeOffset, baseRadius - mergeOffset + 40, rotationAngles[0], alphaOuter);
	        drawBars(spectrum, getRainbowColor(120), baseRadius + spacing * (1 - transition / 2), baseRadius + spacing * (1 - transition / 2) + 40, rotationAngles[1], 255);
	        drawBars(spectrum, getRainbowColor(240), baseRadius + spacing * 2 - mergeOffset, baseRadius + spacing * 2 - mergeOffset + 40, rotationAngles[2], alphaOuter);
	        pop();
	    }
	
	    // Dibujo del espectro fusionado (uno solo, más grande y brillante)
	    if (transition > 0.02) {
	        push();
	        let glow = map(transition, 0, 1, 0, 80);
	        strokeWeight(2.5 + glow * 0.02);
	        drawBars(spectrum, getRainbowColor(hueShift), (baseRadius + spacing) * scaleCentral, (baseRadius + spacing + 80) * scaleCentral, rotationAngles[1], map(transition,0,1,0,255));
	        pop();
	    }
	}
	
	// Dibujo de espectros: graves (interno), voces(medio), agudos(externo)
	function drawBars(spectrum, col, minR, maxR, rotationAngle, alphaVal=255, start=0, end=1) {
	    push();
	    rotate(rotationAngle);
	    col.setAlpha(alphaVal);
	    stroke(col);
	    let len = spectrum.length;
	    for (let i = 0; i < 360; i += 3) {
	        let index = floor(map(i,0,360,start*len,end*len));
	        let amp = spectrum[index];
	        let r = map(amp,0,255,minR,maxR); // radio segun la amplitud del sonido
	        let rad = radians(i);
	        line(minR*cos(rad), minR*sin(rad), r*cos(rad), r*sin(rad)); // (coordenadas x y y del radio interno, amplitud)
	    }
	    pop();
	}
	
	function getRainbowColor(offset) { // variacion de paleta de colores
	    let hue = (hueShift + offset) % 360;
	    return color(hue, 100, 100);
	}
	
	```
	
	En esta version se agrego la opcion de cambiar entre canciones. El microbit podia controlar eso con los botones A y B. Se añadieron las funciones `switchToFakeLove()` y `switchToBlackSwan()`. Ademas, en el `preload()` ahora se cargan las dos canciones, y en el `draw()` el fondo depende del tema que este sonando. Todo lo demas, como los anillos, la fusion y los botones de reproduccion, siguio igual


##### Tercera clase de la unidad:

6. Ya tenia las interfaces bonitas, y las canciones cambiando con los botones del microbit. Ahora queria que hubiera un cross fade, q al cambiar de cancion no empezaran desde cero si no que, como q al darle play las dos estuvieran reproduciendose y fuera como si se le bajara volumen a una y la otra sonara en el mismo min de reproduccion. Este fue el codigo que chat me dio para modificar el desktop:

	```jsx
	let songBlackSwan, songFakeLove;
	let fft;
	let socket;
	
	let hueShift = 0;
	let rotationAngles = [0, 0, 0];
	let baseRadius = 140;
	let spacing = 90;
	let fusionValue = 0; // 0 = tres anillos, 1 = uno solo
	
	let currentMode = 'BlackSwan'; // Cancion inicial
	
	let playButton, pauseButton, stopButton; // Botones de reproduccion musica
	
	function preload() {
	    soundFormats('mp3');
	    songBlackSwan = loadSound('blackswan.mp3');
	    songFakeLove = loadSound('fakelove.mp3');
	    song = songBlackSwan;
	}
	
	function setup() {
	    createCanvas(1900, 800);
	    colorMode(HSB);
	    fft = new p5.FFT();
	    socket = io();
	
	    // Preparacion volumen inicial canciones
	    songBlackSwan.setVolume(1);
	    songFakeLove.setVolume(0);
	
	    // Botones de control
	    playButton = createButton('▶');
	    pauseButton = createButton('⏸');
	    stopButton = createButton('⏹');
	
	    styleButton(playButton, width - 120, height / 2 - 100);
	    styleButton(pauseButton, width - 120, height / 2);
	    styleButton(stopButton, width - 120, height / 2 + 100);
	
	     playButton.mousePressed(() => {
	    if (!songBlackSwan.isPlaying() && !songFakeLove.isPlaying()) {
	      songBlackSwan.loop();
	      songFakeLove.loop();
	    }
	    });
	
	    pauseButton.mousePressed(() => {
	        songBlackSwan.pause();
	        songFakeLove.pause();
	    });
	
	    stopButton.mousePressed(() => {
	        songBlackSwan.stop();
	        songFakeLove.stop();
	    });
	
	    userStartAudio();
	
	    // Microbit datos
	    socket.on('microbit', (data) => {
	        if (data.button === 'A') switchToFakeLove();
	        if (data.button === 'B') switchToBlackSwan();
	    });
	
	    // Mobile datos
	    socket.on('message', handleTouch);
	}
	
	function styleButton(btn, x, y) {
	    btn.position(x, y);
	    btn.size(60, 60);
	    btn.style('font-size', '28px');
	    btn.style('border', 'none');
	    btn.style('border-radius', '50%');
	    btn.style('background', 'rgba(100,0,200,0.4)');
	    btn.style('color', 'white');
	    btn.style('cursor', 'pointer');
	    btn.style('backdrop-filter', 'blur(4px)');
	    btn.mouseOver(() => btn.style('background', 'rgba(150,0,255,0.6)'));
	    btn.mouseOut(() => btn.style('background', 'rgba(100,0,200,0.4)'));
	}
	
	function crossfade(toMode) {
	  const fadeTime = 5.0; // Tiempo de fundido en segundos
	  if (toMode === 'FakeLove') {
	    songBlackSwan.amp(0, fadeTime);
	    songFakeLove.amp(1, fadeTime);
	  } else {
	    songBlackSwan.amp(1, fadeTime);
	    songFakeLove.amp(0, fadeTime);
	  }
	}
	
	function switchToFakeLove() {
	    if (currentMode === 'FakeLove') return;
	    currentMode = 'FakeLove';
	    crossfade('FakeLove');
	    hueShift = 0;
	}
	
	function switchToBlackSwan() {
	    if (currentMode === 'BlackSwan') return;
	    currentMode = 'BlackSwan';
	    crossfade('BlackSwan');
	    hueShift = 0;
	}
	
	function handleTouch(data) {
	    if (data.type === 'touch') {
	        hueShift += data.direction === 'right' ? 10 : -10; // Antes decia: if (data.type === 'touch') { if (data.direction === "left") hueShift -= 10; else if (data.direction === "right") hueShift += 10;}
	    }
	    if (data.type === 'fusion') {
	        fusionValue = constrain(data.value, 0, 1);
	    }
	}
	
	function draw() {
	    background(currentMode === 'BlackSwan' ? 0 : color(280, 80, 30, 0.2));
	    translate(width / 2, height / 2); // Mover origen
	    noFill();
	
	    let spectrum = fft.analyze(); //Para dividir en frecuencias (graves, medios y agudos)
	
	    // Rotaciones independientes (el del medio gira al revés)
	    rotationAngles[0] += 0.005;
	    rotationAngles[1] -= 0.006;
	    rotationAngles[2] += 0.007;
	
	    // Valores de fusión
	    let transition = lerp(0, 1, fusionValue);
	    let mergeOffset = spacing * transition;
	    let alphaOuter = 255 * (1 - transition);
	    let scaleCentral = 1 + 0.4 * transition;
	
	    // Título
	    push();
	    resetMatrix();
	    textAlign(LEFT, CENTER);
	    textSize(64);
	    fill(255);
	    text("Pulse of BTS", 100, height / 2 - 25);
	    pop();
	
	    // Texto informativo funcionamieno microbit
	    push();
	    resetMatrix();
	    textSize(22);
	    fill(200);
	    text("Controles Micro:bit:", 100, height / 2 + 40);
	    text("Botón A → Fake Love", 100, height / 2 + 80);
	    text("Botón B → Black Swan", 100, height / 2 + 110);
	    pop();
	
	    // Dibujo de los tres anillos (se acercan al centro)
	    if (transition < 0.98) {
	        push();
	        strokeWeight(2);
	        drawBars(spectrum, getRainbowColor(0), baseRadius - mergeOffset, baseRadius - mergeOffset + 40, rotationAngles[0], alphaOuter);
	        drawBars(spectrum, getRainbowColor(120), baseRadius + spacing * (1 - transition / 2), baseRadius + spacing * (1 - transition / 2) + 40, rotationAngles[1], 255);
	        drawBars(spectrum, getRainbowColor(240), baseRadius + spacing * 2 - mergeOffset, baseRadius + spacing * 2 - mergeOffset + 40, rotationAngles[2], alphaOuter);
	        pop();
	    }
	
	    // Dibujo del espectro fusionado (uno solo, más grande y brillante)
	    if (transition > 0.02) {
	        push();
	        let glow = map(transition, 0, 1, 0, 80);
	        strokeWeight(2.5 + glow * 0.02);
	        drawBars(spectrum, getRainbowColor(hueShift), (baseRadius + spacing) * scaleCentral, (baseRadius + spacing + 80) * scaleCentral, rotationAngles[1], map(transition,0,1,0,255));
	        pop();
	    }
	}
	
	// Dibujo de espectros: graves (interno), voces(medio), agudos(externo)
	function drawBars(spectrum, col, minR, maxR, rotationAngle, alphaVal=255, start=0, end=1) {
	    push();
	    rotate(rotationAngle);
	    col.setAlpha(alphaVal);
	    stroke(col);
	    let len = spectrum.length;
	    for (let i = 0; i < 360; i += 3) {
	        let index = floor(map(i,0,360,start*len,end*len));
	        let amp = spectrum[index];
	        let r = map(amp,0,255,minR,maxR); // radio segun la amplitud del sonido
	        let rad = radians(i);
	        line(minR*cos(rad), minR*sin(rad), r*cos(rad), r*sin(rad)); // (coordenadas x y y del radio interno, amplitud)
	    }
	    pop();
	}
	
	function getRainbowColor(offset) { // variacion de paleta de colores
	    let hue = (hueShift + offset) % 360;
	    return color(hue, 100, 100);
	}
	```
	
	En esta version cambiamos la forma en que se manejaban las canciones, ahora ambas suenan al mismo tiempo, pero con volumenes distintos, y se usa un efecto de crossfade para pasar suavemente de una a la otra sin cortes. Tambien se agregaron textos informativos en pantalla que explican como usar los botones del microbit. Además, se ajusto el codigo de los botones de reproduccion para que controlen las dos canciones a la vez, haciendo que el sistema sea mas estable y continuo durante los cambios

7. En este punto le añadimos la interaccion con el acelerometro. Le recorde como la idea a chat y le reenvie los codigos actuales nuevamente. Tuvimos que modificar tanto el server como el sketch del desktop

	Server:
	
	```jsx
	const express = require('express');
	const http = require('http');
	
	const { Server } = require("socket.io"); // const socketIO = require('socket.io');
	const { SerialPort } = require('serialport'); // para conectar y leer los datos del microbit...
	const { ReadlineParser } = require('@serialport/parser-readline'); //...a traves del puerto USB
	
	const app = express();
	const server = http.createServer(app);
	const io = new Server(server); // const io = socketIO(server); sintaxis moderna de V4
	const port = 3000;
	
	app.use(express.static('public'));
	
	// Microbit
	const microbitPort = new SerialPort({ path: 'COM10', baudRate: 115200 }); //REVISAR SIEMPRE QUE SE CAMBIA DE MICROBIT Y MODIFICAR EL COM
	const parser = microbitPort.pipe(new ReadlineParser({ delimiter: '\n' }));
	
	// Vrbles acelerometro
	let lastX = 0, lastY = 0;
	let shakeThreshold = 500; // sensibilidad
	let lastShakeTime = 0;
	
	parser.on('data', (line) => { // separar los valores (botones y acelerometro)
	    const [x, y, a, b] = line.trim().split(',');
	    const data = {
	        x: Number(x),
	        y: Number(y),
	        buttonA: a === 'True' || a === '1',
	        buttonB: b === 'True' || b === '1'
	    };
	
	    if (data.buttonA) io.emit('microbit', { button: 'A' });
	    if (data.buttonB) io.emit('microbit', { button: 'B' });
	
	    // Detectar acelerometro
	    const deltaX = Math.abs(data.x - lastX);
	    const deltaY = Math.abs(data.y - lastY);
	    const now = Date.now();
	
	    if ((deltaX > shakeThreshold || deltaY > shakeThreshold) && (now - lastShakeTime > 1000)) {
	        io.emit('microbit', { shake: true });
	        lastShakeTime = now;
	    }
	
	    lastX = data.x;
	    lastY = data.y;
	});
	
	// Socket.io
	io.on('connection', (socket) => {
	    console.log('Nuevo cliente conectado');
	
	    socket.on('message', (data) => { // Comunicacion Mobile → Desktop
	        io.emit('message', data); // ahora io.emit en lugar de broadcast para asegurar que los 3 reciban todos los datos de sincronizacion
	    });
	
	    socket.on('disconnect', () => {
	        console.log('Cliente desconectado');
	    });
	});
	
	server.listen(port, () => {
	    console.log(`Server listening on http://localhost:${port}`);
	});
	```
	
	En esta version se agrego la deteccion de movimiento del microbit usando los valores del acelerometro. Ahora el servidor compara los cambios en X y Y, y si pasan un limite (shakeThreshold) manda un evento `shake` a todos los clientes con `io.emit`. Se puso un pequeño tiempo de espera para no detectar muchas sacudidas seguidas. La comunicacion entre mobile y desktop sigue igual, usando `io.emit` para que todos reciban los datos
	
	Desktop:
	
	```jsx
	let songBlackSwan, songFakeLove;
	let fft;
	let socket;
	
	let hueShift = 0;
	let rotationAngles = [0, 0, 0];
	let baseRadius = 140;
	let spacing = 90;
	let fusionValue = 0; // 0 = tres anillos, 1 = uno solo
	
	let currentMode = 'BlackSwan'; // Cancion inicial
	
	let playButton, pauseButton, stopButton; // Botones de reproduccion musica
	let pulses = []; // Efecto de ondas expansivas
	
	function preload() {
	    soundFormats('mp3');
	    songBlackSwan = loadSound('blackswan.mp3');
	    songFakeLove = loadSound('fakelove.mp3');
	    song = songBlackSwan;
	}
	
	function setup() {
	    createCanvas(1900, 800);
	    colorMode(HSB);
	    fft = new p5.FFT();
	    socket = io();
	
	    // Preparacion volumen inicial canciones
	    songBlackSwan.setVolume(1);
	    songFakeLove.setVolume(0);
	
	    // Botones de control
	    playButton = createButton('▶');
	    pauseButton = createButton('⏸');
	    stopButton = createButton('⏹');
	
	    styleButton(playButton, width - 120, height / 2 - 100);
	    styleButton(pauseButton, width - 120, height / 2);
	    styleButton(stopButton, width - 120, height / 2 + 100);
	
	     playButton.mousePressed(() => {
	    if (!songBlackSwan.isPlaying() && !songFakeLove.isPlaying()) {
	      songBlackSwan.loop();
	      songFakeLove.loop();
	    }
	    });
	
	    pauseButton.mousePressed(() => {
	        songBlackSwan.pause();
	        songFakeLove.pause();
	    });
	
	    stopButton.mousePressed(() => {
	        songBlackSwan.stop();
	        songFakeLove.stop();
	    });
	
	    userStartAudio();
	
	    // Microbit datos botones y acelerometro
	    socket.on('microbit', (data) => {
	        if (data.button === 'A') switchToFakeLove();
	        if (data.button === 'B') switchToBlackSwan();
	
	        if (data.shake) {
	      for (let i = 0; i < 4; i++) {
	        pulses.push({
	          r: 0,
	          alpha: 255,
	          growSpeed: random(10, 25),
	          decaySpeed: random(3, 6)
	        });
	      }
	    }
	    });
	
	    // Mobile datos
	    socket.on('message', handleTouch);
	}
	
	function styleButton(btn, x, y) {
	    btn.position(x, y);
	    btn.size(60, 60);
	    btn.style('font-size', '28px');
	    btn.style('border', 'none');
	    btn.style('border-radius', '50%');
	    btn.style('background', 'rgba(100,0,200,0.4)');
	    btn.style('color', 'white');
	    btn.style('cursor', 'pointer');
	    btn.style('backdrop-filter', 'blur(4px)');
	    btn.mouseOver(() => btn.style('background', 'rgba(150,0,255,0.6)'));
	    btn.mouseOut(() => btn.style('background', 'rgba(100,0,200,0.4)'));
	}
	
	function crossfade(toMode) {
	  const fadeTime = 5.0; // Tiempo de fundido en segundos
	  if (toMode === 'FakeLove') {
	    songBlackSwan.amp(0, fadeTime);
	    songFakeLove.amp(1, fadeTime);
	  } else {
	    songBlackSwan.amp(1, fadeTime);
	    songFakeLove.amp(0, fadeTime);
	  }
	}
	
	function switchToFakeLove() {
	    if (currentMode === 'FakeLove') return;
	    currentMode = 'FakeLove';
	    crossfade('FakeLove');
	    hueShift = 0;
	}
	
	function switchToBlackSwan() {
	    if (currentMode === 'BlackSwan') return;
	    currentMode = 'BlackSwan';
	    crossfade('BlackSwan');
	    hueShift = 0;
	}
	
	function handleTouch(data) {
	    if (data.type === 'touch') {
	        hueShift += data.direction === 'right' ? 10 : -10; // Antes decia: if (data.type === 'touch') { if (data.direction === "left") hueShift -= 10; else if (data.direction === "right") hueShift += 10;}
	    }
	    if (data.type === 'fusion') {
	        fusionValue = constrain(data.value, 0, 1);
	    }
	}
	
	function draw() {
	    background(currentMode === 'BlackSwan' ? 0 : color(280, 80, 30, 0.2));
	    translate(width / 2, height / 2); // Mover origen
	    noFill();
	
	    let spectrum = fft.analyze(); //Para dividir en frecuencias (graves, medios y agudos)
	
	    // Rotaciones independientes (el del medio gira al revés)
	    rotationAngles[0] += 0.005;
	    rotationAngles[1] -= 0.006;
	    rotationAngles[2] += 0.007;
	
	    // Valores de fusión
	    let transition = lerp(0, 1, fusionValue);
	    let mergeOffset = spacing * transition;
	    let alphaOuter = 255 * (1 - transition);
	    let scaleCentral = 1 + 0.4 * transition;
	
	    // Título
	    push();
	    resetMatrix();
	    textAlign(LEFT, CENTER);
	    textSize(64);
	    fill(255);
	    text("Pulse of BTS", 100, height / 2 - 25);
	    pop();
	
	    // Texto informativo funcionamieno microbit
	    push();
	    resetMatrix();
	    textSize(22);
	    fill(200);
	    text("Controles Micro:bit:", 100, height / 2 + 40);
	    text("Botón A → Fake Love", 100, height / 2 + 80);
	    text("Botón B → Black Swan", 100, height / 2 + 110);
	    pop();
	
	    // Dibujo de los tres anillos (se acercan al centro)
	    if (transition < 0.98) {
	        push();
	        strokeWeight(2);
	        drawBars(spectrum, getRainbowColor(0), baseRadius - mergeOffset, baseRadius - mergeOffset + 40, rotationAngles[0], alphaOuter);
	        drawBars(spectrum, getRainbowColor(120), baseRadius + spacing * (1 - transition / 2), baseRadius + spacing * (1 - transition / 2) + 40, rotationAngles[1], 255);
	        drawBars(spectrum, getRainbowColor(240), baseRadius + spacing * 2 - mergeOffset, baseRadius + spacing * 2 - mergeOffset + 40, rotationAngles[2], alphaOuter);
	        pop();
	    }
	
	    // Dibujo del espectro fusionado (uno solo, más grande y brillante)
	    if (transition > 0.02) {
	        push();
	        let glow = map(transition, 0, 1, 0, 80);
	        strokeWeight(2.5 + glow * 0.02);
	        drawBars(spectrum, getRainbowColor(hueShift), (baseRadius + spacing) * scaleCentral, (baseRadius + spacing + 80) * scaleCentral, rotationAngles[1], map(transition,0,1,0,255));
	        pop();
	    }
	
	    // Ondas expansivas
	    push();
	    blendMode(ADD);
	    noFill();
	    for (let i = pulses.length - 1; i >= 0; i--) {
	        let p = pulses[i];
	        strokeWeight(3);
	        let col = currentMode === 'BlackSwan' ? color(200, 100, 100, p.alpha / 255) : color(330, 100, 100, p.alpha / 255);
	        stroke(col);
	        ellipse(0, 0, p.r * 2);
	        p.r += p.growSpeed;
	        p.alpha -= p.decaySpeed;
	        if (p.alpha <= 0) pulses.splice(i, 1);
	    }
	    pop();
	}
	
	// Dibujo de espectros: graves (interno), voces(medio), agudos(externo)
	function drawBars(spectrum, col, minR, maxR, rotationAngle, alphaVal=255, start=0, end=1) {
	    push();
	    rotate(rotationAngle);
	    col.setAlpha(alphaVal);
	    stroke(col);
	    let len = spectrum.length;
	    for (let i = 0; i < 360; i += 3) {
	        let index = floor(map(i,0,360,start*len,end*len));
	        let amp = spectrum[index];
	        let r = map(amp,0,255,minR,maxR); // radio segun la amplitud del sonido
	        let rad = radians(i);
	        line(minR*cos(rad), minR*sin(rad), r*cos(rad), r*sin(rad)); // (coordenadas x y y del radio interno, amplitud)
	    }
	    pop();
	}
	
	function getRainbowColor(offset) { // variacion de paleta de colores
	    let hue = (hueShift + offset) % 360;
	    return color(hue, 100, 100);
	}
	```
	
	En esta version se agrego un nuevo efecto visual de ondas expansivas que aparece cuando el microbit detecta una sacudida (shake). Cada vez que esto pasa, se crean varios pulsos que crecen y se desvanecen desde el centro, dando la sensacion de impacto o energia. Para lograrlo se incluyo el arreglo `pulses[]` y un bloque en `draw()` que dibuja y actualiza esas ondas. Tambien se ajusto el evento del microbit para reconocer el movimiento, manteniendo todo lo demas igual: el cambio entre canciones, los controles y el efecto de fusion siguio funcionando igual que antes

8. Como ya tenia todo lo planeado, quise añadirle un detalle mas, una transicion del color del fondo cada q cambia de cancion. Esto lo logramos:

	```jsx
	// añadiendo nuevas variables
	let bgColor;
	let blackSwanColor;
	let fakeLoveColor;
	let targetMode;
	```
	
	```jsx
	// En setup()
	blackSwanColor = color(0);
	fakeLoveColor = color(280, 80, 30);
	bgColor = blackSwanColor;
	targetMode = 'BlackSwan';
	```
	
	```jsx
	// En switchToFakeLove() y switchToBlackSwan()
	targetMode = 'FakeLove'; // o 'BlackSwan'
	```
	
	```jsx
	// En draw(), antes del background():
	let targetColor = (targetMode === 'BlackSwan') ? blackSwanColor : fakeLoveColor;
	bgColor = lerpColor(bgColor, targetColor, 0.05);
	background(bgColor);
	```
	
	El efecto que se logro fue una clase de interpolacion entre los dos colores de fondo

9. En la segunda clase de la segunda semana de la unidad en los 40 min que me quedaban, quise poner un boton para conectar el microbit ya que la manera en que se estaba conectando era como solito de la nada, no como aprendimos que podiamos como selecionarlo con una ventana emergente. Pero no lo logre y se volvio un locuron. Entonces como en al rubrica lo que no solicitan es que el programa este 100% funcional decidi dejarlo no guardar commit de lo que hice en esos 40 min, ya que si lo hacia la interaccion con el microbit no funcionaba, no se estaban enviando o recibiendo los datos correctamente. Y ya no tuve oportunidad o tiempo para solicitar por fuera de la clase el microbit :p

	De igual forma quede satisfecha con lo logrado, y siento que cumpli con todo lo solicitado. Me hubiera gustado poder poner el boton del microbit

#### 💻Codigos          
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
server.js
```javascript
const express = require('express');
const http = require('http');

const { Server } = require("socket.io"); // const socketIO = require('socket.io');
const { SerialPort } = require('serialport'); // para conectar y leer los datos del microbit...
const { ReadlineParser } = require('@serialport/parser-readline'); //...a traves del puerto USB

const app = express();
const server = http.createServer(app);
const io = new Server(server); // const io = socketIO(server); sintaxis moderna de V4
const port = 3000;

app.use(express.static('public'));

// Microbit
const microbitPort = new SerialPort({ path: 'COM10', baudRate: 115200 }); //REVISAR SIEMPRE QUE SE CAMBIA DE MICROBIT Y MODIFICAR EL COM
const parser = microbitPort.pipe(new ReadlineParser({ delimiter: '\n' }));

// Vrbles acelerometro
let lastX = 0, lastY = 0;
let shakeThreshold = 500; // sensibilidad
let lastShakeTime = 0;

parser.on('data', (line) => { // separar los valores (botones y acelerometro)
    const [x, y, a, b] = line.trim().split(',');
    const data = {
        x: Number(x),
        y: Number(y),
        buttonA: a === 'True' || a === '1',
        buttonB: b === 'True' || b === '1'
    };

    if (data.buttonA) io.emit('microbit', { button: 'A' });
    if (data.buttonB) io.emit('microbit', { button: 'B' });

    // Detectar acelerometro
    const deltaX = Math.abs(data.x - lastX);
    const deltaY = Math.abs(data.y - lastY);
    const now = Date.now();

    if ((deltaX > shakeThreshold || deltaY > shakeThreshold) && (now - lastShakeTime > 1000)) {
        io.emit('microbit', { shake: true });
        lastShakeTime = now;
    }

    lastX = data.x;
    lastY = data.y;
});

// Socket.io
io.on('connection', (socket) => {
    console.log('Nuevo cliente conectado');

    socket.on('message', (data) => { // Comunicacion Mobile → Desktop
        io.emit('message', data); // ahora io.emit en lugar de broadcast para asegurar que los 3 reciban todos los datos de sincronizacion
    });

    socket.on('disconnect', () => {
        console.log('Cliente desconectado');
    });
});

server.listen(port, () => {
    console.log(`Server listening on http://localhost:${port}`);
});
```

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
Sketch.js/desktop:
```javascript
let songBlackSwan, songFakeLove;
let fft;
let socket;

let hueShift = 0;
let rotationAngles = [0, 0, 0];
let baseRadius = 140;
let spacing = 90;
let fusionValue = 0; // 0 = tres anillos, 1 = uno solo

let currentMode = 'BlackSwan'; // Cancion inicial
let targetMode = 'BlackSwan';  // Transicion de fondo

let playButton, pauseButton, stopButton; // Botones de reproduccion musica
let pulses = []; // Efecto de ondas expansivas

// Vrbles de transicion de color fondo
let bgColor;
let blackSwanColor;
let fakeLoveColor

function preload() {
    soundFormats('mp3');
    songBlackSwan = loadSound('blackswan.mp3');
    songFakeLove = loadSound('fakelove.mp3');
    song = songBlackSwan;
}

function setup() {
    createCanvas(1900, 800);
    colorMode(HSB);
    fft = new p5.FFT();
    socket = io();

    // Colores base de las canciones
    blackSwanColor = color(230, 80, 10); // Azul oscuro tenue
    fakeLoveColor = color(320, 90, 25);  // Magenta rojizo
    bgColor = blackSwanColor;

    // Preparacion volumen inicial canciones
    songBlackSwan.setVolume(1);
    songFakeLove.setVolume(0);

    // Botones de control
    playButton = createButton('▶');
    pauseButton = createButton('⏸');
    stopButton = createButton('⏹');

    styleButton(playButton, width - 120, height / 2 - 100);
    styleButton(pauseButton, width - 120, height / 2);
    styleButton(stopButton, width - 120, height / 2 + 100);

     playButton.mousePressed(() => {
    if (!songBlackSwan.isPlaying() && !songFakeLove.isPlaying()) {
      songBlackSwan.loop();
      songFakeLove.loop();
    }
    });

    pauseButton.mousePressed(() => {
        songBlackSwan.pause();
        songFakeLove.pause();
    });

    stopButton.mousePressed(() => {
        songBlackSwan.stop();
        songFakeLove.stop();
    });

    userStartAudio();

    // Microbit datos botones y acelerometro
    socket.on('microbit', (data) => {
        if (data.button === 'A') switchToFakeLove();
        if (data.button === 'B') switchToBlackSwan();

        if (data.shake) {
      for (let i = 0; i < 4; i++) {
        pulses.push({
          r: 0,
          alpha: 255,
          growSpeed: random(10, 25),
          decaySpeed: random(3, 6)
        });
      }
    }
    });

    // Mobile datos
    socket.on('message', handleTouch);
}

function styleButton(btn, x, y) {
    btn.position(x, y);
    btn.size(60, 60);
    btn.style('font-size', '28px');
    btn.style('border', 'none');
    btn.style('border-radius', '50%');
    btn.style('background', 'rgba(100,0,200,0.4)');
    btn.style('color', 'white');
    btn.style('cursor', 'pointer');
    btn.style('backdrop-filter', 'blur(4px)');
    btn.mouseOver(() => btn.style('background', 'rgba(150,0,255,0.6)'));
    btn.mouseOut(() => btn.style('background', 'rgba(100,0,200,0.4)'));
}

function crossfade(toMode) {
  const fadeTime = 5.0; // Tiempo de fundido en segundos
  if (toMode === 'FakeLove') {
    songBlackSwan.amp(0, fadeTime);
    songFakeLove.amp(1, fadeTime);
  } else {
    songBlackSwan.amp(1, fadeTime);
    songFakeLove.amp(0, fadeTime);
  }
}

function switchToFakeLove() {
    if (currentMode === 'FakeLove') return;
    targetMode = 'FakeLove';
    crossfade('FakeLove');
    hueShift = 0;
}

function switchToBlackSwan() {
    if (currentMode === 'BlackSwan') return;
    targetMode = 'BlackSwan';
    crossfade('BlackSwan');
    hueShift = 0;
}

function handleTouch(data) {
    if (data.type === 'touch') {
        hueShift += data.direction === 'right' ? 10 : -10; // Antes decia: if (data.type === 'touch') { if (data.direction === "left") hueShift -= 10; else if (data.direction === "right") hueShift += 10;}
    }
    if (data.type === 'fusion') {
        fusionValue = constrain(data.value, 0, 1);
    }
}

function draw() {
    // Suavizado del fondo entre canciones
    let targetColor = targetMode === 'BlackSwan' ? blackSwanColor : fakeLoveColor;
    bgColor = lerpColor(bgColor, targetColor, 0.02);
    background(bgColor);
    // Actualizar modo actual
    if (abs(hue(bgColor) - hue(targetColor)) < 2) currentMode = targetMode;
    
    translate(width / 2, height / 2); // Mover origen
    noFill();

    let spectrum = fft.analyze(); //Para dividir en frecuencias (graves, medios y agudos)

    // Rotaciones independientes (el del medio gira al revés)
    rotationAngles[0] += 0.005;
    rotationAngles[1] -= 0.006;
    rotationAngles[2] += 0.007;

    // Valores de fusión
    let transition = lerp(0, 1, fusionValue);
    let mergeOffset = spacing * transition;
    let alphaOuter = 255 * (1 - transition);
    let scaleCentral = 1 + 0.4 * transition;

    // Título
    push();
    resetMatrix();
    textAlign(LEFT, CENTER);
    textSize(64);
    fill(255);
    text("Pulse of BTS", 100, height / 2 - 25);
    pop();

    // Texto informativo funcionamieno microbit
    push();
    resetMatrix();
    textSize(22);
    fill(200);
    text("Controles Micro:bit:", 100, height / 2 + 40);
    text("Botón A → Fake Love", 100, height / 2 + 80);
    text("Botón B → Black Swan", 100, height / 2 + 110);
    pop();

    // Dibujo de los tres anillos (se acercan al centro)
    if (transition < 0.98) {
        push();
        strokeWeight(2);
        drawBars(spectrum, getRainbowColor(0), baseRadius - mergeOffset, baseRadius - mergeOffset + 40, rotationAngles[0], alphaOuter);
        drawBars(spectrum, getRainbowColor(120), baseRadius + spacing * (1 - transition / 2), baseRadius + spacing * (1 - transition / 2) + 40, rotationAngles[1], 255);
        drawBars(spectrum, getRainbowColor(240), baseRadius + spacing * 2 - mergeOffset, baseRadius + spacing * 2 - mergeOffset + 40, rotationAngles[2], alphaOuter);
        pop();
    }

    // Dibujo del espectro fusionado (uno solo, más grande y brillante)
    if (transition > 0.02) {
        push();
        let glow = map(transition, 0, 1, 0, 80);
        strokeWeight(2.5 + glow * 0.02);
        drawBars(spectrum, getRainbowColor(hueShift), (baseRadius + spacing) * scaleCentral, (baseRadius + spacing + 80) * scaleCentral, rotationAngles[1], map(transition,0,1,0,255));
        pop();
    }

    // Ondas expansivas
    push();
    blendMode(ADD);
    noFill();
    for (let i = pulses.length - 1; i >= 0; i--) {
        let p = pulses[i];
        strokeWeight(3);
        let col = currentMode === 'BlackSwan' ? color(200, 100, 100, p.alpha / 255) : color(330, 100, 100, p.alpha / 255);
        stroke(col);
        ellipse(0, 0, p.r * 2);
        p.r += p.growSpeed;
        p.alpha -= p.decaySpeed;
        if (p.alpha <= 0) pulses.splice(i, 1);
    }
    pop();
}

// Dibujo de espectros: graves (interno), voces(medio), agudos(externo)
function drawBars(spectrum, col, minR, maxR, rotationAngle, alphaVal=255, start=0, end=1) {
    push();
    rotate(rotationAngle);
    col.setAlpha(alphaVal);
    stroke(col);
    let len = spectrum.length;
    for (let i = 0; i < 360; i += 3) {
        let index = floor(map(i,0,360,start*len,end*len));
        let amp = spectrum[index];
        let r = map(amp,0,255,minR,maxR); // radio segun la amplitud del sonido
        let rad = radians(i);
        line(minR*cos(rad), minR*sin(rad), r*cos(rad), r*sin(rad)); // (coordenadas x y y del radio interno, amplitud)
    }
    pop();
}

function getRainbowColor(offset) { // variacion de paleta de colores
    let hue = (hueShift + offset) % 360;
    return color(hue, 100, 100);
}
```

#### 🔗Enlace al repositorio       
https://github.com/VanDiosa/Pulse-of

## ⭐ Autoevaluación
Nota propuesta: 5 / 5

Justificación:
Propongo un 5 pq complete todas las actividades de la unidad y documente todo en mi bitacora
En la actividad 1, desarrolle los cinco items solicitados. No use IA para generar el diseño de mi proyecto, parti de una base que fue el apply de la unidad anterior, y pense como integrar el microbit de una forma logica y coherente con el concepto general, evitando usar los botones o el acelerometro solo por cumplir
Sobre la actividad 2, cumpli con los 2 items, documente el proceso de construccion mencionando lo que le solicitaba a chat y las modificaciones que fui implementando. Ademas no me limite solo en copiar y pegar codigo, si no que mientras construia iba analizando, tratando de entender y aprender para que era cada funcion, vrble o linea que iba agregando. Todos los codigos estan en la bitacora y el link al repositorio tmb

Por todo esto, ademas de por el esfuerzo y la dedicacion que le meti a la unidad considero que me merezco un 5 :D














