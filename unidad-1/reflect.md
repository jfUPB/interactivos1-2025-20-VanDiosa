# Unidad 1

## 🤔 Fase: Reflect

### 📚 Actividad 07 - Autoevaluación
💡Parte 1: recuperación de conocimiento (Retrieval Practice)   

❓1. Basándote en los ejemplos que vimos de sistemas físicos interactivos al iniciar el curso, describe las tres características que definen a un sistema físico interactivo.
Un sistema fisico interactivo es combinar elementos fisicos con un software. Las tres caracteristicas son:
+ Un imput fisico, por ejemplo sensores, camaras u otros que registran temperatura, movimiento, sonido, luz, etc
+ Un procesamiento que es realizado por un software programado que actuara o dara una devolucion dependiendo de la información que reciba
+ Un output fisico como sonidos, luces, imagenes
    
❓2. Explica el modelo input-process-output de Patrick Hübner usando como ejemplo el sistema que construiste con micro:bit y p5.js en la Actividad 06. ¿Cuál fue el input, cuál fue el proceso y cuál fue el output?

Para el micro bit:
+ Input: boton A y B
+ Procesamiento: leer cual es el boton que se esta presionando
+ Output: envia la informacion correspondiente por el serial, o sea A o B

Para el PC:
+ Input: boton de conexion al microbit, informacion recibida en el serial
+ Procesamiento: lee la informacion recibida y decide como se mueve el circulo
+ Output: el circulo cambia su posicion en x dependiendo de la informacion leida
    
❓3. ¿Cuál es la función de la línea uart.write('A') en el código del micro:bit y qué función en p5.js se encarga de “escuchar” ese mensaje?   
Despues de revisar si algo esta presionado la funcion uart.write('A') es la que envia informacion por el serial al pc. En cuando a la funcion que escucha en el p5, no me la se de memoria
    
❓4. ¿Cuál es la diferencia fundamental entre el arte/diseño tradicional y el arte/diseño generativo?   
En el tradicional todo lo crea directamente el artista/diseñardor y toma las deciciones manualmente.
En el generativo el artista/diseñador crea un sistema y lo alimenta con reglas, normas, etc, para que luego este sistema cree multiples resultados variables dependiendo del codigo, del azar, del entorno, etc.
    
❓5. Imagina que quieres que un círculo en p5.js cambie a un color aleatorio cada vez que sacudes el micro:bit. Describe qué tendrías que programar en el micro:bit y qué tendrías que programar en p5.js para lograrlo.   
+ En el microbit se tendria que programar con un is. o was. si el acelerometro esta activo por decirlo asi y enviar esa informacion usando el uart.write al p5.js   
+ En el p5 se tendria que programar el setup inicial. Y como en la actividad anterior crear una variable global para el relleno del circulo. Y en la funcion que lea la informacion enviada por el uart se actualizaria la varibale global con un nuevo color aleatorio

💡Parte 2: reflexión sobre tu proceso (Metacognición)   
❓1. ¿Qué fue más desafiante para ti en esta unidad: la parte conceptual (entender qué es un sistema físico interactivo) o la parte técnica (hacer que el micro:bit y p5.js se comunicaran)? ¿Por qué?   
En mi caso personal se me hace mas dificil la parte tecnica, ya que la programacion siempre ha sido como un reto para mi, y me cuesta un poco comprender el codigo, o para que sirven ciertas partes en especifico o como puedo hacer que algo ocurra 
   
❓2. Describe el momento “¡Aha!” que tuviste cuando lograste que una acción en el micro:bit (presionar un botón, sacudirlo) tuviera un efecto visible en el canvas de p5.js por primera vez. ¿Qué fue lo que entendiste en ese instante?   
Cuando use de referencia la actividad 5 para hacer la actividad 6 y logre que el circulo se moviera pude terminar de comprender algunas lineas del codigo que tal vez aun no habia terminado de entender
   
❓3. Al inicio de la unidad te pregunté: “¿Este curso para qué me sirve?”. Después de experimentar y construir tu primer prototipo, ¿Cómo ha cambiado o se ha vuelto más concreta tu respuesta a esa pregunta?   
No se me habia ocurrido para que me podria servir, pero luego de ver los videos de los sitemas fisicos de ejemplo, pude ver que es un curso muy util para el momento en que quiera conectar lo fisico con lo digital, ampliar la experiencia y que sea tal vez algo mas sensorial
   
❓4. El tutorial de la Actividad 05 te llevó paso a paso. ¿Cómo te sentiste con ese método de aprendizaje? ¿Te dio seguridad o preferirías haberlo intentado por tu cuenta desde el principio?   
Me gusto ese metodo porque fue una gran referencia para el desarrollo de la actividad 6, y me permitio entender bien cada linea a medida que el profe nos iba explicando

### 📚 Actividad 08 - Coevaluación


### 📚 Actividad 09 - Feedback

