# Unidad 2

## 🔎 Fase: Set + Seek

### 📚 Actividad 01 - Analizando un programa con una máquina de estados simple
❓Describe detalladamente cómo funciona este ejemplo.    
 Se define una clase Pixel que utiliza estados simples para encender y apagar el pixel en funcion del tiempo.
 Se crea un objeto tipo Pixel y se le asignan los valores iniciales (coordenadas, estado inicial, intervalo de tiempo)
 En el metodo update se esta revisando constantemente el estado actual de cada pixel y se ejecutan las acciones que correspondan:
 + Si el estado es Init el pixel se enciende por primera vez, se guarda el tiempo actual y se cambia al estado waitTimeout
 + Si el estado ya es WaitTimeout si ya paso el tiempo de intervalo definido, en caso de que si, se cambia el brillo del pixel (0 a 9, 9 a 0), actualiza el tiempo y se queda esperando

❓¿Cuáles son los estados en el programa?    
Hay un estado de guarda -> self.state : es una variable que almacena información de la condición actual del objeto para decidir que hacer    
En este caso, el estado de guarda puede tomar dos valores:
+ Init: cuando el pixel se inicializa (se enciende por primera vez)
+ WaitTimeout: cuando esta esperando que pase el tiempo para cambiar su brillo

❓¿Cuáles son los eventos/inputs en el programa?
En este programa solo hay eventos internos, no se usan botones o sensores
+ Inicio del programa -> creacion del objeto en el estado init:  **self.state = "Init"**
+ Cambio de estado Init a WaitTimeout -> de **self.state == "Init"** a **self.state = "WaitTimeout"**
+ Cumplimiento de los intervalos de tiempo definidos -> **utime.ticks_ms(),self.startTime) > self.interval**

❓¿Cuáles son las acciones en el programa?
+ display.set_pixel(...): Mostrar un pixel con brillo 0 o 9
+ Alternar estado del pixel entre 0 (apagar) y 9 (encender)
+ self.startTime = utime.ticks_ms(): Actualizar tiempo cada que se actualiza el estado
