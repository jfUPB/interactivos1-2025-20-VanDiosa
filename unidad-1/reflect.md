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
El compañero con el que intercambie fue Tomas y este es el link de [su repositorio](https://github.com/jfUPB/interactivos1-2025-20-Tomasm12/blob/unidad1/apply/unidad-1/apply.md)

Las diferencias entre soluciones son:
+ El compañero creo 2 variables globales para el movimiento del circulo tanto en x como en y. En mi caso solo hice una variable global para el movimiento en x
+ Otra diferencia meramente estetica es el diametro de los circulos, el de el es de 100 y el mio de 50
+ En el caso del compañero uso un sleep en cada condicion del codigo del micro bit, pero yo solo use uno. Creo que por ese lado lo de el fue mas eficiente en terminos de no enviar muchos datos seguidos
+ El tambien uso un ellipseMode(CENTER), yo no lo use y tampoco lo tuve como presente pero creo que es un recurso bueno para tener un mejor contro en el movimiento

Para proximas actividades tendre presente el uso del sleep para tener codigos menos cargados de informacion

### 📚 Actividad 09 - Feedback   
❓1. Continuar: ¿Qué actividad, video o ejemplo de esta unidad te resultó más inspirador o te ayudó más a entender el potencial de los sistemas físicos interactivos?   
La verdad en cuanto a entender el potencial diria que los videos ya que eran proyectos grandes y avanzados entonces pude ver como la magnitud a la que se puede llegar con estos sistemas. Pero de igual forma el codigo del ejemplo de la actvidad 5 me ayudo mucho

❓2. Dejar de hacer: ¿Hubo alguna parte que te pareció demasiado abstracta, muy rápida o confusa? ¿Hay algo que crees que podríamos cambiar para que sea más claro?   
Al principio pense que el tiempo no me iba a dar para realizar las actividades, pero en realidad fue el tiempo justo. Por lo cual en este momento no se me ocurre nada para cambiar

❓3. Empezar a hacer: ¿Qué te genera más curiosidad ahora? ¿Te gustaría explorar más sensores del micro:bit (luz, temperatura), crear visualizaciones más complejas en p5.js o ver más ejemplos de proyectos artísticos?   
Me gustaria explorar mas ejemplos de proyectos artisticos ya que todo lo relacionado con el arte es lo q mas me llama la atencion, no me importa si son ejemplos sencillos, puesto que puedo ir aprendiendo de a poco

❓4. Balance inspiración vs. técnica: ¿Cómo sentiste el equilibrio entre ver los videos inspiradores de la Actividad 01 y la parte técnica de conectar las herramientas en las actividades 03-06?   
Siento que hubo un buen equilibrio, los videos nos ayudan a imaginar las posibilidades de proximas actividades. Las parte tecnica mostrada paso a paso fue de mucha ayuda para no sentirme tan perdida.

❓5. Comentario adicional: ¿Hay algo más que quieras compartir sobre tu experiencia en esta unidad introductoria?
Mi experiencia fue comoda, pense que la conexion con el microbit seria mas compleja, pero las actividades, explicaciones, y consultas individuales, fueron muy utiles para aprender
