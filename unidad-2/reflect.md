# Unidad 2


## 🤔 Fase: Reflect

### 📚 Actividad 06 - Autoevaluación    
💡Parte 1: recuperación de conocimiento (Retrieval Practice)    
❓1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?    

Una maquina de estados es una forma de programar donde se divide el codigo en diferentes estados para no hacer todo de una, si no, que se va cambiando entre ellos segun lo q pase. Los componentes fundamentales son:
+ Estados
+ Eventos
+ Acciones
+ Transiciones

❓2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?

Porque con la maquina de estados el programa va revisando rapido en que estado este y que debe hacer, sin quedarse dormido esperando. Asi puede ir atendiendo el temporizador, los botones y otros eventos casi al mismo tiempo. Si usaramos sleep() el microbit se quedaria parado y no podria reaccionar a otras cosas hasta que pase cierto tiempo

❓3. Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?

En el estado ARMADO añadiria un nuevo evento "accelerometer.was_gesture(shake)" que en vez de cambiar de estado, haga la accion de dividir el tiempo que queda entre 2

❓4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.    

Es como un lista de pruebas que se hace para asegurarse de que el programa este funcionando bien. Sirve para revissar los estados, eventos y encontrar posibles errores. Uno de los vectores seria por ejemplo, si presiono el boton A mientras estoy configurando el temporizador, entonces el tiempo debe subir en uno

💡Parte 2: reflexión sobre tu proceso (Metacognición)    
❓1. ¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?

Lo mas difícil para mi fue realizar el diagrama, ya que en otros cursos habia trabajado con diagramas de flujo y de clases pero no con este tipo, por lo que me tomo mas tiempo entenderlo y hacerlo

❓2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?

El problema principal que tuve estuvo en la condicion del if dentro del estado STATE_ARMED. La logica hacia que el contador llegara a valores negativos o por alguna razon contaba de dos en dos o explotaba en 3. Pensar en estados, eventos y transiciones me ayudo a ver cuando debia ocurrir la transicion a STATE_EXPLODED (justo despues de mostrar 0), corregi la condicion del if y empezo a comportarse como esperaba

❓3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?

Empece con algo simple, solo el estado de configuracion y que mostrara el tiempo. Luego agregue la parte de armarla con shake y despues la cuenta regresiva (por prueba use 5 y no 20). Por ultimo sume la explosion y el reinicio. Asi era mas facil probar cada parte y no tener errores en todo a la vez

❓4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?

Creo que se podria aplicar en un juego tipo Bop It (parecido a Simon dice), donde el jugador debe reaccionar rapidamente a diferentes ordenes que cambian segun el estado del juego. Tambien en un videojuego con enemigos que patrullan y dependiendo de lo que ocurra cambian su comportamiento para atacar, perseguir o retirarse. La maquina de estados ayudaria a organizar y controlar de forma clara las transiciones y acciones segun lo que pase en cada momento

### 📚 Actividad 09 - Feedback   
❓1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?

❓2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso, innecesariamente complicado o que aportó poco a tu aprendizaje? ¿Qué cambiarías o eliminarías?

❓3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?

❓4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa (Actividad 03) al diseño desde cero de uno complejo (Actividad 04 y 05)? ¿Por qué?

❓5. Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?


