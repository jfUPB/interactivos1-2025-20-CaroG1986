
# Evidencias de la unidad 7

## Actividad 01 👰

**¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?** 🤵

https://k3nfwl9g-3000.use2.devtunnels.ms/mobile/

Yo creo que se debe usar este porque el servidor no esta conectandos dos páginas desde el mismo dispositivo, sino que busca conectar dos dispositivos diferentes   

**Describe brevemente qué hace npm install y npm start.** 🤵‍♂

npm install lo que hace es que intalar las dependencias del programa, es decir, básicamente las bibliotecas necesarias, mientras que npm start inicia el servidor que es lo que permite la conexión. 

**¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?** 🤵‍♂

El mensaje fue: 
```
Server is listening on http://localhost:3000
New client connected
New client connected
Received message => { type: 'touch', x: 210.19798278808594, y: 243.05540466308594 }
Received message => { type: 'touch', x: 195.4116668701172, y: 202.67222595214844 }
Received message => { type: 'touch', x: 194.2127685546875, y: 195.4752197265625 }
```

Ese mensaje a comparación de cuando se conectaba con el cliente de escritorio no muestra una posición o tamaño de las ventanas que se están manejando en el mismo computador sino que ahora la posición que nos interesa es en dónde se da el contacto en el celular que sería en este caso el cliente móvil. Es por esto que está ese tipo toque que es la información que necesitamos en este proyecto

**Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?** 🤵‍♂

Sí funcionó la interacción sin problema y también descubrimos que si se llegara a conectar otro cliente pues en sí el programa tendría como cierto fallo o se volvería loco en cierta forma porque no sabría muy bien a dónde mandar el círculo. Por otro lado si hay un poco de retraso pero no es muy significativo y son sí mucho menos de un segundo. Supongo que este a diferencia del de computador va a tener cierto retraso porque no se trata del mismo dispositivo.

## Actividad 02 👰

**Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?** 🤵‍♂

Dev tunnels es necesario en ese escenario porque está conectando el servidor local que está en mi dispositivo portátil con mi teléfono móvil. Este funciona conectando a través del internet ambos dispositivos, lo que permite que ahora no sea necesario conectar a través de la IP del computador o que ambos dispositivos deban tener la misma red de wi-fi, por lo que ahora simplemente usa el internet como un medio para dar esa intermediación entre ambos dispositivos.

**Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.** 🤵‍♂

Esa función es la encargada de dar las coordenadas respecto a la posición que esta tocando dentro del canvas en el dispositivo móvil y utiliza la variable threshold para que no se llene de mensajes Todo el tiempo que se haga algún movimiento pequeño sino que cuando sea algo más significativo y de esa forma que no se llene el puerto de mensajes innecesarios.

**Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?** 🤵‍♂

Las ventajas de usar este método de conexión es que permite una conexión más segura sin necesidad de tener la misma conexión wi-fi y funciona  incluso si los dispositivos siguen alguna clase de protección.sin embargo algo que funciona en este caso pero podría ver como desventaja es que sí o sí es necesario que ambos dispositivos estén conectados al internet.

**Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).** 🤵‍♂

<img width="1715" height="836" alt="image" src="https://github.com/user-attachments/assets/f16136cf-ebce-496b-81e4-3a291c2c7e46" />
<img width="621" height="821" alt="image" src="https://github.com/user-attachments/assets/4329ebe7-94dc-4995-af98-dc59ad80d64a" />
<img width="402" height="574" alt="image" src="https://github.com/user-attachments/assets/27e18543-9e3c-4f3a-ae31-05c12ef8d3e4" />

## Actividad 03 👰‍♀️

**¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?** 🤵‍♂

La función principal de esto es conectar la aplicación por medio de la carpeta 'public' qué es la que contiene la información de cómo se da la conexión en la computadora y el dispositivo móvil. A diferencia de la unidad anterior este no busca una ruta específica que está en el computador como antes que era página 1 página 2, y es por eso mismo que se permite una conexión con otro dispositivo.

**Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?** 🤵‍♂

Primero desde el movil el evento que envia la información es touchMoved, esa después le comunica al servidor sobre la información por medio de io.on y ya después se envía la información a el portátil por medio de socket on.broadcast, el portátil por su parte lo recibe con socket.on.El broadcast se usa ya que está es una trasmisión en vivo que cambia con el tiempo y necesita actualizarse.

**Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?** 🤵‍♂

>Yo creo que se conectarán dos computadores al mismo servidor serían los dos computadores los que recibirían el mensaje de el móvil ya que ambos se toman en este caso como los receptores.

Como no estaba muy segura sobre esa pregunta entonces investigué más sobre cómo funciona esta conexión. Por lo que descubrí que clientes pueden haber muchos sin embargo servidores activos con el mismo devtunnel solo hay uno, porque así funciona el devtunnel, generando una conexión con un solo servidor local entonces la información llegaría a el computador con el servidor inicial.

**¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?** 🤵‍♂

El console.log manda mensajes de si hay un nuevo cliente conectado o desconectado, en dónde está escuchando el servidor, y cuáles son los mensajes que estás recibiendo del cliente. Esos mensajes que se muestran son útiles porque permite el programador conocer qué está pasando en realidad en el programa y entonces si ocurre algún error se puede ver si fue desde la conexión o en cuanto a los mensajes que se recibieron.

## Actividad 04 👰‍♀️

**Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema.** 🤵‍♂

<img width="799" height="748" alt="image" src="https://github.com/user-attachments/assets/83c89838-aff6-472d-933b-626ac1eca174" />

## Actividad 05 👰‍♀️

La verdad siento que este fue un reto algo difícil, principalmente porque no sabía muy bien cómo combinar el concepto de una canción con visuales. Pero aún así aquí está mi idea:

La canción que utilicé se llama "Pink in the Night" de Mistki, la cual representa un amor que florece en soledad y en la imaginación. En esta canción se ve el amor pero también cierto comportamiento obsesivo, ya que expresa que es un pensamiento que no sale de su cabeza y está ahí brillando "rosa" en su habitación, de ahí claramente sale la paleta de colores para este trabajo. En una parte también menciona que cuando escucha las gotas de lluvia caer estás cantan por su amor. Me gusta la metáfora de que la repetitividad y constancia de estás gotas de lluvia representa las ideas que no puede sacarse de la mente, y la verdad cuando escucho esta canción yo también me imagino esas palabras repitiéndose una y otra vez. Sin embargo, a pesar de que el color rosa y las palabras de amor hacen que la escena se vea linda decidí que el fondo fuera negro no solo en representación de la noche sino también de que en realidad al final sigue estando sola en su habitación.La interacción del usuario en unas partes es el brillo que ocupa más espacio en su mente y en otras resalta las palabras que salen en la pantalla.

>Aunque todo eso suena muy poético pero yo creo que parece un edit de TikTok 😔

El código es el siguiente:

**server**

``` java script
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

app.use(express.static('public'));

io.on('connection', (socket) => {
    console.log('New client connected');
    socket.on('message', (message) => {
        console.log('Received message =>', message);
        socket.broadcast.emit('message', message);
    });

    socket.on('disconnect', () => {
        console.log('Client disconnected');
    });
});

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
});
```

**Código del desktop**

``` java script

let socket;
let circleX = null;
let circleY = null;

let song, fft;
let particles = [];
let rainLetters = [];
let halos = [];
let estado = "inicio";

let startChorus = 55;
let endChorus = 72;
let startOutro = 104;
let endOutro = 121;

function preload() {
  song = loadSound("Mitski - Pink in the Night.mp3");
}

function setup() {
  createCanvas(300, 400);
  colorMode(HSB, 360, 100, 100, 1);
  fft = new p5.FFT();
  background(0);

  socket = io();

  socket.on("connect", () => console.log("Connected to server"));
  socket.on("disconnect", () => console.log("Disconnected from server"));
  socket.on("connect_error", (err) => console.error("Socket error:", err));

  socket.on("message", (data) => {
    if (data && data.type === "touch") {
      circleX = data.x;
      circleY = data.y;
    }
  });

  userStartAudio();
}

function draw() {
  // Fondo dinámico, más etéreo
  let hueShift = map(mouseX, 0, width, 310, 350);
  background(hueShift, 30, 10, 0.1);

  let spectrum = fft.analyze();
  let bass = fft.getEnergy("bass");
  let treble = fft.getEnergy("treble");

  // Cambio de estado según tiempo del audio
  let t = song.isPlaying() ? song.currentTime() : 0;
  if (t > startChorus && t < endChorus) estado = "coro";
  else if (t > startOutro && t < endOutro) estado = "otrocoro";
  else estado = "inicio";

  if (frameCount % 3 === 0) particles.push(new Particle());
  for (let p of particles) {
    p.update();
    p.show();
  }
  particles = particles.filter((p) => !p.isOffscreen());


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
      // Las letras cerca del toque brillan más
      push();
      textSize(22);
      fill(330, 80, 100, map(d, 0, 100, 1, 0.2)); // más rosa al centro
      text(r.txt, r.x, r.y);
      pop();
      continue; // saltar el dibujado normal
    }
  }

  r.show();
}
rainLetters = rainLetters.filter((r) => r.alpha > 0);


  
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
}

function touchStarted() {
  userStartAudio();
  if (!song.isPlaying()) song.play();
  return false;
}


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

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

**código del mobile**

``` java script
let socket;
let lastTouchX = null; 
let lastTouchY = null; 
const threshold = 5;

function setup() {
    createCanvas(300, 400);
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
}

function draw() {
    background(220);
    fill(255, 192, 203);
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

así se ve

<img width="401" height="552" alt="image" src="https://github.com/user-attachments/assets/1d69bf45-5dda-45bc-bb80-d09aafa1775e" />
<img width="409" height="515" alt="image" src="https://github.com/user-attachments/assets/18862d98-13f4-45b5-b70a-97d786e06d29" />


## Autoevaluación 👰‍♀️

Mi nota es : 5.0 

| Actividad | nota  | justificación | 
|-----------|-------|---------------|
| 1 y 2     | 1 unidad | ambas esta completas y como se puede ver si logré comprender la función básica de este sistema y porque es tan util para puebras de diseño como estas|
| 3   |  1 unidad | esta completa y esta era más dobre la conexión en si entre los dos dispositivos lo caul me quedo claro|
|  4  | 1 unidad | completo| 
| 5   | 2 unidades | esta completa, tristemenete por cuestion de tiempo use IA (😔), sin embargo esta vez senti que era más algo conjunto que decirle uque haga todo y ya, porqur yo lo indicaba por ejemplo que hiciera todo con una maquina de estados para asi poder cambiar las visuales y tan bien corregi las partes que estaban relacionadas con la conexión, así que la IA fue principalmente para que pusiera los diseños que yo le decia y así ahorrar tiempo| 
