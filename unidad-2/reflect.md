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

❓3. Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?

❓4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.    

Es como un lista de pruebas que se hace para asegurarse de que el programa este funcionando bien. Sirve para revissar los estados, eventos y encontrar posibles errores. Uno de los vectores seria por ejemplo, si presiono el boton A mientras estoy configurando el temporizador, entonces el tiempo debe subir en uno

💡Parte 2: reflexión sobre tu proceso (Metacognición)    
❓1. ¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?

❓2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?

❓3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?

❓4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?

### 📚 Actividad 08 - Coevaluación

### 📚 Actividad 09 - Feedback   
❓1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?

❓2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso, innecesariamente complicado o que aportó poco a tu aprendizaje? ¿Qué cambiarías o eliminarías?

❓3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?

❓4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa (Actividad 03) al diseño desde cero de uno complejo (Actividad 04 y 05)? ¿Por qué?

❓5. Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?
