
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
+ Similitudes: 
+ Diferencias: 
+ El por que de la complejidad de HTTP:

🧐✍️HTML, CSS y JavaScript    
Piensa en una página web simple, como un formulario de login.
+ ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?
+ ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?
+ ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?

R/

🧐✍️¿Cómo se ejecuta JavaScript?    
Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.
+ ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?
+ ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?

R/

🧐✍️¿Qué es Node.js?    
¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?

R/

🧐✍️WebSockets y Socket.IO    
Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?

R/

### 📚Actividad 03    
