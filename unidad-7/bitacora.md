
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

## 🛠 Fase: Apply

### 📚Actividad 05




