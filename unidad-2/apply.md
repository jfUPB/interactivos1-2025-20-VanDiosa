# Unidad 2


## 🛠 Fase: Apply
### 📚 Actividad 04 - Diseño de la lógica de una bomba temporizada    
⭐

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
            last_tick = utime.ticks_ms()

    elif state == STATE_ARMED:
        now = utime.ticks_ms()
        if utime.ticks_diff(now, last_tick) >= 1000: #aqui le va restando 1 al contador y actualiza el ultimo tiempo
            countdown -= 1
            last_tick = now

            if countdown > 0:
                display.show(str(countdown)) #aqui no use el scroll por temas de agilidad de la cuenta atras
            else: #cambio de estado
                state = STATE_EXPLODED
                display.show(Image.SKULL)
                music.play(music.POWER_DOWN) #pa q suene bonito

        if pin_logo.is_touched():
            state = STATE_CONFIG
            countdown = 20
            display.clear()

    elif state == STATE_EXPLODED:
        display.show(Image.SKULL)

        if pin_logo.is_touched():
            state = STATE_CONFIG
            countdown = 20
            display.clear()
```
⭐Vectores de prueba básicos
