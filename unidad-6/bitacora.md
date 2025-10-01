
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
- Inicia el servidor y abre page1 y page2. ✔️

- Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves? ✔️

<img width="878" height="255" alt="Captura de pantalla 2025-10-01 143905" src="https://github.com/user-attachments/assets/cdeef18d-c347-40e0-b34c-977c6e8de7ce" />

R/ En la terminal aparece el evento `Received win1update`con los datos de la posición y tamaño de la ventana . Ejemplo:  `{ x: -6, y: 306, width: 610, height: 244 }`

- Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves? ✔️

<img width="896" height="254" alt="Captura de pantalla 2025-10-01 143936" src="https://github.com/user-attachments/assets/80c91c99-065c-4307-8aa0-63bac3183ac7" />

R/ En la terminal aparece el evento `Received win2update`con los datos de la posición y tamaño de la ventana . Ejemplo:  `{ x: 368, y: 0, width: 904, height: 156 }`

CONCLUSION DEL EXPERIMENTO 3 HASTA AQUI: Cada pagina tiene su propio evento de actualizacion y el servidor puede distinguir de quien vienen los datos

- Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.

Codigo antes:

<img width="1017" height="548" alt="Captura de pantalla 2025-10-01 145342" src="https://github.com/user-attachments/assets/abb433b5-34c9-4df7-be93-52e119d4edc1" />


Codigo despues:

<img width="1018" height="547" alt="Captura de pantalla 2025-10-01 145356" src="https://github.com/user-attachments/assets/a9ae0344-70fa-4176-ae27-ac0d6a80ae1b" />


R/  Cuando movi page 1 el servidor recibio el evento y lo registro en la consola (se ve win1update…), PERO esos movimientos no se ven reflejados en page 2, la informacion no le esta llegando a ese cliente. Con `socket.emit(...)` solo el cliente que mando el evento recibe su propia info, asi que no hay sincronizacien entre las paginas; en cambio con `socket.broadcast.emit(...)` page1 y page2 se sincronizan porque cada vez que uno manda datos, el servidor los envia a los demas clientes

#### 🧐🧪✍️ Experimento 4  
