# Unidad 3

## 🔎 Fase: Set + Seek

### 📚 Actividad 05 - Es momento de modelar la bomba y definir vectores de prueba   
1. Construye el modelo de la bomba 3.0. Como ya tienes el código puedes tener un modelo muy preciso.    
⭐Modelando del programa con una máquina de estados:
<img width="934" height="895" alt="Maquina de Estados Bomba 3 0" src="https://github.com/user-attachments/assets/94a3898b-9f1c-4a18-85b5-b783f1948a73" />


2. Crear una tabla con los vectores de prueba. La tabla debe tener 4 columnas por vector y puedes agrupar vectores en un gran vector.    
⭐Tabla de vectores de prueba    

| Estado inicial | Evento disparador | Acciones | Estado final |
|----------------|------------------|----------|--------------|
| CONFIG | button_a.was_pressed() (contador < 60) | count = count + 1 ; actualizar -> display | CONFIG |
| CONFIG | button_b.was_pressed() (contador > 10) | count = count - 1 ; actualizar -> display | CONFIG |
| CONFIG | accelerometer.was_gesture("shake") | Guardar -> startTime ; cambiar -> state = "ARMED" | ARMED |
| ARMED | Pasan 1000 ms (1 seg) y count > 0 | count = count - 1 ; actualizar -> display | ARMED |
| ARMED | Pasan 1000 ms (1 seg) y count == 0 | Mostrar calavera ; cambiar -> state = "EXPLODED" | EXPLODED |
| ARMED | Se pulsa "A" o "B" | Guardar caracter en key ; avanzar keyindex | ARMED |
| ARMED | Secuencia "A-B-A" correcta | Reiniciar count = 20 ; mostrar en display count ; actualizar -> keyindex = 0 | CONFIG |
| ARMED | Secuencia incorrecta | keyindex = 0 | ARMED |
| EXPLODED | pin_logo.is_touched() | Reiniciar count = 20 ; mostrar en display count ; cambiar -> state = CONFIG| CONFIG |


