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

### 📚 Actividad 02 - Implementando un semáforo con máquina de estados
⭐Codigo semaforo:
```python
from microbit import *
import utime #para manejar el tiempo en milisegundos

class Semaforo: #representa el semaforo
    def __init__(self): 
        self.state = "Rojo" #ESTADO inicial del semaforo
        self.startTime = utime.ticks_ms() #ACCION de guardar el tiempo actual
        self.interval = 3000  #ACCION: duracion de cada luz en ms

    def update(self): #metodo que actualiza el estado

        currentTime = utime.ticks_ms() #ACCION: mirar el tiempo q ha pasado

        if utime.ticks_diff(currentTime, self.startTime) > self.interval: #EVENTO revisa si el tiempo actual  es superior al intervalo definido
            #ESTADOS:
            if self.state == "Rojo": #si el estado actual es rojo
                self.state = "Verde" #pasa a verde
            elif self.state == "Verde": #si es verde
                self.state = "Amarillo" #pasa a amarillo
            elif self.state == "Amarillo": #si es amarillo
                self.state = "Rojo" #pasa a rojo

            self.startTime = currentTime  #ACCION reinicia contador del tiempo

        self.mostrar() #ACCION llama el metodo mostrar para encender el led que corresponda
        
    def mostrar(self): #metodo para imprimir el semaforo
        #ACCIONES:
        display.clear() # limpia la pantalla
        if self.state == "Rojo": #si en el if de uptade el estado paso a ser rojo
            display.set_pixel(2, 0, 9) #se enciende el led superior medio
        elif self.state == "Amarillo":  #si el estado actual es amarillo
            display.set_pixel(2, 2, 9) #se enciende el led medio de la fila 3
        elif self.state == "Verde": #si el estado actual es verde
            display.set_pixel(2, 4, 9) #se enciende el led medio de la fila inferior
            
semaforo = Semaforo() #ACCION: crear semaforo con estado inicial (rojo)

while True: #EVENTO en bucle, revisa el tiempo 
    semaforo.update()
    sleep(100) #evitar sobrecarga
```

❓Identifica los estados, eventos y acciones en tu código.    
⭐Estados: Son tres los principales, los colores del semaforo. El estado actual se almacena en "self.state" y cambia ciclicamente entre Red, Green, Yellow, Red, y asi sucesivamente

⭐Eventos: Al igual que en el ejemplo de la actividad 01 los eventos del semaforo tambien son internos, ya que, no se usan botones ni sensores: Los eventos son:    
+ self.state = "Red" -> Creación del objeto con estado inicial Red al inicio del programa
+ utime.ticks_diff(utime.ticks_ms(), self.startTime) > self.interval -> Verificacion del cumplimiento del intervalo de tiempo definido

⭐Acciones: cada que cambia de estado suceden ciertas acciones
+ display.clear() -> Se limpia la pantalla
+ self.startTime = utime.ticks_ms() -> Actualizar el tiempo de inicio del nuevo estado
+ Mostrar el led correspondiente al color del estado actual: display.set_pixel(0, 2, 9) → Rojo, display.set_pixel(2, 2, 9) → Amarillo, display.set_pixel(4, 2, 9) -> Verde
