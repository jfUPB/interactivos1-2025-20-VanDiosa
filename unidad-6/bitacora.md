
# Evidencias de la unidad 6

## 🔎 Fase: Set

### 📚Actividad 01: Preparación del entorno y primer contacto    

❓¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito? 

R/ Al ejecutar ese comando aparecio una carpeta nueva en el visual code (node_modules), donde se descargaron e instalaron las dependendencias. Creo que su proposito es darle al programa las herramientas que necesita para poder funcionar correctamente y para lograr que las dos paginas se puedan comunicar   
<img width="584" height="705" alt="image" src="https://github.com/user-attachments/assets/bd767aab-fe3f-4992-9faf-ba668e1a829a" />

❓¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?    

R/ En la captura muestro el mensaje en especifico:
<img width="1532" height="231" alt="image" src="https://github.com/user-attachments/assets/b3cd1079-ea36-4afc-85e4-1f1b3d58a062" />
Indica que el programa se esta ejecutando y que el server esta escuchando en esta URL: http://localhost:3000/

❓Describe lo que ves inicialmente en page1 y page2 en tu navegador.  

R/ Inicialmente al abrir page 1 sale el mensaje "Esperando conexion de la otra ventana", luego al abrir la page 2 sale el mensaje "sincronizando datos". Finalmente en ambas ventanas se muestra un circulo, y cada uno de los circulos evidencia la conexión con el otro, lo cual significa que que ya estan sincronizados

<img width="1919" height="1024" alt="image" src="https://github.com/user-attachments/assets/efb19400-a966-4e96-b9d8-154d31967cbd" />


❓¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?

R/ En la terminal se muestran mensajes que confirman la conexion de los clientes. Al abrir page 1 aparecio un mensaje indicando la conexion del primer cliente y al abrir page 2 se mostro un mensaje similar pero confirmando que el segundo cliente tmb se conecto

<img width="1096" height="297" alt="image" src="https://github.com/user-attachments/assets/d16464fe-33c3-4f6a-bd0d-51755e63e8a0" />

 Para cada page en la terminar se nos da un ID, unos datos enviados de cada ventana (posiciones en x y, altura y anchura de la ventana), el estado de conexion entre las pagina (cuando esta desconectada la page 1: 0 cuando si esta conectada sale page 1: 1) y el estadode sincronizacion entre las dos

❓Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?   

R/ Visualmente: cuando se mueve una ventana, el circulo de esa pagina cambia de posicion y automaticamente se refleja en la otra ventana, mostrando una sincronizacion en tiempo real
<img width="1919" height="1011" alt="image" src="https://github.com/user-attachments/assets/84965675-6cd5-4517-858c-01d50d6172f3" />

Consola del navegador: aparecen mensajes como “Sync status: SYNCED” y “Received valid remote data”, junto con las coordenadas y dimensiones de la ventana (x, y, width, height), lo que nos indica que los datos se estan recibiendo y aplicando correctamente en cada page
<img width="1673" height="1008" alt="image" src="https://github.com/user-attachments/assets/c937122e-02ff-4a2d-a2a0-f791b77a0a0c" />


Terminal del servidor: los mensajes aqui muestran las coordenadas (x, y), el tamaño de las ventanas cada vez que se mueven, y se confirma que ambos pages siguen conectados y sincronizados
<img width="1117" height="667" alt="image" src="https://github.com/user-attachments/assets/e864d359-c03b-4b17-af6f-801a956b15e0" />

## 🔎 Fase: Seek

### 📚Actividad 02     
🧐✍️¿Qué es Internet?    
Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.    

R/ En mi casa y en la universidad normalmente uso wifi. Al ser como la entrada a internet si se corta, aunque mi pc este prendido no podria entrar a paginas, enviar mensajes o usar apps en linea. Siguiendo con la analogia de los vehiculos, seria como tener el carro listo pero sin una carretera por la que pueda andar

🧐✍️Navegador y servidor   
¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?

R/ En un restaurante: la clienta soy yo pidiendo un plato, el servidor es el mesero/cocina entregando la comida

En una libreria: el cliente es quien solicita un libro, el servidor es el vendedor que lo busca y entrega

🧐✍️¿Qué es una URL?   
Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?

R/ Esta es la URL de uno de los sitios web que mas visito ultimamente: https://www.netflix.com/browse/my-list?jbv=82024665 (Un anime llamado La nobleza de las flores en mi lista de netflix) 

+ Procolo: https://
+ Nombre de dominio: www.netflix.com
+ Ruta: /browse/my-list?jbv=82024665

Si solo escribo www.netflix.com, el servidor me envia a la pagina de inicio por defecto de netflix 

🧐✍️Protocolo HTTP    
Compara HTTP con los protocolos seriales que usaste. ¿Qué similitudes encuentras? ¿Qué diferencias clave ves?¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?

R/ 
+ Similitudes: Los tres protocolos son reglas de comunicacion donde se asegura que dos dispositivos se puedan entender. En todos los casos hay un emisor y un receptor que intercambian informacion siguiendo un formato predefinido y se usan mensajes lo mas estructurado posibles para evitar datos confusos o incompletos

+ Diferencias: Por el lado de los protocolos seriales (ASCCI o binario) la comunicacion era mas basica ya que solo se usaban secuencias de bits o caracteres, marcando inicio y fin por paquete    
En cuanto a HTPP la communicacion es mas completa ya que no solo se envian datos si no tambien metadatos como metodos, cabeceras, codigo de estado (ejemplos: GET, tipo de contenido, 200 OK, etc). Ademas este protocolo esta diseñado para q funcione sobre una red global como por ejemplo internet, donde hay muchos servidores y diversos clientes, en comparacion con ASCII/binario donde la comunicacion era local (microbit-pc)

+ El por que de la complejidad de HTTP: Lo que entiendo es que en protocolo (HTTP) necesita ser complejo pq con solo datos como los que habiamos estado trabajando no basta. Ahora se necesita indicar que se quiere, en que formato, como manejar errores. Solo enviar bytes ocasionaria que el navegador no sepa si esos datos son un texto, una imagen, un video, un error. Ser tan especificos por decirlo asi, permite que internet funcione universalmente, de modo que cualquier cliente pueda comunicarse con cualquier servidor

🧐✍️HTML, CSS y JavaScript    
Piensa en una página web simple, como un formulario de login.
+ ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?
+ ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?
+ ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?

R/ 
+ HTML: Los campos de usuario y contraseñe, el boton de ingresar
+ CSS: El color del boton, la imagen o el color del fondo, el tipo y el tamaño de la tipografia
+ JavaScript: Comprobar que no se dejen campos vacios, comprobar que los datos son correctos, mostrar mensaje de usuario o contraseña incorrecta

🧐✍️¿Cómo se ejecuta JavaScript?    
Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.
+ ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?
+ ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?

R/ El modelo basado en eventos solo reacciona cuando ocurre algun cambio a comparacion del buccle draw() que se dibuja constantemente incluso si nada cambio. La ventaja es que es mucho mas eficiente para interfaces web usar el modelo basado en eventos pq no se gastarian recursos innecesarios al redibujar constantemente, ya que solo actuaria cuando el usuaria o el servidor asi lo requieran

🧐✍️¿Qué es Node.js?    
¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?

R/ Pq se usaria un solo protocolo en todo el proyecto, permitiendo que un mismo desarrollador trabaje en ambos espacios sin tener que aprender o usar un lenguaje diferente. Eso podria lograr que el codigo sea mas facil de compartir y entender, y ademas se podria reutilizar funciones en ambos lador

🧐✍️WebSockets y Socket.IO    
Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?

R/
+ HTTP tradicional: funciona por peticion y respuesta. Es como mandar correos: yo envio uno y espero la respuesta
+ Usando WebSockets/Socket.IO: abren un canal de comunicacion permanente. Es como una llamada telefonica donde ambos pueden hablar en cualquier momento sin tener que pedir permiso formal

Apps: whatsapp web, messenger, juegos multijugador en el navegador, google docs y parecidos

### 📚Actividad 03    
#### 🧐🧪✍️ Experimento 1    
+ Detén el servidor si está corriendo. ✔️
  
+ Modificaciones al servidor: Cambia la primera ruta de /page1 a /pagina_uno. ✔️     
Antes:     
<img width="810" height="212" alt="Captura de pantalla 2025-10-01 112544" src="https://github.com/user-attachments/assets/bcbb3db1-a33d-486f-8437-b2617bf342f1" />

Despues:     
<img width="828" height="209" alt="Captura de pantalla 2025-10-01 112640" src="https://github.com/user-attachments/assets/e5f4842b-3592-4ec9-a221-216163e76173" />

+ Inicia el servidor. ✔️

+ Intenta acceder a http://localhost:3000/page1. ¿Funciona? ✔️    
R/ No funciona, al modificar la ruta en el codigo la direccion /page1 dejo de estar definida por lo que al intentar acceder a ella no se encuentra coincidencias y responde con un error
<img width="487" height="184" alt="Captura de pantalla 2025-10-01 112754" src="https://github.com/user-attachments/assets/d59a3715-37a4-43eb-b2c6-972b2cba35e1" />

+ Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona? ✔️    
R/ Si funciona, como definimos la ruta como /pagina_uno esa es la URL valida del momento y el servidor la asocia con page1.html
<img width="690" height="318" alt="Captura de pantalla 2025-10-01 112824" src="https://github.com/user-attachments/assets/eabde3bc-6e71-4c34-a788-0c48c28c9de8" />

+ ¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas? Restaura el código. ✔️    
R/ Si la URL no coincide exactamente con la ruta que se define de manera explicita en el codigo (/page1 ≠ /pagina_uno), el servidor devuelve un error: Cannot GET /page1. O sea las respuestas dependen directamente de como esten configuradas las rutas en el servidor    

#### 🧐🧪✍️ Experimento 2  
+ Asegúrate de que el servidor esté corriendo (npm start). ✔️

+ Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID. ✔️
<img width="892" height="151" alt="Captura de pantalla 2025-10-01 135619" src="https://github.com/user-attachments/assets/b0aa5598-ef51-4e9c-88ea-ba10abc448b7" />
R/ El mensaje que salio fue "A user connected - ID: ZYRVhlh8Rd3KyAbhAAAB", esto significa que un cliente nuevo (pestaña con page1) se conecto y se le asigno un ID unico. Ademas esa pestaña mando datos de su ventana (posicion y tamaño) y el servidor guardo esa informacion y el servidor hace un chequeo del estado (1 cliente conectado, en page1, y no esta sincronizado con nadie)

+ Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente? ✔️
<img width="899" height="195" alt="Captura de pantalla 2025-10-01 135736" src="https://github.com/user-attachments/assets/18b454e8-d8f0-44ba-9283-8e837aa43f37" />

R/ El mensaje q salio fue: "A user connected - ID: NcI86hIPvrGrjfgKAAAD", este es un segundo cliente (otra pestaña) con su propio ID. Y ahora el servidor detecta que hay dos pestañas activas, una en page1 y otra en page2

Tmb mostro "All clients are fully synced", lo que significa que ambos clientes compartieron sus datos y confirmaron sincronizacion

+ Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste? ✔️
<img width="497" height="35" alt="Captura de pantalla 2025-10-01 141759" src="https://github.com/user-attachments/assets/586f51a0-e226-4d9d-ba24-b2e725ed6d1c" />

R/ El mensaje que salio fue: "User disconnected - ID: ZYRVhlh8Rd3KyAbhAAAB", lo que significa que el servidor detecta la desconexion y borro el ID de su lista interna

+ Cierra la pestaña de page2. Observa la terminal. ✔️
<img width="502" height="34" alt="Captura de pantalla 2025-10-01 141821" src="https://github.com/user-attachments/assets/09d79c98-6902-4fb1-846a-88755d313794" />

R/ El mensaje que salio fue: "User disconnected - ID: NcI86hIPvrGrjfgKAAAD", significa lo mismo q lo anterior


CONCLUSIÓN DEL EXPERIMENTO 2: cada conexion tiene un ID distinto (aunque sea desde el mismo computador y navegador). Cuando cerre la pestaña, el servidor detecta la desconexion y borra ese ID de su lista de clientes conectados


#### 🧐🧪✍️ Experimento 3  
+ Inicia el servidor y abre page1 y page2. ✔️

+ Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves? ✔️

<img width="878" height="255" alt="Captura de pantalla 2025-10-01 143905" src="https://github.com/user-attachments/assets/cdeef18d-c347-40e0-b34c-977c6e8de7ce" />

R/ En la terminal aparece el evento `Received win1update`con los datos de la posición y tamaño de la ventana . Ejemplo:  `{ x: -6, y: 306, width: 610, height: 244 }`

+ Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves? ✔️

<img width="896" height="254" alt="Captura de pantalla 2025-10-01 143936" src="https://github.com/user-attachments/assets/80c91c99-065c-4307-8aa0-63bac3183ac7" />

R/ En la terminal aparece el evento `Received win2update`con los datos de la posición y tamaño de la ventana . Ejemplo:  `{ x: 368, y: 0, width: 904, height: 156 }`

CONCLUSION DEL EXPERIMENTO 3 HASTA AQUI: Cada pagina tiene su propio evento de actualizacion y el servidor puede distinguir de quien vienen los datos

+ Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit. ✔️

Codigo antes:

<img width="1017" height="548" alt="Captura de pantalla 2025-10-01 145342" src="https://github.com/user-attachments/assets/abb433b5-34c9-4df7-be93-52e119d4edc1" />


Codigo despues:

<img width="1018" height="547" alt="Captura de pantalla 2025-10-01 145356" src="https://github.com/user-attachments/assets/a9ae0344-70fa-4176-ae27-ac0d6a80ae1b" />


R/  Cuando movi page 1 el servidor recibio el evento y lo registro en la consola (se ve win1update…), PERO esos movimientos no se ven reflejados en page 2, la informacion no le esta llegando a ese cliente. Con `socket.emit(...)` solo el cliente que mando el evento recibe su propia info, asi que no hay sincronizacien entre las paginas; en cambio con `socket.broadcast.emit(...)` page1 y page2 se sincronizan porque cada vez que uno manda datos, el servidor los envia a los demas clientes (En pocas palabras, emit envia solo al cliente emisor; broadcast.emit envia a todos los demss clientes conectados)

#### 🧐🧪✍️ Experimento 4  
+ Detén el servidor. ✔️

+ Cambia const port = 3000; a const port = 3001;.✔️

+ Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando?✔️
    
<img width="993" height="191" alt="Captura de pantalla 2025-10-01 150925" src="https://github.com/user-attachments/assets/5fdf6f8a-fb6e-485f-b796-ab2cef65e5b3" />

R/ `Server is listening on [http://localhost:3001](http://localhost:3001/)`
    
+ Intenta abrir http://localhost:3000/page1. ¿Funciona?✔️
    
<img width="655" height="671" alt="Captura de pantalla 2025-10-01 151006" src="https://github.com/user-attachments/assets/15044085-a1e1-4d32-a364-31347c5e0e59" />
    
R/ No funciona pq el servidor ya no esta escuchando en el puerto 3000. Esa direccion quedo vacia o innexistente y por eso el navegador no encuentra la pagina✔️
    
+ Intenta abrir http://localhost:3001/page1. ¿Funciona?✔️
    
<img width="668" height="291" alt="Captura de pantalla 2025-10-01 151041" src="https://github.com/user-attachments/assets/bdd9e577-2a9c-4cbf-a9a1-84ddf1348c69" />
    
R/ Si funciona, pq el servidor ahora esta activo en el puerto 3001 y responde a las solicitudes en esa direccion
    
+ ¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000. ✔️
  
R/ La variable `port` define el numero de puerto donde el servidor escucha. Al cambiarla de `3000` a `3001`, el servidor dejo de atender en la direccion anterior y pasa a la nueva    
La funcion `listen` usa esa variable para abrir la puerta de comunicacion, por eso solo funciona con la URL que coincide con el puerto configurado

### 📚Actividad 04: Explorando los clientes (p5.js + Socket.IO)        
#### 🧐🧪✍️ Experimento 1    
+ Abre page2.html en tu navegador (con el servidor corriendo). ✔️
+ Abre la consola de desarrollador (F12). ✔️

<img width="1289" height="408" alt="Captura de pantalla 2025-10-02 120452" src="https://github.com/user-attachments/assets/369708d1-d8e0-4ba6-b22c-7ef1e5f25cab" />

+ Detén el servidor Node.js (Ctrl+C). ✔️

<img width="707" height="90" alt="Captura de pantalla 2025-10-02 120632" src="https://github.com/user-attachments/assets/f7a29589-b27f-4682-9409-733fb1343d94" />

R/ Cuando detuve el servidor, la consola mostro el error: `net::ERR_CONNECTION_REFUSED`(el navegador intento reconectarse pero el servidor ya no estaba disponible

+ Refresca la página page2.html. Observa la consola del navegador. ¿Ves algún error relacionado con la conexión? ¿Qué indica? ✔️

<img width="1296" height="957" alt="Captura de pantalla 2025-10-02 125651" src="https://github.com/user-attachments/assets/f02253f4-a793-46c2-8129-aa3bff9dba17" />

R/ Al refrescar page2.html con el servidor detenido, ya no aparecieron mensajes nuevos en la consola, porque el cliente no pudo ni iniciar la conexion

+ Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores?  ✔️

R/ No habia errores en la consola en ese momento, ya que habian desaparecido cuando se refresco la pagina con el servidor apagado. Al reiniciar el servidor y volver a refrescar, la consola mostro nuevamente los mensajes de conexion correctos, como en la primera captura:

```
page2.js:30 Connected with ID: HybT7X6XsnMBABYvAAAB
page2.js:51 Sync status: NOT SYNCED
page2.js:44 Received valid remote data: {x: 0, y: 0, width: 100, height: 100}
page2.js:51 Sync status: NOT SYNCED
```

#### 🧐🧪✍️ Experimento 2    
+ Comenta la línea socket.emit(‘win2update’, currentPageData, socket.id); dentro del listener connect. ✔️

<img width="1380" height="456" alt="Captura de pantalla 2025-10-02 133425" src="https://github.com/user-attachments/assets/19477507-9215-422a-8d28-d0f380369f0a" />

+ Reinicia el servidor y refresca page1.html y page2.html. ✔️

<img width="1919" height="1009" alt="Captura de pantalla 2025-10-02 133244" src="https://github.com/user-attachments/assets/976a6d26-0452-48fd-972f-a9c095cc03fa" />

+ Mueve la ventana de page2 un poco para que envíe una actualización. ✔️

<img width="1591" height="728" alt="Captura de pantalla 2025-10-02 133324" src="https://github.com/user-attachments/assets/d06cf606-d0fc-4e7f-84a5-ccc9c2a31531" />

+ ¿Qué pasó? ¿Por qué? ✔️

R/ Al reiniciar el servidor y refrescar page1 y page2, ambas ventanas cargaron y lograron sincronizarse inicialmente (se veian los circulos rojos unidos por la linea)

Pero al mover la ventana de page2 , la posicion ya no le llego a page1, entonces la posicion de page1 no se actualizo con respecto al movimiento de page2

Al comentar la linea `[//socket.emit](https://socket.emit/)('win2update', currentPageData, [socket.id](http://socket.id/));` dentro de la funcion `checkWindowPosition()` , page2 solo pudo enviar su posicion inicial gracias a la funcion setup. Eso permitio una primera sincronizacion, pero despues ya no pudo seguir enviando nuevas coordenadas, dañando la actualizacion en tiempo real

#### 🧐🧪✍️ Experimento 3    
+ Abre ambas páginas. ✔️
+ Mueve la ventana de page1. Observa la consola del navegador de page2. ¿Qué datos muestra? ✔️

<img width="1919" height="1010" alt="Captura de pantalla 2025-10-02 171036" src="https://github.com/user-attachments/assets/ade2e76d-2063-47f0-9b5d-1dd009c7316f" />

R/  En la consola de **page2** aparecen mensajes como:

```
Received valid remote data:
{ x: -138, y: 86, width: 750, height: 312 }
Sync status: SYNCED
```

Eso significa que page2 esta recibiendo en tiempo real la informacion de posicion enviada por page1

+ Mueve la ventana de page2. Observa la consola de page1. ¿Qué pasa? ¿Por qué? ✔️
    
<img width="1919" height="1006" alt="Captura de pantalla 2025-10-02 171247" src="https://github.com/user-attachments/assets/b8b3c527-77d9-4615-bf38-b1d792392cdc" />    

R/ En la consola de page1 se muestran los mismos mensajes con las coordenadas actualizadas de page2
Ocurre pq cada pagina al detectar un cambio en su posicion envia un evento (`win1update` o `win2update`) al servidor. Este reenvia los datos a la otra pagina, y ahi es donde se registran en su consola. Asi ambas ventanas se mantienen sincronizadas y saben en que posicion esta la otra

#### 🧐🧪✍️ Experimento 4    

+ Observa checkWindowPosition() en page2.js y modifica el código del if para comprobar si el código dentro de este se ejecuta. ✔️

Antes:

```jsx
function checkWindowPosition() {
    currentPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
        currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height) {

        point2 = [currentPageData.width / 2, currentPageData.height / 2]
        socket.emit('win2update', currentPageData, socket.id);
        previousPageData = currentPageData; 
    }
}
```

Despues:

```jsx
function checkWindowPosition() {
    currentPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
        currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height) {

        console.log("El if se ejecuto");

        point2 = [currentPageData.width / 2, currentPageData.height / 2]
        socket.emit('win2update', currentPageData, socket.id);
        previousPageData = currentPageData; 
    }
}
```

+ Mueve cada ventana y observa las consolas. ✔️

<img width="1163" height="890" alt="Captura de pantalla 2025-10-02 174301" src="https://github.com/user-attachments/assets/3db45fd1-7546-4c1a-83b8-564fed591668" />

+ ¿Qué puedes concluir y por qué? ✔️

R/  Despues de cambiar el codigo e iniciar adecuadamente todo, al mover page2 y revisar la consola pude concluir que: El **if** dentro de `checkWindowPosition()` en `page2.js` funciona correctamente, o sea, se dispara siempre que la posicion o tamaño de Page2 cambia

Por otro lado al mover la ventana de page1, en la consola de page2 se mostro que no solo se ejecuta su propio envio de datos, sino que ademas recibe datos del servidor cuando page1 se mueve

Es decir, la sincronizacion funciona en ambos sentidos

#### 🧐🧪✍️ Experimento 5    
+ Cambia el background(220) para que dependa de la distancia entre las ventanas. Puedes calcular la magnitud del resultingVector usando let distancia = resultingVector.mag(); y luego usa map() para convertir esa distancia a un valor de gris o color. background(map(distancia, 0, 1000, 255, 0)); (ajusta el rango 0-1000 según sea necesario).  ✔️

Codigo añadido en fuction draw():

```jsx
		// Calcular la distancia
    let distancia = resultingVector.mag();
    
    // Fondo azul dinámico según la distancia
    let azul = map(distancia, 0, 1000, 255, 0); 
    background(0, 0, azul);
```

Asi quedo la funcion completa:

```jsx
function draw() {
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);

    // Calcular la distancia
    let distancia = resultingVector.mag();
    
    // Fondo azul dinámico según la distancia
    let azul = map(distancia, 0, 1000, 255, 0); 
    background(0, 0, azul);
    
    if (!isConnected) {
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }
    
    if (!hasRemoteData) {
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }
    
    if (!isFullySynced) {
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }

    // Solo dibujar cuando esté completamente sincronizado
    drawCircle(point2[0], point2[1]);
    checkWindowPosition();
    
    stroke(50);
    strokeWeight(20);
    drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
    line(point2[0], point2[1], resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
}

```

Algunas capturas donde se puede ver el cambio de color en page 2 dependiendo de la distancia:

<img width="1919" height="999" alt="Captura de pantalla 2025-10-02 190526" src="https://github.com/user-attachments/assets/6c4a1031-de12-456f-b65c-42ea955b5b76" />

<img width="1919" height="940" alt="Captura de pantalla 2025-10-02 190536" src="https://github.com/user-attachments/assets/0e287851-b8d7-4cc3-a19e-db57ac78dde2" />

<img width="1019" height="1012" alt="Captura de pantalla 2025-10-02 190614" src="https://github.com/user-attachments/assets/ac99e2c5-4a86-4de9-87c4-2b01174f6af1" />

+ Inventa otra modificación creativa.  ✔️
Para la segunda modificacion creativa me gusta la idea de que el tamaño del circulo de page2 cambiara de acuerdo a la distancia entre las dos ventanas

Esto se logro usando la función `map()` sobre la variable `distancia` creada en la modificacion anterior. Asi cuando las ventanas estan mas lejos el radio del circulo2 es mayor  y cuando las ventanas se acercan el radio es menor

<img width="1919" height="1008" alt="Captura de pantalla 2025-10-02 194413" src="https://github.com/user-attachments/assets/cc689889-e3a0-4f89-9cc7-078756eb6e5a" />

<img width="1145" height="624" alt="Captura de pantalla 2025-10-02 194913" src="https://github.com/user-attachments/assets/2a69aa83-2a83-414f-a2ae-f1e6eeeb7a50" />

Codigo añadido / modificado en fuction draw():
Se calculo un radio dinamico usando la funcion map() aplicada a la distancia

```jsx
		let radio = map(distancia, 0, 1000, 50, 200);

    // Solo dibujar cuando esté completamente sincronizado
    drawCircle(point2[0], point2[1], radio);

    drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2, radio);
    
```

Asi quedo la funcion completa:

```jsx
function draw() {
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);

    // Calcular la distancia
    let distancia = resultingVector.mag();
    
    // Fondo azul dinamico segun la distancia
    let azul = map(distancia, 0, 1000, 255, 0); 
    background(0, 0, azul);

    
    
    if (!isConnected) {
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }
    
    if (!hasRemoteData) {
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }
    
    if (!isFullySynced) {
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }

     let radio = map(distancia, 0, 1000, 50, 200);

    // Solo dibujar cuando esté completamente sincronizado
    drawCircle(point2[0], point2[1], radio);
    
    checkWindowPosition();
    
    stroke(50);
    strokeWeight(20);
    // se agrego el valor radio
    drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2, radio);
    line(point2[0], point2[1], resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
}
```

Funcion drawCircle() modificada:
Se modifico la funcion drawCircle(x, y) para que aceptara un tercer parametro r que controla el radio del circulo

```jsx
function drawCircle(x, y, r) {
    fill(255, 0, 0);
    ellipse(x, y, r, r);
}
```

### 📚Actividad 05: App Conexión de Corazones
#### Idea Principal 🌠
Desarrolle una aplicacion que representa la conexión en tiempo real entre dos usuarios mediante una metafora visual de corazones que palpitan. La interaccion no es simplenete funcional, si no que queria una experiencia estetica y emocional. Para la idea me inspire en el concepto de **Love Alarm**, donde las emociones y la conexión entre personas se representan visualmente

Los corazones se enlazan a traves de particulas doradas, generando un vinculo visual que refleja la cercania y lo sincronizados que estan

Las caracteristicas de la aplicación son:
+ Latido sincronizado de los corazones de cada usuario
+ Fondo dinamico que varia del gris al rojo segun la proximidad entre los corazones
+ Particulas doradas que simbolizan la energia compartida y la conexion magica
+ Ondas expansivas que aparecen al haber contacto

#### Bocetos 📝

#### Codigos 💻
A el codigo del server, solo le personalice los mensajes de la consolo para que estuvieran de acuerdo a la tematica:}

```jsx
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
const path = require('path');
const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

let page1 = { x: 0, y: 0, width: 100, height: 100 };
let page2 = { x: 0, y: 0, width: 100, height: 100 };
let connectedClients = new Map();
let syncedClients = new Set();

app.use(express.static(path.join(__dirname, 'views')));

app.get('/page1', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page1.html'));
});

app.get('/page2', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page2.html'));
});

io.on('connection', (socket) => {
    console.log('Conexión establecida- ID:', socket.id);
    connectedClients.set(socket.id, { page: null, synced: false });
    
    socket.on('disconnect', () => {
        console.log('El corazón de un usuario se ha desconectado - ID:', socket.id);
        connectedClients.delete(socket.id);
        syncedClients.delete(socket.id);
        // Notificar a otros clientes que se perdió la sincronización
        socket.broadcast.emit('El otro corazón perdió conexión');
    });

    socket.on('win1update', (window1, sendid) => {
        console.log('Received win1update from ID:', socket.id, 'Data:', window1);
        if (isValidWindowData(window1)) {
            page1 = window1;
            connectedClients.set(socket.id, { page: 'page1', synced: false });
            socket.broadcast.emit('getdata', { data: page1, from: 'page1' });
            checkAndNotifySyncStatus();
        }
    });

    socket.on('win2update', (window2, sendid) => {
        console.log('Received win2update from ID:', socket.id, 'Data:', window2);
        if (isValidWindowData(window2)) {
            page2 = window2;
            connectedClients.set(socket.id, { page: 'page2', synced: false });
            socket.broadcast.emit('getdata', { data: page2, from: 'page2' });
            checkAndNotifySyncStatus();
        }
    });

    socket.on('requestSync', () => {
        const clientInfo = connectedClients.get(socket.id);
        if (clientInfo?.page === 'page1') {
            socket.emit('getdata', { data: page2, from: 'page2' });
        } else if (clientInfo?.page === 'page2') {
            socket.emit('getdata', { data: page1, from: 'page1' });
        }
    });

    socket.on('confirmSync', () => {
        syncedClients.add(socket.id);
        const clientInfo = connectedClients.get(socket.id);
        if (clientInfo) {
            connectedClients.set(socket.id, { ...clientInfo, synced: true });
        }
        checkAndNotifySyncStatus();
    });    
});

function isValidWindowData(data) {
    return data && 
           typeof data.x === 'number' && 
           typeof data.y === 'number' && 
           typeof data.width === 'number' && data.width > 0 &&
           typeof data.height === 'number' && data.height > 0;
}

function checkAndNotifySyncStatus() {
    const page1Clients = Array.from(connectedClients.entries()).filter(([id, info]) => info.page === 'page1');
    const page2Clients = Array.from(connectedClients.entries()).filter(([id, info]) => info.page === 'page2');
    
    const bothPagesConnected = page1Clients.length > 0 && page2Clients.length > 0;
    const allClientsSynced = Array.from(connectedClients.keys()).every(id => syncedClients.has(id));
    const hasMinimumClients = connectedClients.size >= 2;

    console.log(`Estado de depuración - Clientes conectados: ${connectedClients.size}, Page1: ${page1Clients.length}, Page2: ${page2Clients.length}, Synced: ${syncedClients.size}`);

    
    if (bothPagesConnected && allClientsSynced && hasMinimumClients) {
        io.emit('fullySynced', true);
        console.log('Todos los corazones están sincronizados');
    } else {
        io.emit('fullySynced', false);
        console.log(`Estado de sincronización: pages=${bothPagesConnected}, synced=${allClientsSynced}, clients=${connectedClients.size}`);
    }
}

server.listen(port, () => {
    console.log(`Servidor escuchando en http://localhost:${port}`);
});
```

Para los codigo base de page1/page2
+ Reemplace los circulos por corazones con efecto de palpitar y tamaño segun la distancia
+ Personalice los mensajes de estado: “Buscando latidos…”, “Esperando al otro corazón…”, “Entrelazando latidos…”, en color blanco
+ Añadi efectos visuales: particulas doradas (aura y connection), ondas expansivas al acercarse los corazones y fondo dinamico de gris a rojo    
En general la sincronizacion en tiempo real con socket.io se mantiene intacta; solo cambie la parte visual y estetica

Codigo de page1 (el de page2, es casi igual asi que lo omitire):
	
```jsx
let currentPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
}

let previousPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
};

let remotePageData = { x: 0, y: 0, width: 100, height: 100 };
let point1 = [currentPageData.width / 2, currentPageData.height / 2];
let socket;
let isConnected = false;
let hasRemoteData = false;
let isFullySynced = false;
let connectionTimeout;

//cadenas de efectos visuales
let particles = [];
let explosionParticles = [];
let shockwaves = [];   

//estado de la colision
let wasColliding = false;

function setup() {
    createCanvas(windowWidth, windowHeight);
    frameRate(60);
    socket = io();

    socket.on('connect', () => {
        console.log('Connected with ID:', socket.id);
        isConnected = true;
        socket.emit('win1update', currentPageData, socket.id);
        
        setTimeout(() => {
            socket.emit('requestSync');
        }, 500);
    });

    socket.on('getdata', (response) => {
        if (response && response.data && isValidRemoteData(response.data)) {
            remotePageData = response.data;
            hasRemoteData = true;
            console.log('Received valid remote data:', remotePageData);
            socket.emit('confirmSync');
        }
    });

    socket.on('fullySynced', (synced) => {
        isFullySynced = synced;
        console.log('Sync status:', synced ? 'SYNCED' : 'NOT SYNCED');
    });

    socket.on('peerDisconnected', () => {
        hasRemoteData = false;
        isFullySynced = false;
        console.log('Peer disconnected, waiting for reconnection...');
    });

    socket.on('disconnect', () => {
        isConnected = false;
        hasRemoteData = false;
        isFullySynced = false;
        console.log('Disconnected from server');
    });
}

function isValidRemoteData(data) {
    return data && 
           typeof data.x === 'number' && 
           typeof data.y === 'number' && 
           typeof data.width === 'number' && data.width > 0 &&
           typeof data.height === 'number' && data.height > 0;
}

function checkWindowPosition() {
    currentPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
        currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height) {

        point1 = [currentPageData.width / 2, currentPageData.height / 2]
        socket.emit('win1update', currentPageData, socket.id);
        previousPageData = currentPageData;
    }
}
//funcion para q los objetos sean corazones
function drawHeart(x, y, size, col) {
    push();
    translate(x, y - size/3);
    fill(col);
    noStroke();
    beginShape();
    vertex(0, size / 4);
    bezierVertex(size / 2, -size / 2, size, size / 3, 0, size);
    bezierVertex(-size, size / 3, -size / 2, -size / 2, 0, size / 4);
    endShape(CLOSE);
    pop();
}

//particulas
function spawnParticles(x, y, type = "aura", targetX = 0, targetY = 0) {
    if (type === "aura") {
        for (let i = 0; i < 2; i++) {
            let angle = random(TWO_PI);
            let r = random(40, 80);
            particles.push({
                x: x + cos(angle) * r,
                y: y + sin(angle) * r,
                size: random(2, 5),
                life: 200
            });
        }
    } else if (type === "connection") {
        for (let i = 0; i < 3; i++) {
            let t = random();
            let px = lerp(x, targetX, t) + random(-10, 10);
            let py = lerp(y, targetY, t) + random(-10, 10);
            particles.push({ x: px, y: py, size: random(2, 5), life: 200 });
        }
    }
}

function triggerShockwave(x, y) {
    shockwaves.push({ x, y, r: 0, alpha: 255 });
}

function handleParticles() {
    // aura + conexión
    for (let i = particles.length - 1; i >= 0; i--) {
        let p = particles[i];
        fill(255, 220, 100, p.life);
        noStroke();
        ellipse(p.x, p.y, p.size);
        p.life -= 3;
        if (p.life <= 0) particles.splice(i, 1);
    }

    // explosiones
    for (let i = explosionParticles.length - 1; i >= 0; i--) {
        let p = explosionParticles[i];
        fill(red(p.col), green(p.col), blue(p.col), p.life);
        noStroke();
        ellipse(p.x, p.y, p.size);
        p.x += p.vx;
        p.y += p.vy;
        p.life -= 5;
        if (p.life <= 0) explosionParticles.splice(i, 1);
    }

    // ondas expansivas
    for (let i = shockwaves.length - 1; i >= 0; i--) {
        let s = shockwaves[i];
        noFill();
        stroke(255, 230, 120, s.alpha);
        strokeWeight(3);
        ellipse(s.x, s.y, s.r * 2);
        s.r += 6;
        s.alpha -= 6;
        if (s.alpha <= 0) shockwaves.splice(i, 1);
    }
}

function draw() {
    //mensajes de estado
    if (!isConnected) {
    showStatus('Buscando latidos…', color(255)); 
    return;
    }

    if (!hasRemoteData) {
        showStatus('Esperando al otro corazón…', color(255));
        return;
    }

    if (!isFullySynced) {
        showStatus('Entrelazando latidos…', color(255,));
        return;
    }

    checkWindowPosition();
    
     //calcular posicion del corazon remoto
    let remoteX = map(remotePageData.x + remotePageData.width / 2, currentPageData.x, currentPageData.x + currentPageData.width, 0, width);
    let remoteY = map(remotePageData.y + remotePageData.height / 2, currentPageData.y, currentPageData.y + currentPageData.height, 0, height);
    
    //distancia entre corazones
    let distBetween = dist(point1[0], point1[1], remoteX, remoteY);

    //fondo gris que se vuelve rojo
    let bgCol = lerpColor(color(80), color(200, 0, 0), map(distBetween, 800, 0, 0, 1, true));
    background(bgCol);

    //tamaño con efecto de palpitar
    let pulse = sin(frameCount * 0.15) * 6;
    let baseSize = map(distBetween, 800, 0, 50, 200, true);
    let currentSize = baseSize + pulse;

    //dibujar corazones
    drawHeart(point1[0], point1[1], currentSize, color(0));
    drawHeart(remoteX, remoteY, currentSize, color(255));

    // partículas aura + conexión con menos frecuencia
    if (frameCount % 2 === 0) {
        spawnParticles(point1[0], point1[1], "aura");
        spawnParticles(remoteX, remoteY, "aura");
    }
    if (frameCount % 4 === 0) {
        spawnParticles(point1[0], point1[1], "connection", remoteX, remoteY);
    }

    handleParticles();

    let colliding = distBetween < 50;

    //mientras esten colisionando, siguen generando ondas expansivas
    if (colliding) {
        if (frameCount % 15 === 0) {
            triggerShockwave((point1[0] + remoteX) / 2, (point1[1] + remoteY) / 2);
        }
    }

    wasColliding = colliding;
}


function showStatus(message, statusColor) {
    textSize(24);
    textAlign(CENTER, CENTER);
    noStroke();
    fill(0, 0, 0, 150);
    rectMode(CENTER);
    let textW = textWidth(message) + 40;
    let textH = 40;
    rect(width / 2, 1*height / 6, textW, textH, 10);
    fill(statusColor);
    text(message, width / 2, 1*height / 6);
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}

```
#### Capturas de la app 📸
<img width="1919" height="1009" alt="Captura de pantalla 2025-10-03 002616" src="https://github.com/user-attachments/assets/07e66ef4-fe3a-4aed-9ed8-0b995fd34a1d" />
<img width="1516" height="885" alt="Captura de pantalla 2025-10-03 002659" src="https://github.com/user-attachments/assets/43fd36b9-65af-40d4-b8bd-69d849e70fbf" />
<img width="1156" height="922" alt="Captura de pantalla 2025-10-03 002726" src="https://github.com/user-attachments/assets/0bd7202f-5c91-4c2f-862a-58944342101f" />
Mensajes personalizados:
<img width="1102" height="530" alt="Captura de pantalla 2025-10-03 002756" src="https://github.com/user-attachments/assets/334511b1-ede9-45fd-82d7-0f626845d68a" />


#### Enlace al repositorio 🔗
El codigo completo de la aplicación se encuentra aqui:
https://github.com/VanDiosa/Unidad06-Actividad05.git



