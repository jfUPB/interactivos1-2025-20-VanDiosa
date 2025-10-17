
# Evidencias de la unidad 7

## 🔎 Fase: Set

### 📚Actividad 01    
❓¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?    
R/ La URL que obtuve fue: https://czskkfpf-3000.use2.devtunnels.ms/

Usamos esta URL en lugar de localhost o la IP local pq el celular no puede conectarse directamente al servidor q esta en mi computador. El tunel de Dev Tunnels crea un enlace publico q permite q mi celular pueda comunicarse con el servidor desde internet aunque no este en la misma red que el computador

❓Describe brevemente qué hace npm install y npm start.    
R/ npm install -> sirve para instalar todos los archivos y librerias q necesita el proyecto para funcionar correctamente

npm start -> se usa para iniciar el servidor, q en este caso es el archivo que hace posible la comunicación entre el celular y el computador

❓¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?    
R/ En la terminal se podian ver mensajes del servidor indicando las conexiones y los datos q se recibian desde el celular
Primero aparecieron las lineas:

```
Server is listening on http://localhost:3000  
New client connected  
New client connected

```
Despues se imprimieron los valores de posicion q el celular enviaba al tocar la pantalla, por ejemplo:

```
Received message => { type: 'touch', x: 191.48, y: 222.48 }
```
Los mensajes son iguales para ambos clientes, no se muestran identificadores diferentes. Solo se ve cuando se conectan y los datos q el servidor recibia desde el celular

❓Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?    
R/ La interaccion funciono correctamente, al mover el dedo en la pantalla del celular el circulo en el computador tambien se movia siguiendo la direccion del toque.
Sin embargo note q a veces el movimiento del circulo iba un poco lento, como si hubiera un pequeño retraso. Creo q esto se debio a la conexion a internet, ya q parecia faltarle algo de potencia. Aun asi, la comunicacion entre ambos dispositivos se mantuvo estable y el sistema respondio de forma adecuada

## 🔎 Fase: Seek

### 📚Actividad 02     
❓Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?    
R/ Es necesario pq permite q el celular se pueda conectar al servidor q esta corriendo en mi computador, incluso si no estan en la misma red. Normalmente localhost solo sirve dentro del mismo equipo y la IP local solo funciona si ambos dispositivos comparten el mismo wifi

Con Dev Tunnels se crea una direccion publica (una URL en internet) q hace de puente entre el servidor local y los demas dispositivos. Cuando el celular se conecta a esa URL, Dev Tunnels reenvia la informacion hasta mi servidor en el puerto 3000, y luego envia las respuestas de vuelta al celular

❓Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.    
R/ La funcion touchMoved() se ejecuta cada vez q se toca la pantalla y uno mueve el dedo. En este caso sirve para detectar la posición del toque (usando mouseX y mouseY) y enviar esa informacion al servidor mediante socket.emit()

Para evitar que se envien demasiados mensajes por movimientos muy pequeños (como cuando el dedo tiembla un poco), se usa la variable threshold. Este valor define un limite minimo de movimiento: solo si el dedo se desplaza mas de ese valor el codigo envia los datos al servidor. Esto mejora el rendimiento y evita saturar la conexion con demasiados mensajes

❓Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?    
R/ IP local:
+ Ventaja: Es mas rapido pq la conexion va directamente entre los dispositivos
+ Desventaja: Solo funciona si el celular y el computador estan en la misma red wifi y no hay bloqueos del firewall. Ademas no sirve si el celular usa datos moviles

Dev Tunnels:
+ Ventaja: Permite conectar desde cualquier red de forma segura y sin configurar puertos ni redes
+ Desventaja: Depende de la conexion a internet y puede tener un poco mas de retraso que una conexion local directa

❓Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).    
R/
Celular:    
![Imagen de WhatsApp 2025-10-10 a las 15 05 09_adf5b81c](https://github.com/user-attachments/assets/704478ce-3f83-4af9-aa9b-c7f2158bd78e)

Computador:   
<img width="653" height="746" alt="image" src="https://github.com/user-attachments/assets/68f8e7dd-05b1-4963-9eb0-b242bd9882d3" />

Terminal:    
<img width="1518" height="452" alt="Captura de pantalla 2025-10-10 150209" src="https://github.com/user-attachments/assets/4f4fe050-64b7-4c59-8177-9e14cbbccb71" />


### 📚Actividad 03
❓¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?   
R/ La funcion express.static('public') le indica al servidor q todos los archivos dentro de la carpeta public esten disponibles de forma directa para el navegador

En este caso, dentro de public hay dos carpetas: desktop y mobile, y cada una tiene su propio index.html y sketch.js. Gracias a express.static, el servidor puede mostrar esas paginas sin tener q crear rutas manuales para cada una

Por ejemplo, al abrir la URL del tunel seguida de /mobile o /desktop, el navegador carga automaticamente los archivos de esas carpetas

A diferencia de app.get('/ruta', ...), donde uno debe escribir una ruta especifica y devolver un archivo con res.sendFile(), express.static() simplifica el proceso al servir todos los archivos estaticos (HTML, JS, CSS, imagenes, etc.) de forma automatica

❓Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?    
R/ El flujo del mensaje tactil es el siguiente

1. En el cliente movil, el evento q envia el mensaje es socket.emit('message', touchData) dentro de la funcion touchMoved()
Cada vez q el usuario mueve el dedo, el movil envia al servidor las coordenadas del toque (x y y)

2. El servidor recibe ese mensaje gracias al evento socket.on('message', (message) => {...})

3. Cuando el servidor lo recibe, lo muestra en consola con console.log('Received message =>', message) y luego lo reenvia usando socket.broadcast.emit('message', message)

4. Ese socket.broadcast.emit hace q el mensaje se envie a todos los demas clientes conectados, excepto al q lo mando
   
   Por eso, el circulo del cliente de escritorio se mueve segun el toque del celular, pero el movil no recibe su propio mensaje

No se usa io.emit pq ese enviaria el mensaje a todos los clientes (incluyendo el que lo mando), y tampoco socket.emit pq solo lo enviaria de vuelta al mismo cliente

❓Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?     
R/ Los dos computadores recibirian el mensaje pq el servidor usa socket.broadcast.emit, lo q significa q el mensaje se envia a todos los clientes conectados excepto al q lo envio (en este caso, el celular)
De esa manera ambos computadores podrian mover su circulo al mismo tiempo segun el movimiento del dedo en el movil

❓¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?     
R/ Los mensajes console.log permiten ver en tiempo real lo q esta pasando en el servidor. Por ejemplo, muestran cuando se conecta o desconecta un cliente y q datos esta enviando el movil (como las coordenadas de toque). Esto ayuda a comprobar q la comunicacion entre los dispositivos funciona correctamente y facilita detectar errores o problemas de conexion

### 📚Actividad 04
<img width="5647" height="892" alt="DiagramaUnidad7" src="https://github.com/user-attachments/assets/9887f026-980b-4f8b-b591-190919d4866d" />


## 🛠 Fase: Apply

### 📚Actividad 05
#### Boceto e idea 🌟
El visualizador esta inspirado en Black Swan de BTS.
En el desktop, se encuentran tres circulos concentricos q representan las capas del sonido (voz, altos y bajos) que reaccionan visualmente al ritmo de la cancion. Desde el celular, el usuario puede interactuar en tiempo real: deslizar horizontalmente cambia la paleta de colores, y deslizar verticalmente acerca o separa los circulos, fusionándolos de 3 espectros a 1 solo

<img width="1920" height="1080" alt="BocetoSistemas" src="https://github.com/user-attachments/assets/4d02dec4-dc9b-4a3a-8a16-2862689856d1" />

#### Codigos 💻
server.js
```jsx
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

app.use(express.static('public'));

io.on('connection', (socket) => {
    console.log('New client connected');
    socket.on('message', (message) => {
        console.log('Received message =>', message);
        socket.broadcast.emit('message', message);
    });

    socket.on('disconnect', () => {
        console.log('Client disconnected');
    });
});

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
});
```

desktop/sketch.js
```jsx
let song;
let fft;
let fusion = false;
let socket;

let hueShift = 0;
let rotationAngles = [0, 0, 0];
let baseRadius = 140;
let spacing = 90;
let transition = 0; // 0 = tres anillos, 1 = uno solo

function preload() {
    soundFormats('mp3');
    song = loadSound('blackswan.mp3');
}

function setup() {
    createCanvas(800, 800);
    colorMode(HSB);
    fft = new p5.FFT();
    socket = io();

    socket.on('message', handleTouch);

    userStartAudio().then(() => {
        if (!song.isPlaying()) song.loop();
    });
}

function handleTouch(data) {
    if (data.type === 'touch') {
        if (data.direction === "left") hueShift -= 10;
        else if (data.direction === "right") hueShift += 10;
        else if (data.direction === "down") fusion = true;
        else if (data.direction === "up") fusion = false;
    }
}

function draw() {
    background(0, 0.2);
    translate(width / 2, height / 2);
    noFill();

    let spectrum = fft.analyze();

    // Rotaciones independientes (el del medio gira al revés)
    rotationAngles[0] += 0.005; 
    rotationAngles[1] -= 0.006;
    rotationAngles[2] += 0.007;

    // Transición suave entre 3 y 1 espectro
    if (fusion) transition = lerp(transition, 1, 0.05);
    else transition = lerp(transition, 0, 0.05);

    // Valores de transición
    let mergeOffset = spacing * transition;
    let alphaOuter = 255 * (1 - transition);
    let scaleCentral = 1 + 0.4 * transition;

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
        drawBars(
            spectrum,
            getRainbowColor(hueShift),
            (baseRadius + spacing) * scaleCentral,
            (baseRadius + spacing + 80) * scaleCentral,
            rotationAngles[1],
            map(transition, 0, 1, 0, 255)
        );
        pop();
    }
}

// DIbujo de espectros dependientes a graves (interno), voces(medio), agudos(externo)
function drawBars(spectrum, col, minR, maxR, rotationAngle, alphaVal = 255, start = 0, end = 1) {
    push();
    rotate(rotationAngle);
    col.setAlpha(alphaVal);
    stroke(col);
    let len = spectrum.length;
    for (let i = 0; i < 360; i += 3) {
        let index = floor(map(i, 0, 360, start * len, end * len));
        let amp = spectrum[index];
        let r = map(amp, 0, 255, minR, maxR);
        let rad = radians(i);
        let x1 = minR * cos(rad);
        let y1 = minR * sin(rad);
        let x2 = r * cos(rad);
        let y2 = r * sin(rad);
        line(x1, y1, x2, y2);
    }
    pop();
}

function getRainbowColor(offset) {
    let hue = (hueShift + offset) % 360;
    return color(hue, 100, 100);
}

```

mobile/sketch.js
```jsx
let socket;
let lastTouchX = null;
let lastTouchY = null;
let lastSendTime = 0;
const threshold = 30; // movimiento mínimo para detectar un gesto
const cooldown = 300; // milisegundos entre gestos

function setup() {
    createCanvas(360, 500); 
    background(0);
    fill(255);
    textAlign(CENTER, CENTER);
    textSize(20);
    text('Pulse of Swan 🦢', width / 2, height / 2 - 50);
    textSize(15);
    text('Desliza en dirección horizontal o vertical', width / 2, height / 2 + 30);

    socket = io();

    socket.on('connect', () => console.log('Conectado al servidor'));
    socket.on('disconnect', () => console.log('Desconectado del servidor'));
}

function touchStarted() {
    lastTouchX = mouseX;
    lastTouchY = mouseY;
}

function touchMoved() {
    if (!socket || !socket.connected) return false;

    const now = millis();
    if (now - lastSendTime < cooldown) return false; // evita enviar gestos seguidos

    let dx = mouseX - lastTouchX;
    let dy = mouseY - lastTouchY;

    if (abs(dx) < threshold && abs(dy) < threshold) return false; // ignorar movimientos pequeños

    let direction = "";
    if (abs(dx) > abs(dy)) {
        direction = dx > 0 ? "right" : "left";
    } else {
        direction = dy > 0 ? "down" : "up";
    }

    socket.emit('message', { type: 'touch', direction });
    lastSendTime = now;

    // Reinicia punto de referencia
    lastTouchX = mouseX;
    lastTouchY = mouseY;

    background(0);
    fill(255);
    textSize(20);
    let mensaje = "";

    switch (direction) {
        case "right":
            mensaje = "Deslizaste hacia la derecha →";
            break;
        case "left":
            mensaje = "← Deslizaste hacia la izquierda";
            break;
        case "down":
            mensaje = "⬇ Capas fusionadas";
            break;
        case "up":
            mensaje = "⬆ Capas separadas";
            break;
    }

    text(mensaje, width / 2, height / 2);
    return false;
}
```

#### Capturas de la app 📸
<img width="812" height="810" alt="Captura de pantalla 2025-10-17 002430" src="https://github.com/user-attachments/assets/7b86f5b3-c007-4653-accc-bf74b140dbf3" />
<img width="816" height="813" alt="Captura de pantalla 2025-10-17 002443" src="https://github.com/user-attachments/assets/97aaefc5-9c2e-45a2-a7b4-7c1c7b202dd3" />


#### Enlace al repositorio 🔗
La aplicación se encuentra aqui:
https://github.com/VanDiosa/Pulse-of-Swan

## ⭐ Autoevaluacion
Nota propuesta: 5 / 5

Justificación:  
Propongo un 5 pq complete todas las actividades de la unidad y documente cada paso en mi bitacora. No solo ejecute las tareas, sino que analice y entendi los conceptos nuevos (Dev Tunnels, Socket.IO, touch events en p5.js, etc). Probe, depure y mejore el caso de estudio base hasta convertirlo en mi proyecto final (Pulse of Swan), implemente la conexion movil→servidor→escritorio, ajuste la logica de gestos, use transiciones visuales coherentes con la musica

Defensa de cada actividad:
+ Actividad 1: Segui las instrucciones completas y deje registro de mis resultados  
+ Actividad 2: Analice los conceptos nuevos y busque entenderlos a fondo
+ Actividad 3: Comprendi como funciona el servidor y la comunicacion entre clientes 
+ Actividad 4: Realice el diagrama siguiendo lo solicitado
+ Actividad 5: Diseñe y planifique el visualizador. Implemente, probe y fui ajustando mi aplicacion, reflexionando sobre los errores y mejoras  

En general, considero que mi desempeño fue constante y responsable, y que mi nota refleja tanto el esfuerzo como el aprendizaje obtenido





