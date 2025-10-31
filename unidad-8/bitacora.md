
# Evidencias de la unidad 8

## Actividad 01

**Documenta los referentes visuales que te inspiren.**

En realidad toda esta muy inspirado en lo que aparece en mi cabeza al escuchar esta canción, sin embargo, también me inspire en la estetica que sulen tener los conciertos de la cantante,  donde todo suele ser muy oscuro iluminado unicamente por una luz principal que esta sobre la artista, así:

<img width="637" height="1058" alt="image" src="https://github.com/user-attachments/assets/471b6359-d65f-489c-beaa-ce408db0ca0c" />

y la tambíen en como se expresa, especialmente en [esta](https://www.youtube.com/watch?v=iCzwu3sDdhg) presentación, donde se le ve muy estallada y es parte de lo que queria mostrar.

**Define el concepto de las visuales que quieres crear.**

Las visuales que quiero crear en esta unidad van de la mano con lo que cree para la unidad pasada, es decir, visuales para una canción que den la idea de un video músical interactivo, que fuera capaz de recrear el sentimiento que trasnmite la canción de obsesión y limerencia. Es por esto que quise agregar aun más cosas ya que usamos la herramienta del micro:bit, así que ahora queria que girara para que diera un efecto más intenso y que se agregaran corazones con un boton del microbit. También como agregado se me ocurrión que el la pantalla del microbit apareciera el texto "I love you", pero todavía no estoy segura de lograr esta parte

**Explica cómo el móvil y el micro:bit controlarán las visuales.**

Bueno el movil sigue agregando ondas dentro del programa e interactuando con las letras en la lluvia, y ahora con el acelerometro dle micro:bit rote el programa y con el botón a se le puede añadir una lluvia de corazones.

**Haz un bocetos de todas las interfaces del sistema.**

![Imagen de WhatsApp 2025-10-31 a las 14 29 33_7d0816ae](https://github.com/user-attachments/assets/2a9d6e72-d6ad-4312-8272-6807ee470d86)

**Haz un diagrama que explique cómo se comunicarán los diferentes componentes del sistema.**

<img width="345" height="526" alt="image" src="https://github.com/user-attachments/assets/757b1e3a-266a-4e1c-8a68-08fa128d5c5d" />

## Actividad 02

**Documenta todo el proceso de construcción.**

Para construir este programa empece diciendole lo siguinete a la IA:
<img width="1042" height="493" alt="image" src="https://github.com/user-attachments/assets/80ee865e-dfe6-46b7-ad2c-d45143b35a5c" />

Con esto ya estaba listo casi todo, solo tenia un par de problemas con el microbit ya que el programa ejecutaba pero se cerraba apenas iniciaba
<img width="1033" height="600" alt="image" src="https://github.com/user-attachments/assets/3d585843-71ee-4c5e-bdc7-838dc4ab8eaf" />

Pero después identifique que esto se debia que en lugar de 'COM5' PUSE 'COM3' y ahí no estaba conectado el  microbit, por eso no identificaba nada. Luego, el problema era que no se mandaba la info de lo que debia hacer el micro:bit 
<img width="1065" height="373" alt="image" src="https://github.com/user-attachments/assets/06290ab2-8731-4cbf-a897-4420285202ef" />

y era porque en realidad lo que estaba en el código no conectaba con nada, despúes logó corregirlo pero solo se veían los corazones y no rotaba. Como chat ya estaba alucinando empece otra comversación con el, donde dijo lo siguiente:
<img width="999" height="172" alt="image" src="https://github.com/user-attachments/assets/96706716-a9dc-4bd2-b061-3d36d35e422f" />}

Y ahora si todo en la pantalla estaba tal y como quería pero no aparecia el texto en el microbit, que eso era más un agregado pero lo quería incluir como un detalle de fina coquetería, pero no dio :(

**Incluye todos los códigos: servidor, cliente móvil, cliente de escritorio y micro:bit.**

server

``` java script
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
const { SerialPort } = require('serialport');
const { ReadlineParser } = require('@serialport/parser-readline');

const app = express();
const server = http.createServer(app);
const io = socketIO(server);
const port = 3000;

// Archivos estáticos (public/index.html, etc.)
app.use(express.static('public'));

// Configurar conexión con micro:bit
const microbitPort = new SerialPort({
  path: 'COM6', 
  baudRate: 115200,
});

const parser = microbitPort.pipe(new ReadlineParser({ delimiter: '\n' }));

parser.on('data', (data) => {
  const cleanData = data.trim();
  console.log(' micro:bit dice:', cleanData);

  // interpreta mensajes simples del micro:bit
  if (cleanData === "heart") {
    io.emit('microbit', { type: "button", button: "A" });
  } 
  else if (cleanData.startsWith("tilt:")) {
    // ejemplo: tilt:10,-5
    const [pitch, roll] = cleanData.replace("tilt:", "").split(",");
    io.emit('microbit', { type: "tilt", pitch: parseFloat(pitch), roll: parseFloat(roll) });
  }
  else if (cleanData === "I love you") {
    io.emit('microbit', { type: "text", value: "I love you" });
  }
});

io.on('connection', (socket) => {
  console.log(' New client connected');

  socket.on('message', (message) => {
    console.log('From mobile =>', message);
    socket.broadcast.emit('message', message);
  });

  socket.on('microbitMessage', (txt) => {
    console.log('Sending to micro:bit =>', txt);
    microbitPort.write(txt + '\n');
  });

  socket.on('disconnect', () => {
    console.log('Client disconnected');
  });
  socket.on('microbit', (data) => {
  if (data.type === 'display' && data.text) {
    console.log(' Enviando texto al micro:bit =>', data.text);
    microbitPort.write(`display:${data.text}\n`);
  }
});
});


// Iniciar servidor
server.listen(port, () => {
  console.log(` Server listening on http://localhost:${port}`);
});
```

Desktop
```java script
let socket;
let circleX = null;
let circleY = null;

let song, fft;
let particles = [];
let rainLetters = [];
let halos = [];
let hearts = [];
let estado = "inicio";

let startChorus = 55;
let endChorus = 72;
let startOutro = 104;
let endOutro = 121;

let tiltX = 0;
let tiltY = 0;

function preload() {
  song = loadSound("Mitski - Pink in the Night.mp3");
}

function setup() { 
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB, 360, 100, 100, 1);
  fft = new p5.FFT();
  background(0);

  socket = io();

  socket.on("connect", () => console.log(" Connected to server"));
  socket.on("disconnect", () => console.log(" Disconnected from server"));
  socket.on("connect_error", (err) => console.error("Socket error:", err));

  socket.on("message", (data) => {
    if (data && data.type === "touch") {
      // Asegúrate de que el celular esté enviando su tamaño de pantalla
      // (data.phoneWidth y data.phoneHeight)
      const phoneW = data.phoneWidth || 360;  // valor por defecto
      const phoneH = data.phoneHeight || 640;

      circleX = map(data.x, 0, phoneW, 0, width);
      circleY = map(data.y, 0, phoneH, 0, height);
    }
  });

  // Comunicación con el micro:bit
  socket.on("microbit", (data) => {
    if (data.type === "button") {
      if (data.button === "A") addHeart(); // Botón A → Corazón
    }

    if (data.type === "tilt") {
      applyTilt(data.pitch, data.roll); // Inclinación → rotación del canvas
    }
  });

  userStartAudio();
}

function draw() {


let hueShift = map(mouseX, 0, width, 310, 350);
  background(hueShift, 30, 10, 0.1);

  push();
  translate(width / 2, height / 2);
  rotate(radians(tiltX)); // pitch controla rotación
  translate(-width / 2, -height / 2);

  let spectrum = fft.analyze();
  let bass = fft.getEnergy("bass");
  let treble = fft.getEnergy("treble");

  // Cambios de estado según tiempo del audio
  let t = song.isPlaying() ? song.currentTime() : 0;
  if (t > startChorus && t < endChorus) {
    if (estado !== "coro") {
      socket.emit("microbit", { type: "display", text: "I love you" }); 
    }
    estado = "coro";
  } else if (t > startOutro && t < endOutro) {
    estado = "otrocoro";
  } else estado = "inicio";

  // Partículas de fondo
  if (frameCount % 3 === 0) particles.push(new Particle());
  for (let p of particles) {
    p.update();
    p.show();
  }
  particles = particles.filter((p) => !p.isOffscreen());

  // Efectos de toque o micro:bit
  if ((mouseIsPressed || touches.length > 0) && frameCount % 5 === 0) {
    halos.push(new Halo(mouseX, mouseY));
  }
  if (circleX !== null && circleY !== null && frameCount % 5 === 0) {
    halos.push(new Halo(circleX, circleY));
  }

  for (let h of halos) {
    h.update();
    h.show();
  }
  halos = halos.filter((h) => !h.isDone());

  // Letras
  if (treble > 220 && frameCount % 5 === 0 && estado === "inicio") {
    let txts = ["glow", "pink", "shine", "light"];
    rainLetters.push(new RainLetter(random(width), 0, random(txts)));
  }

  if (estado === "coro" && frameCount % 3 === 0) {
    rainLetters.push(new RainLetter(random(width), random(height), "I love you"));
  } else if (estado === "otrocoro" && frameCount % 10 === 0) {
    rainLetters.push(new RainLetter(random(width), random(height), "Try again"));
  }

  for (let r of rainLetters) {
    r.update();

    let touchX = mouseIsPressed ? mouseX : circleX;
    let touchY = mouseIsPressed ? mouseY : circleY;
    if (touchX && touchY) {
      let d = dist(r.x, r.y, touchX, touchY);
      if (d < 100) {
        push();
        textSize(22);
        fill(330, 80, 100, map(d, 0, 100, 1, 0.2));
        text(r.txt, r.x, r.y);
        pop();
        continue;
      }
    }
    r.show();
  }
  rainLetters = rainLetters.filter((r) => r.alpha > 0);

  // Corazones del micro:bit
  for (let h of hearts) {
    h.update();
    h.show();
  }
  hearts = hearts.filter((h) => !h.isOffscreen());

  // Bass reactivo
  if (bass > 180) {
    fill(330, 60, 100, 0.05);
    rect(0, 0, width, height);
  }

  if (estado === "coro") {
    fill(330, 30, 100, 0.08);
    rect(0, 0, width, height);
  }

  if (circleX !== null && circleY !== null) {
    fill(320, 80, 100);
    noStroke();
    ellipse(circleX, circleY, 10);
  }

  pop();
}

function touchStarted() {
  userStartAudio();
  if (!song.isPlaying()) song.play();
  return false;
}

// Corazones que aparecen con el micro:bit
function addHeart() {
  for (let i = 0; i < 8; i++) {
    hearts.push(new Heart(random(width), random(height)));
  }
}

// Aplicar inclinación del micro:bit
function applyTilt(pitch, roll) {
  tiltX = pitch;
  tiltY = roll;
}

// --- Clases visuales ---

class Particle {
  constructor() {
    this.x = random(width);
    this.y = random(height);
    this.size = random(1, 3);
    this.alpha = random(100, 200);
    this.speedY = random(-0.2, 0.2);
  }

  update() {
    this.y += this.speedY;
    this.alpha -= 0.3;
  }

  show() {
    noStroke();
    fill(330, 50, 100, this.alpha / 255);
    ellipse(this.x, this.y, this.size);
  }

  isOffscreen() {
    return this.alpha <= 0;
  }
}

class RainLetter {
  constructor(x, y, txt) {
    this.x = x;
    this.y = y;
    this.txt = txt;
    this.speed = random(0.5, 2);
    this.alpha = 255;
  }

  update() {
    this.y += this.speed;
    this.alpha -= 0.5;
  }

  show() {
    fill(330, 40, 100, this.alpha / 255);
    text(this.txt, this.x, this.y);
  }
}

class Halo {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.r = 0;
    this.alpha = 255;
  }

  update() {
    this.r += 2;
    this.alpha -= 3;
  }

  show() {
    noFill();
    stroke(330, 80, 100, this.alpha / 255);
    strokeWeight(1.5);
    ellipse(this.x, this.y, this.r);
  }

  isDone() {
    return this.alpha <= 0;
  }
}

class Heart {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.size = random(10, 30);
    this.alpha = 255;
    this.speedY = random(-1, -2);
  }

  update() {
    this.y += this.speedY;
    this.alpha -= 3;
  }

  show() {
    noStroke();
    fill(330, 90, 100, this.alpha / 255);
    beginShape();
    vertex(this.x, this.y);
    bezierVertex(this.x - this.size / 2, this.y - this.size / 2,
      this.x - this.size, this.y + this.size / 3,
      this.x, this.y + this.size);
    bezierVertex(this.x + this.size, this.y + this.size / 3,
      this.x + this.size / 2, this.y - this.size / 2,
      this.x, this.y);
    endShape(CLOSE);
  }

  isOffscreen() {
    return this.alpha <= 0;
  }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}


function applyTilt(pitch, roll) {
  tiltX = pitch;
  tiltY = roll;
}
```

Mobile
``` java script
let socket;
let lastTouchX = null; 
let lastTouchY = null; 
const threshold = 5;

function setup() {
    createCanvas(windowWidth, windowHeight);
    background(220);
    socket = io();

    socket.on('connect', () => {
        console.log('Connected to server');
    });

    socket.on('message', (data) => {
        console.log(`Received message: ${data}`);
    });

    socket.on('disconnect', () => {
        console.log('Disconnected from server');
    });

    socket.on('connect_error', (error) => {
        console.error('Socket.IO error:', error);
    });
    socket.emit("message", {
    type: "touch",
    x: touchX,
    y: touchY,
    phoneWidth: window.innerWidth,
    phoneHeight: window.innerHeight
    });

}

function draw() {
    background(220);
    fill(255, 0, 128);
    textAlign(CENTER, CENTER);
    textSize(24);
    text('Toca para interactuar', width / 2, height / 2);
}

function touchMoved() {
    if (socket && socket.connected) { 
        let dx = abs(mouseX - lastTouchX);
        let dy = abs(mouseY - lastTouchY);

        if (dx > threshold || dy > threshold || lastTouchX === null) {
            let touchData = {
                type: 'touch',
                x: mouseX,
                y: mouseY
            };
            socket.emit('message', touchData);

            lastTouchX = mouseX;
            lastTouchY = mouseY;
        }
    }
    return false;
}
```

Autoevaluación

Mi nota es: 5

| Actividad | Estado | Justificación |
|-----------|--------|---------------|
| Ac 1 | completo | Ahí estan claramente expresados los referentes visuales y el como funcionan la conección por medio del diagrama|
| Act 2| completo | Logre incluir el micro:bit dentro del programa y corregir errores que tenía el código antes para que ahora sea más interativo|
