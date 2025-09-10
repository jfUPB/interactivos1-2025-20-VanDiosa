
# Evidencias de la unidad 5

## 🔎 Fase: Set

### 📚Actividad 01
❓Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?    
El microbit y p5 se comunican usando un puerto serial por USB. El microbit envia estos datos:
+ xValue: valor del acelerometro en el eje X
+ yValue: valor del acelerómetro en el eje Y
+ aState: si el boton A esta presionado (True o False)
+ bState: si el boton B esta presionado (True o False)

❓¿Cómo es la estructura del protocolo ASCII usado?    
El microbit envia los datos como texto en formato ASCII, separados por comas y terminados en salto de linea:
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
  }
```
+ port.readUntil("\n") -> es para por paquetes, teniendo en cuenta que cada paquete termina al encontrar un salto de linea
+ data.split(",") -> separa los valores recibidos por comas

Tenemos un arreglo para almacenar los datos enviados por el microbit:    
+ values[0] y values[1] -> son enteros y pasan de ser xValue, yValue a ser microBitX, microBitY estos dos se estan dividiendo por 2 para que queden centrados en el canva
+ values[2] y values[3] -> son convertidos en booleanos (true/false) y representan si los botones estan o no presionados

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
### 📚Actividad 03
