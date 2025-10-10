
# Evidencias de la unidad 7

## 🔎 Fase: Set

### 📚Actividad 01    
❓¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?    
R/ La URL que obtuve fue: https://czskkfpf-3000.use2.devtunnels.ms/

Usamos esta URL en lugar de localhost o la IP local pq el celular no puede conectarse directamente al servidor q esta en mi computador. El tunel de Dev Tunnels crea un enlace publico q permite q mi celular pueda comunicarse con el servidor desde internet aunque no este en la misma red que el computador

❓Describe brevemente qué hace npm install y npm start.    
R/ npm install -> sirve para instalar todos los archivos y librerias q necesita el proyecto para funcionar correctamente

npm start -> se usa para iniciar el servidor, q en este caso es el archivo que hace posible la comunicación entre el celular y el computador

❓¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?    
R/ En la terminal se podian ver mensajes del servidor indicando las conexiones y los datos q se recibian desde el celular
Primero aparecieron las lineas:

```
Server is listening on http://localhost:3000  
New client connected  
New client connected

```
Despues se imprimieron los valores de posicion q el celular enviaba al tocar la pantalla, por ejemplo:

```
Received message => { type: 'touch', x: 191.48, y: 222.48 }
```
Los mensajes son iguales para ambos clientes, no se muestran identificadores diferentes. Solo se ve cuando se conectan y los datos q el servidor recibia desde el celular

❓Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?
R/ La interaccion funciono correctamente, al mover el dedo en la pantalla del celular el circulo en el computador tambien se movia siguiendo la direccion del toque.
Sin embargo note q a veces el movimiento del circulo iba un poco lento, como si hubiera un pequeño retraso. Creo q esto se debio a la conexion a internet, ya q parecia faltarle algo de potencia. Aun asi, la comunicacion entre ambos dispositivos se mantuvo estable y el sistema respondio de forma adecuada

## 🔎 Fase: Seek

### 📚Actividad 02     

### 📚Actividad 03

### 📚Actividad 04

## 🛠 Fase: Apply

### 📚Actividad 05


