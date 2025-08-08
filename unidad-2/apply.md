# Unidad 2


## 🛠 Fase: Apply
### 📚 Actividad 04 - Diseño de la lógica de una bomba temporizada    
⭐Diagrama maquina de estados
<img width="821" height="903" alt="Diagrama de estados – Bomba" src="https://github.com/user-attachments/assets/0a9ba7de-fc55-43ba-9155-4b87b5d1434f" />


### 📚 Actividad 05 - Implementando la Bomba Temporizada    
⭐Codigo bomba:
```python
from microbit import *
import utime
import music #permite reproducir sonidos en el speaker

#estados
STATE_CONFIG = 0
STATE_ARMED = 1
STATE_EXPLODED = 2

#vrbles
state = STATE_CONFIG
countdown = 20  #tiempo inicial
last_tick = utime.ticks_ms()

while True:
    if state == STATE_CONFIG:
        display.scroll(str(countdown))  #mostrar el tiempo completo, str(countdown) es para convertir numero a texto

        if button_a.was_pressed() and countdown < 60: #limite max
            countdown += 1
            display.scroll(str(countdown))

        if button_b.was_pressed() and countdown > 10: #limite min
            countdown -= 1
            display.scroll(str(countdown))

        if accelerometer.was_gesture("shake"): #cambio de estado
            state = STATE_ARMED
            display.show(Image.ANGRY)
            utime.sleep(1)
            display.show(str(countdown))
            last_tick = utime.ticks_ms()

    elif state == STATE_ARMED:
        now = utime.ticks_ms()
        if utime.ticks_diff(now, last_tick) >= 1000: #aqui le va restando 1 al contador y actualiza el ultimo tiempo
            countdown -= 1
            last_tick = now

            if countdown > -1:
                display.show(str(countdown)) #aqui no use el scroll por temas de agilidad de la cuenta atras
            else: #cambio de estado
                state = STATE_EXPLODED
                music.play(music.POWER_DOWN)

    elif state == STATE_EXPLODED:
        display.show(Image.SKULL)

        if pin_logo.is_touched():
            state = STATE_CONFIG
            countdown = 20
            display.clear()
```
⭐Vectores de prueba básicos
STATE_CONFIG
+ Presionar boton A -> ¿El temporizador aumenta en 1? -> Si-> Funciona correctamente
+ Presionar boton B -> ¿El temporizador disminuye en 1? -> Si -> Funciona correctamente
+ Agitar el micro bit -> ¿Muestra carita enojada y luego el valor del temporizador? -> Si -> Funciona correctamente

STATE_ARMED
+ ¿Luego de mostrar el valor del temporizador, se muestra como va disminuyendo en 1 hasta llegar a 0? -> Si-> Funciona correctamente
+ ¿Luego de llegar a 0 muestra una calavera y reproduce un tono tipo game over? -> Si -> Funciona correctamente

STATE_EXPLODED
+ ¿Despues de explotar la calavera se muestra indefinidamente? -> Si -> Funciona correctamente
+ Tocar el boton touch -> ¿Se reinicia al estado inicial y el contador esta en 20? -> Si -> Funciona correctamente
