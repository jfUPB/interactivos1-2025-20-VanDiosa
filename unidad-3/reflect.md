# Unidad 3


## 🤔 Fase: Reflect

### 📚 Actividad 08 - Autoevaluación   
💡Parte 1: recuperación de conocimiento (Retrieval Practice)    
❓ 1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?

Es un modelo de programacion que divide el codigo en:   
+ Estados (CONFIG, ARMED, EXPLODED)
+ Eventos (Presionar A, B, sacudir el microbit o presionar S, tocar el touch del microbit o presionar R)
+ Acciones (Actualizar el display, pasar entre estados, guardar la contraseña,pasar de estado)
+ Transiciones (el cambio de un estado a otro segun el evento que ocurra)    

Para que no se este ejecutando todo de una si no que se va cambiando entre estados de forma organizada segun las condiciones que se vayan presentando

❓ 2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender varios eventos y tareas “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?

El usar sleep hace que el programa se quede dormido (BLOQUEA EL FLUJO) esperando cierto tiempo, en cambio la maquina de estados esta constantemente revisando el estado en que esta y cual es el siguiente paso a ejecutar SIN DETENER EL FLUJO. Si se usara el sleep el codigo no podria manejar varios eventos de forma eficiente a comparacion de la maquina de estados que trabaja eventos en paralelo

❓3. Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial (por ejemplo, una combinación de botones o un comando serial) mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?

En el estado ARMED se tendria que añadir un nuevo evento especial, la transicion seria entre ese evento y la accion de modificar el temporizador para que el tiempo restante reduzca a la mitad. Todo eso sin salir del estado ARMED

❓ 4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.

Un vector de prueba es una lista o tabla que se crea para revisar que el programa este funcionando bien, se divide en los estados del programa y se escriben los eventos que ocurren y las acciones que se esperan obtener por cada uno de los estados

Es crucial pq podemos detectar errores y verificar que la maquina de estados tenga la logica completa

💡Parte 2: reflexión sobre tu proceso (Metacognición)    
❓1. ¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?   

En esta unidad me resulto demasiado desafiante tanto el diagrama como el codigo. En el caso del diagrama, no sabia si dividir los eventos en rectangulos separados o escribirlos todos juntos, siento que me quedo mucho texto en el diagrama y que probablemente escribi cosas que alli no iban. En el caso del codigo, por un lado en cursos anteriores no habia usado nunca javascript por lo que debo de recurrir a google, internet, las propias librerias de P5, o chat GPT para ir comprendiendo para que sirven ciertas lineas de codigo, de igual forma falte la clase en la que explicaron la aplicación de conexión serial la cual creo era de mucha utilidad para la realizacion de la actividad 07, siento que no usar esa aplicacion me complico y enrredo mucho

❓2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?

En la actividad 07, luego de agregar al codigo las lineas para manejar la bomba tanto con el microbit como con el teclado me salio un error, que tengo la sospecha sucede por no usar la aplicación de conexión serial. El error era "p5.WebSerial is not a constructor". El error no estaba en la lógica de los estados ni en los eventos, sino en cómo estaba cargando la librería de conexión serial

❓3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?

Si empece con una version simple. Primero implemente la logica de los estados principales (CONFIG, ARMED, EXPLODED) para ver que funcionara el cambio entre ellos    
Luego el control desde el teclado, para bajar o subir el temporizador en CONFIG, para pasar del estado CONFIG a ARMED, para desactivar la bomba mientras esta en el estado ARMED, y para reiniciar la bomba al esta estar en EXPLODED
Luego el contror con el microbit que fue lo mas complicado para mi

❓4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?

En la unidad anterior mencione juegos de interaccion rapida como Simon dice o Bop It, donde hay que reaccionar a estimulos especificos y cada accion del jugador cambia el estado del juego. Ahora pienso que tambien seria util en videojuegos narrativos con decisiones donde cada eleccion lleva al jugador a un estado distinto de la historia

### 📚 Actividad 09 - Feedback   
❓1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?

Me gusto que siguieramos usando los codigos de la unidad anterior. Tambien me gusto mucho cuando nos muestran la estructura del codigo hacia la que debemos llegar, ya que sirve como guia

❓2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso? ¿Qué cambiarías o eliminarías?

En esta unidad en especifico lo que mas confuso me parecio fue como hacer que el p5 se manejara tanto por teclado como por el microbit. Ademas de que sigo sin entender completamente la manera adecuada de hacer los graficos de las maquinas de estado, siento que el de esta unidad lo sature demasiado 

❓3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?

Me habria ayudado tener una seccion de puros graficos de maquinas de estado, ademas de un ejercicio mas explicito para el manejo del p5 desde microbit

❓4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa a diseñar y programar uno complejo? ¿Por qué?

En mi caso personal senti esta unidad como un 4, el pasar de diseñar a programar no es complejo lo que es complejo es conocer funciones y sintaxis que me pueda ser util en cada caso en particular

❓5. Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?    

Mi mayor frustracion fue el bug de "p5.WebSerial is not a constructor" ya que por mas q repetia y borraba lo de la libreria que se debia de añadir, seguia apareciendo... al final ni supe como quite ese error. Y el momento aha fue ver como los cambios al codigo de microbit a p5 fueron poquitos pq se escribia casi que igual

