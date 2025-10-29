
# Evidencias de la unidad 8

## 🔎 Fase: Seek

### 📚Actividad 01   

#### 🧐 Referencias    
Como referencia y punto de partida inicial tome el proyecto de la unidad anterior que se ve asi:
<img width="816" height="813" alt="Captura de pantalla 2025-10-17 002443" src="https://github.com/user-attachments/assets/e0b85b40-1e8c-4cc0-89e8-8183766e8bda" />
<img width="812" height="810" alt="Captura de pantalla 2025-10-17 002430" src="https://github.com/user-attachments/assets/6caa89e4-f476-4514-b7df-de5475138f6e" />

En esta nueva version, para la interfaz del movil, me gustaria añadir un boton deslizante para el cambio de 3 espectros a 1, no se pq pero me imagino algo como el modificador de tipo de cuerpo de la opcion de editar avatar en roblox:
<img width="1058" height="465" alt="Captura de pantalla 2025-10-24 104357" src="https://github.com/user-attachments/assets/01218d85-3fcb-4b12-b420-61cf7d9276fe" />

En el desktop me gustaria que al sacudir el microbit salieran y se expandieran un tipo ondas. Y si lo logro me gustaria que fueran brillantes
<img width="720" height="641" alt="videoframe_27" src="https://github.com/user-attachments/assets/7022de77-2618-424e-a5bb-d87f0db7e85e" />
![db725e3d8c44831e3b61f16b9cda0772](https://github.com/user-attachments/assets/bd810e1e-02ad-4ada-85dd-1385838b5d2a)

#### 🧐 Concepto    
El visualizador interactivo Pulse of... esta inspirado en Black Swan y Fake Love de BTS:
+ En el modo Black Swan se muestran tres circulos concentricos que representan las capas del sonido (voz altos y bajos) reaccionando al ritmo de la cancion
+ En Fake Love los espectros cambian a formas triangulares y el fondo pasa de negro a blanco transformando de esa forma la atmosfera visual

Desde el celular el usuario puede deslizar horizontalmente para cambiar la paleta de colores y verticalmente para modificar la distancia entre los espectros fusionandolos. Con el microbit se podra alternar entre canciones con los botones A y B y al detectar movimiento con el acelerometro generar destellos tipo explosion expandiendo ondas luminosas desde el centro

#### 🧐 Explicación control movil y microbit
Movil-Touch: 
+ Deslizamiento horizontal: cambia la gama de colores de los espectros
+ Deslizamiento vertical: fusiona o separa las capas (de tres espectros a uno)

Microbit:
+ Boton A: cambia la musica de Black Swan a Fake Love, variando de un fondo negro a uno claro, y cambiando los espectos de circulos a triangulos
+ Boton B: regresa al modo Black Swan
+ Acelerometro: al detectar movimiento, emite unos aros de luz que parten desde el centro de los espectros y se expande en el lienzo

#### ✍️ Bocetos    
Este es el boceto 1 de como me imagine las interfaces:
<img width="1920" height="1080" alt="BocetoSistemas" src="https://github.com/user-attachments/assets/dde99a5c-4dec-4a6d-a1f4-064e95caec36" />

Luego en al terminar la interfaz del celular pense en que me gustaria pausar o iniciar la musica en el desktop, entonces hice otra version del boceto:
<img width="1920" height="1080" alt="BocetoSistemas" src="https://github.com/user-attachments/assets/a41d626e-7986-4fe7-a9f3-69f8ab5a2648" />


#### ✍️ Diagrama
<img width="5647" height="1594" alt="Diagramas Sistemas Fisicos" src="https://github.com/user-attachments/assets/d054bed8-aace-4df5-9015-044ba5054fbb" />


## 🛠 Fase: Apply

### 📚Actividad 02  
#### ✍️ Proceso de Construcción
Este proyecto lo inicie usando el codigo de la actividad anterior, un visualizador de audio con tres circulos concentricos que reaccionaban al ritmo de una cancion (Black Swan de BTS). Esta versión inicial me servio como punto de partida para incorporar el microbit

En la primera clase de esta unidad:

1. Revise el codigo, que estuviera funcionando correctamente, lo clone y subi a un nuevo repo de github
2. Antes de la nueva interaccion me quise tomar el tiempo de poner mas bonita la interfaz del celular, ya que, solo era el fondo negro con un texto en el centro que decia deslizaste a tal lado o capas fusionadas o no…
- Primero se logro tener el triangulo del slider, pero era meramente visual no funcional, y la punta quedo hacia arriba (en el boceto la imagine hacia abajo). Ademas sentia q el canva era muy pequeño entonces lo cambie para que se adaptara al tamaño de la pantalla dependiendo del celular usando:  `createCanvas(windowWidth, windowHeight);`
- Chat me comento que P5.js tiene un elemento deslizante: `createSlider()`  pero al usar lo se me generaba de forma horizontal por lo que se formaba un conflicto con el cambio de color que se controlaba tmb de forma horizontal
- Entonces dividi el canva en 3 zonas, una para el titulo, otra para el slider y abajo una zona para el cambio de color. Tmb opte por no usar el elemento antes mencionado, entonces se creo una linea y una perilla. Aqui se me presento otra situacion. Hasta el momento solo estaba modificando el codigo del sketch del mobile pero entonces para que el slider funcionara tmb modifique unas vrbles en el sketch del desktop, para que la fusion ya no dependiera de recibir que se movio de arriba a abajo si no de una vrblae entre 0 y 1. En este momento ya funcionaba todo bien. Pero no tenia el triangulo entonces simplemente lo añadi detras del slider como algo meramente estetico
- Tmb use emojis para que no se sintiera una interfaz tan plana, y asi quedo:
<img src="https://github.com/user-attachments/assets/82106d9b-4f2b-4537-b446-e8be518a7b69" width="300">

#### Codigos 💻

#### Enlace al repositorio 🔗

## ⭐ Autoevaluación





