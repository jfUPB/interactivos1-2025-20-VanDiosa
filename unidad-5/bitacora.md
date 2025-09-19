
# Evidencias de la unidad 5

## 🔎 Fase: Set

### 📚Actividad 01
⭐ Para tenerlo a la mano, [este es el codigo](https://editor.p5js.org/VanDiosa/sketches/NWrL9_nN1) del caso de estudio usado en esta actividad

❓Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?    
El microbit y p5 se comunican usando un puerto serial por USB. El microbit envia estos datos:
+ xValue: valor del acelerometro en el eje X
+ yValue: valor del acelerómetro en el eje Y
+ aState: si el boton A esta presionado (True o False)
+ bState: si el boton B esta presionado (True o False)

❓¿Cómo es la estructura del protocolo ASCII usado?    
El microbit envia los datos como texto en formato ASCII, separados por comas y terminados en salto de linea
```
data = "{},{},{},{}\n".format(xValue, yValue, aState,bState)
```
Ejemplo:
```
123,-456,True,False\n
```
❓Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.    
La parte del codigo en p5 encargada de leer y transformar las coordenadas esta en draw() y es:
``` js
if (port.availableBytes() > 0) {
      let data = port.readUntil("\n");
      if (data) {
        data = data.trim();
        let values = data.split(",");
        if (values.length == 4) {
          microBitX = int(values[0]) + windowWidth / 2;
          microBitY = int(values[1]) + windowHeight / 2;
          microBitAState = values[2].toLowerCase() === "true";
          microBitBState = values[3].toLowerCase() === "true";
          updateButtonStates(microBitAState, microBitBState);
        } else {
          print("No se están recibiendo 4 datos del micro:bit");
        }
      }
    }
```
+ port.readUntil("\n") -> es para leer por paquetes, teniendo en cuenta que cada paquete termina al encontrar un salto de linea
+ data.trim() -> limpia espacios en blanco o saltos de linea sobrantes
+ data.split(",") -> separa los valores recibidos por comas

Tenemos un arreglo para almacenar los datos enviados por el microbit:    
+ values[0] y values[1] -> convierte los valores de xValue, yValue en enteros, los centra en el canva y los almacena en la cadena
+ values[2] y values[3] -> convierte los textos en booleanos (true/false) q representan si los botones estan o no presionados

❓¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?     
Estos eventos suceden en la siguiente funcion:    
``` js
function updateButtonStates(newAState, newBState) {
  // Generar eventos de keypressed
  if (newAState === true && prevmicroBitAState === false) {
    // create a new random color and line length
    lineModuleSize = random(50, 160);
    // remember click position
    clickPosX = microBitX;
    clickPosY = microBitY;
    print("A pressed");
  }
  // Generar eventos de key released
  if (newBState === false && prevmicroBitBState === true) {
    c = color(random(255), random(255), random(255), random(80, 100));
    print("B released");
  }

  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}
```

En esta parte del codigo se compara el estado actual de cada boton con su estado anterior:

+ Para el boton A: el evento "A pressed" ocurre cuando newAState pasa de false a true. Eso significa que el microbit envio que ahora el boton esta presionado y p5 lo interpreta como un clic del mouse para generar una accion (cambiar el tamaño de las lineas y guardar la posicion)

+ Para el boton B: el evento "B released" ocurre cuando newBState pasa de true a false. Cuando el microbit avisa que el boton dejo de estar presionado. En ese momento p5 responde creando un nuevo color aleatorio para las lineas

Para ambos al final se actualizan las variables prevmicroBitAState y prevmicroBitBState para que en la siguiente lectura el sistema pueda detectar si hubo un cambio o no

❓Capturas de pantalla de algunos dibujos que hayas hecho con el sketch.
<img width="1538" height="965" alt="20250910_145237" src="https://github.com/user-attachments/assets/e80db79e-0689-41cd-83e7-a9655abd3108" />

<img width="1538" height="965" alt="20250910_153121" src="https://github.com/user-attachments/assets/5132d99c-d814-4e2e-85ef-aec8fc5dce7a" />

(Se guardo sin fondo pero no se pq :/)
<img width="1538" height="965" alt="20250910_153926" src="https://github.com/user-attachments/assets/0bb3317b-7d82-4571-b8ab-c8b31fbabbda" />


## 🔎 Fase: Seek
### 📚Actividad 02    
🧐🧪✍️Experimento 1: Mostrar datos como: Texto
<img width="1221" height="783" alt="Experimento1" src="https://github.com/user-attachments/assets/4eee7e8f-96bb-4e73-8879-16c489990926" />

❓¿Por qué se ve este resultado?    
R/ Porque ya no estamos usando ASCII si no formato binario para empaquetar los datos y el programa no logra como interpretar los datos que recibe en terminos de letras entonces usa simbolos y caracteres raros

🧐🧪✍️Experimento 2: Mostrar datos como: Todo en Hex
<img width="1215" height="805" alt="Experimento2" src="https://github.com/user-attachments/assets/70d32962-9057-4e11-be33-a46d435a775a" />

❓Lo que ves ¿Cómo está relacionado con esta línea de código?
```js
data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
```
No te parece que el resultado es un poco más difícil de leer que el texto en ASCII?  

R/ Ahora los simbolos confusos de antes son un poco mas claros. Se esta relacionado con la linea de codigo, ya que alli estamos usando el formado ">2h2B", en este formado se nos explico que cada dato de X y Y value envia 2 bytes cada uno, y los datos de los botones envia 1 byte cada uno, para un total de 6 bytes por paquete, lo cual se evidencia en la captura de pantalla

Por otro lado en cuanto a dificultad de leer comparandolo con ASCII, considero que si es mas dificil, ya que el ascii lo podiamos leer o interpretar con ayuda de una tablita pero el binario a pesar de enviar los datos de forma mas compacta no lo podemos interpretar con la misma facilidad si no que necesitamos como un programa adicional q nos lo traduzca

🧐🧪✍️ ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?

R/ En cuanto a ventajas: como lo mencione anteriormente el binario es mas corto, mas compacto, mas eficiente pq no estamos enviando unas cadenas largas de texto si no solo 6 bytes. Ademas como nos mencionan en la explicacion es mas rapido y estrategico usar este formato cuando se necesitan transmitir muchos datos

En cuanto a desventajas: la principal como lo mencione tambien anteriormente, es que no los podemos leer por nosotros mismo, necesitamos la ayuda de otro programa q los procese e interprete por nosotros

🧐🧪✍️Experimento 3: (Lo puse en HEX)    
<img width="1138" height="747" alt="Experimento3" src="https://github.com/user-attachments/assets/1659cba8-ca50-4a50-a316-13eb63a97c5d" />

¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?

R/  Se siguen enviando 6 bytes, la diferencia es q no se estan enviando constantemente si no solamente cuando se detecta q se sacude el microbit (shake). Se relaciona con el formaro ">2h2B" pq el numero de bytes sigue coincidiendo con los datos, para xValue, yValue: 2 bytes cada uno (4 bytes), aState y bState: 1 byte cada uno (+2 bytes, 6 en total)

🧐🧪✍️ Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?    
R/ Por cuenta propia no tenia ni idea de como se veia los numeros negativos. Pero luego de leer y buscar, encontre que se usa algo llamado "complemento a dos". En binario un numero entero CON signo (h) puede ir de -32768 a 32767, si es positivo se escribe tal cual en binario y si es negativo es donde se usa el complento a dos.

El complemento a dos, es agarrar los mismos bits del numero en positivo e invertirlos para que se entienda que tiene signo negativo. Visualmente al mostrar los datos en HEX se pueden reconocer los numeros negativos cuando empiezan por FF, FE, FD...

🧐🧪✍️ Experimento 4:   
¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario?

Captura:
<img width="1011" height="742" alt="Captura de pantalla 2025-09-17 140916" src="https://github.com/user-attachments/assets/5161f100-9be8-4154-bde2-0d8cf7f4504c" />

(Los datos en binario son los representados entre este tipo de corchete [ ], y por otro lado los datos como ASCII se ven luego de los anteriores en texto legible. Nos muestran los mismos valores representados en ambos formatos)

R/ Diferencias: En binario cada paquete ocupa solo 6 bytes siendo muy compacto y eficiente a comparacion de en ASCII que el tamaño de cada paquete depende de la cantidad de digitos

Binario:
+ Ventajas: compacto, rapido, y eficiente especialmente en situaciones donde se procesan muchos datos
+ Desventajas: dificil de leer directamente por nosotros, se necesita si o si un programa extra q lo interprete o traduzca

ASCII:
+ Ventajas: legible para los humanos sin necesidad de recurrir a otras herramientas. De verificiacion facil
+ Desvenajas: mas espacio ocupado y mas lento en procesos con volumentes altos de datos

### 📚Actividad 03
⭐ Para tenerlo a la mano, [este es el codigo](https://editor.p5js.org/VanDiosa/sketches/iD2vSmtOl) del caso de estudio modificado en esta actividad

🧐🧪✍️ Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.

R/ En la unidad anterior estabamos usando el formato ASCII y era necesario delimitar cada paquete usando \n pq cada mensaje variaba segun la cantidadad de digitos que tuviera cada numero. Por ejemplo uno de los numeros podria ser 19 y alli se ocuparian 2 bytes, o podria ser -1234 y alli se ocuparian 5 bytes. Al delimitar correctamente los paquetes p5 podia reconocer donde empezaban y terminaban para separar los datos en sus respectivos paquetes

Ahora no es necesario pq estamos usando el formato binario donde cada paquete tiene un tamaño fijo de 6 bytes, 2 para xvalue, 2 para yvalue, y 1 para cada boton (aState y bState). Al ser tamaño fijo ya no es necesario usar limitadores pq p5 simplemente sabe que cada 6 bytes es un paquete completo

🧐🧪✍️ Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?

R/ En la unidad anterior, el codigo recibia datos en formato de texto o ASCII. Se usaba el port.readUntil("\n").split(",") para leer hasta encontrar un salto de linea y luego separar esos datos con comas. Despues esos datos eran convertidos a numeros o valores booleanos
```js
let values = port.readUntil("\n").split(",");
microBitX = int(values[0]) + windowWidth / 2;
microBitY = int(values[1]) + windowHeight / 2;
microBitAState = values[2].toLowerCase() === "true";
microBitBState = values[3].toLowerCase() === "true";
```

En esta unidad, el codigo directamente lee bytes usando port.readBytes(6). Esos bytes los interpreta y convierte en un arreglo/array usando DataView
```js
let data = port.readBytes(6);
const buffer = new Uint8Array(data).buffer;
const view = new DataView(buffer);

microBitX = view.getInt16(0); // getInt16 -> numeor entero con signo
microBitY = view.getInt16(2);
microBitAState = view.getUint8(4) === 1; // getUint8 -> numero entero sin signo
microBitBState = view.getUint8(5) === 1;
```

🧐🧪✍️ REPRODUCIENDO UN ERROR: ¿Qué ves en la consola? ¿Por qué crees que se produce este error?

R/ Al inicio se observan datos como correctos y logicos, pero luego empiezan a aparecer valores raros. Lo q creo es que hay un error en la lectura, una desincronizacion, que se mezclan bytes, ya que los datos se estan entregando continuamente

🧐🧪✍️ IMPLEMENTANDO EL FRAMING: Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves?

R/ El framing sirve para asegurar que p5 identifique el inicio y el fin de cada paquete, y que los datos no se desordenen. Al ejecutar el codigo la consola muestra datos claros y logicas    
Tambien se vi mensajes de estado como “Microbit ready to draw”. Si ocurre un error en la transmision aparece “Checksum error in packet” y el paquete se descarta

🧐🧪✍️ VERSIONES FINALES DE LOS PROGRAMAS: ¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js?

R/ En las versiones finales, por el lado del codigo del micro bit, añadimos dos bytes extras en cada paquete: un header para marcar el inicio y un checksum para validar q los datos son correctos. Asi q en lugar de 6 bytes por paquete ahora tenemos 8

Por otro lado en p5, se añadio un buffer, con este buscamos el header para alinear los datos y ademas se usa para calcular el checksum para descartar paquetes

El checksum es el residuo de la operacion modulo (la division) de: la suma de los datos del paquete (los 6 bytes) entre 256. Este valor debe de dar un numero entre 0 y 255

## 🔎 Fase: Apply

### 📚Actividad 04

## 🔎 Fase: Reflect

### 📚Actividad 05

## 📝 Rubrica - Autoevaluacion




