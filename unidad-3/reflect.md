# Unidad 3


## 🤔 Fase: Reflect

### 📚 Actividad 06 - Autoevaluación   
💡Parte 1: recuperación de conocimiento (Retrieval Practice)    
❓ 1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?

Es un modelo de programacion que divide el codigo en:   
+ Estados (CONFIG, ARMED, EXPLODED)
+ Eventos (Presionar A, B, sacudir el microbit o presionar S, tocar el touch del microbit o presionar R)
+ Acciones (Actualizar el display, pasar entre estados, guardar la contraseña,etc)
+ Transiciones    

Para que no se este ejecutando todo de una si no que se va cambiando entre estados segun las condiciones que se vayan presentando

❓ 2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender varios eventos y tareas “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?

El usar sleep hace que el programa se quede dormido esperando cierto tiempo, en cambio la maquina de estados esta constantemente revisando el estado en que esta y cual es el siguiente paso a ejecutar. Si se usara el sleep el codigo no podria manejar varios eventos de forma eficiente

❓3. Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial (por ejemplo, una combinación de botones o un comando serial) mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?

❓ 4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.

Un vector de prueba es una lista o tabla que se crea para revisar que el programa este funcionando bien, se divide el codigo estados y se escriben los eventos que se deben hacer y las acciones que se esperan obtener

💡Parte 2: reflexión sobre tu proceso (Metacognición)    
❓1. ¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?   

En esta unidad me resulto demasiado desafiante tanto el diagrama como el codigo. En el caso del diagrama, no sabia si dividir los eventos en rectangulos separados o escribirlos todos juntos, siento que me quedo mucho texto en el diagrama y que probablemente escribi cosas que alli no iban. En el caso del codigo, por un lado en cursos anteriores no habia usado nunca javascript por lo que debo de recurrir a google, internet, las propias librerias de P5, o chat GPT para ir comprendiendo para que sirven ciertas lineas de codigo, de igual forma falte la clase en la que explicaron la aplicación de conexión serial la cual creo era de mucha utilidad para la realizacion de la actividad 07, siento que no usar esa aplicacion me complico y enrredo mucho

❓2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?

En la actividad 07, luego de agregar al codigo las lineas para manejar la bomba tanto con el microbit como con el teclado me salio un error, que tengo la sospecha sucede por no usar la aplicación de conexión serial. El error era "p5.WebSerial is not a constructor"

❓3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?



❓4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?

En la unidad anterior mencione el juego simon dice y bob it, sigo opinando que esos dos son un buen ejemplo del como se puede aplicar, o sea, en juegos o interacciones de ese tipo donde se debe reaccionar 
