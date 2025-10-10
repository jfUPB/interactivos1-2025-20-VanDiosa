
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

### 📚Actividad 04

## 🛠 Fase: Apply

### 📚Actividad 05



