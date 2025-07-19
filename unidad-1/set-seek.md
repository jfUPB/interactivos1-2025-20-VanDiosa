# Unidad 1

## 🔎 Fase: Set + Seek

### 📚 Actividad 01 - ¿Qué es un sistema físico interactivo?
❓¿Qué es un sistema físico interactivo?   
Si junto la explicación de clase con la lista de videos, lo que entendi es que un sistema fisico interactivo es combinar lo fisico como sensores, luces, camaras, etc. con un software programado para actuar dependiendo de la informacion que recibe. O sea, es un sistema que responde a lo que el usuario haga con imagenes, sonidos, movimientos

❓¿Cómo podrías aplicar lo que has visto en tu perfil profesional?   
Siento que en mi perfil profesional podria usar este sistema para crear experiencias llamativas e inmersivas. Por ejemplo,   
+ Controlar videojuegos con gestos o figuras tipo amiibos
+ Realizar experiencias interactivas como las que se pueden ver en el parque explora o lugares parecidos donde los visitantes tocan, mueven o hablan y el sistema tiene diferentes reacciones
+ Hace años vi una maqueta de una ciudad donde dependiendo de los elementos que se le colocara se reproducian animaciones de desastres naturales encima de ella tipo video mapping, pienso que eso tambien es una forma de juntar la carrera con este tipo de sistema de una forma mas educativa

### 📚 Actividad 02 - ¿Qué es el diseño y el arte generativos?
❓¿Qué es el diseño/arte generativo?   
Es un enfoque de diseño donde en vez de hacer todo a mano, uno crea un sistema que a partir de reglas, condiciones o datos que se le suministran genera multiples resultados de la idea o mensaje que quieres dar. Este metodo no se trata de dejar todo al azar si no de darle una estructura del proceso a la tecnologia. Los diseñadores pasan a colaborar con el sistema, lo que les permite generar diseños que se adaptan a diversas situaciones

Tiene el mismo flujo del sistema fisico interactivo, una entrada, un proceso y una salida

❓¿Cómo podrías aplicar lo que has visto en tu perfil profesional?   
Lo primero que se me ocurre es que se puede aplicar este enfoque en la creacion de personajes con variaciones en colores y formas de una manera mas eficiente. Tambien podria ser una forma interesante para explorar estilos visuales cambiando ciertos parametros o datos lo que creo seria muy util para proyectos con muchos assets. Se puede usar para generar escenarios o niveles, ajustando como el numero de obstaculos y la distribucion de estos. Creo que colaborar con el sistema de esta forma es mas responsable y consciente que simplemente dejarle todo el trabajo

### 📚 Actividad 03 - Herramientas y tecnologías
💡Luego de hacer el ejercicio, responde la siguiente pregunta: En este sistemas físico interactivo identifica los inputs, outputs y el proceso.   
Para el MICRO BIT
+ Inputs:
  + Boton a y b
  + Sensor de acelerometro al sacudir
  + Los datos y la energia recibida por el puerto USB desde el PC 
+ Outputs:
  + Datos enviados al computador por USB (letras a, b o sacudida)
  + Imagenes en el display (mariposa, corazon, flechitas, reloj, caras de emociones, vaquita, fantasma, entre muchos mas)
+ Proceso: El micro bit al detectar los inputs interpreta el tipo de interaccion y segun el caso envia la informacion por el puerto USB
  
Para el PC
+ Inputs:
  + El serial (datos, informacion) que se recibe a traves de la USB (boton presionado a o b, sacudida)
  + El boton Send Love
+ Outputs:
  + Cambio de color del circulo en pantalla segun los datos recibidos (rojo para boton a, amarillo para boton b o verde para sacudida)
+ Proceso: En caso del primer input el programa procesa esa entra y actualiza el color del circulito dependiendo de los datos seriales. Por otro lado, cuando se usa el boton Send Love el programa envia un serial al micro bit para activar la animacion de corazon y luego carita feliz

### 📚 Actividad 04 - Generando patrones visuales
[🌟 Ver mi programa en p5.js](https://editor.p5js.org/VanDiosa/sketches/AqXjMu_mZ)

```javascript
let circles = []; // un arreglo donde se guardan los circulos que se van generando

function setup() { //funcion inicial que se ejecuta solo una vez
  createCanvas(600, 600);
  noStroke(); //circulos sin borde
  background(20); //color del fondo al ser solo un numero se interpreta como gris
}

function draw() {
  background(20, 20, 20, 25); // gris con transparencia para el efecto de rastro (R,G,B,A)

  for (let c of circles) { // aqui se dice como "por cada"
    let size = sin(frameCount * 0.05 + c.phase) * 20 + 40; //se usa la funcion seno para que el tamaño varie en cada fotograma. 0.05 es la velocidad de efecto. C.phase es para dar ritmos diferentes a cada uno. el *20 + 40 es como el rango de tamaño
    c.x += sin(frameCount * 0.05 + c.phase) * 0.5; // el 0,5 es la distancia del movimiento
    c.y += cos(frameCount * 0.05 + c.phase) * 0.5;
    fill(c.color);
    ellipse(c.x, c.y, size, size);
  }
}

function mousePressed() {
  let newCircle = {
    x: random(width), 
    y: random(height), //coordenadas random para x y y
    phase: random(TWO_PI), //ritmo de oscilacion aleatorio
    color: color(random(100, 255), random(100, 255), random(100, 255), 200) // (R,G,B,A)
  };
  circles.push(newCircle); //se añade al arreglo

  if (circles.length > 70) {
    circles.shift(); // para no saturar se coloca un limite de circulos
  }
}
```
