# Unidad 3


## 🛠 Fase: Apply

### 📚 Actividad 06 - Crear la bomba en p5.js   
[🌟 Ver mi programa en p5.js](https://editor.p5js.org/VanDiosa/sketches/4kntLSOGZ)

🌟Codigo del programa en p5.js
```javascript
// equivale a class BombTask: def __init__(self)
let password = ['A','B','A'];
let keyEntered = []; // clave ingresada
let keyIndex = 0; // indice clave
let count = 20;
let startTime;
let state = "CONFIG"; // estado inicial

function setup () { // tmb de class BombTask: def __init__(self)
  createCanvas(400, 400); 
  background(220);
  startTime = millis();
  textAlign(CENTER, CENTER);
  textSize(40)
}

function draw () { // def update(self)
  background(0);
  
  if (state === "CONFIG") { // ESTADO
    fill(0, 0, 200);
    text("⚙️CONFIG⚙️", width / 2, height / 3);
    text(count, width / 2, height / 2);
  }
  
  else if (state === "ARMED") { // ESTADO
    fill(200, 0, 0);
    text("💣ARMED💣", width / 2, height / 3);

    if (millis() - startTime > 1000) { // cada segundo baja el contador
      count--; //
      startTime = millis();
    }

    text(count, width / 2, height / 2);

    if (count <= 0) {
      state = "EXPLODED";
    }
  }

  else if (state === "EXPLODED") {// ESTADO
    fill(0, 200, 0);
    text("💀 EXPLODED 💀", width / 2, height / 2);
  }
  
}


function keyPressed() { // equivalente a class ButtonTask
  let k = key.toUpperCase(); // convierte la tecla a mayuscula siempre
  if (state === "CONFIG") { // === es comparacion estricta
    if (k === 'A') {
      count = min(count + 1, 60); // lo de min es tipo menor que, numero_actual = min(numero_actual + 1, 60)
    }
    if (k === 'B') {
      count = max(count - 1, 10);
    }
    if (k === 'S') { // shake
      state = "ARMED";
      startTime = millis();
    }
  }
  
  else if (state === "ARMED") {
    if (k === 'A' || k === 'B') {
      passwordInput(k);
    }
  }
  
  else if (state === "EXPLODED") {
    if (k === 'R') { // volver a config
      count = 20;
      state = "CONFIG";
      startTime = millis();
    }
  }
}

// función para manejar la clave
function passwordInput(k) {
  keyEntered [keyIndex] = k;
  keyIndex++;

  if (keyIndex === password.length) {
    let passIsOK = true;
    for (let i = 0; i < password.length; i++) {
      if (keyEntered [i] !== password[i]) {
        passIsOK = false;
        break;
      }
    }

    if (passIsOK) {
      count = 20;
      state = "CONFIG";
    }
    // reinicia la secuencia siempre
    keyIndex = 0;
    keyEntered  = [];
  }
}
```
