
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
