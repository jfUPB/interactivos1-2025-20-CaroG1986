# Evidencias de la unidad 4

## Código

[Enlace a la aplicación a modificar](https://editor.p5js.org/generative-design/sketches/ByDlgcq9a1V)

Código a modificar:

``` js
// P_2_1_3_04
/**
 * changing positions of stapled circles in a grid
 *
 * MOUSE
 * position x          : module detail
 * position y          : module parameter
 *
 * KEYS
 * 1-3                 : draw mode
 * arrow left/right    : number of tiles horizontally
 * arrow up/down       : number of tiles vertically
 * s                   : save png
 */
'use strict';

var count = 0;
var tileCountX = 6;
var tileCountY = 6;

var drawMode = 1;

function setup() {
  createCanvas(windowWidth, windowHeight);
  rectMode(CENTER);
}

function draw() {
  clear();
  noFill();

  count = mouseX / 10 + 10;
  var para = mouseY / height;

  var tileWidth = width / tileCountX;
  var tileHeight = height / tileCountY;

  for (var gridY = 0; gridY <= tileCountY; gridY++) {
    for (var gridX = 0; gridX <= tileCountX; gridX++) {

      var posX = tileWidth * gridX + tileWidth / 2;
      var posY = tileHeight * gridY + tileHeight / 2;

      push();
      translate(posX, posY);

      // switch between modules
      switch (drawMode) {
      case 1:
        stroke(0);
        for (var i = 0; i < count; i++) {
          rect(0, 0, tileWidth, tileHeight);
          scale(1 - 3 / count);
          rotate(para * 0.1);
        }
        break;
      case 2:
        noStroke();
        for (var i = 0; i < count; i++) {
          var gradient = lerpColor(color(0, 0), color(166, 141, 5), i / count);
          fill(gradient, i / count * 200);
          rotate(QUARTER_PI);
          rect(0, 0, tileWidth, tileHeight);
          scale(1 - 3 / count);
          rotate(para * 1.5);
        }
        break;
      case 3:
        noStroke();
        for (var i = 0; i < count; i++) {
          var gradient = lerpColor(color(0, 130, 164), color(255), i / count);
          fill(gradient, 170);

          push();
          translate(4 * i, 0);
          ellipse(0, 0, tileWidth / 4, tileHeight / 4);
          pop();

          push();
          translate(-4 * i, 0);
          ellipse(0, 0, tileWidth / 4, tileHeight / 4);
          pop();

          scale(1 - 1.5 / count);
          rotate(para * 1.5);
        }
        break;
      }

      pop();

    }
  }
}

function keyReleased() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
  if (key == '1') drawMode = 1;
  if (key == '2') drawMode = 2;
  if (key == '3') drawMode = 3;
  if (keyCode == DOWN_ARROW) tileCountY = max(tileCountY - 1, 1);
  if (keyCode == UP_ARROW) tileCountY += 1;
  if (keyCode == LEFT_ARROW) tileCountX = max(tileCountX - 1, 1);
  if (keyCode == RIGHT_ARROW) tileCountX += 1;
}
```

[Enlace a la aplicación modificada](https://editor.p5js.org/CaroG1986/sketches/-NOlOtEfs)

Código modificado:

``` js
// P_2_1_3_04

/**
 * changing positions of stapled circles in a grid
 *
 * MOUSE
 * position x          : module detail
 * position y          : module parameter
 *
 * KEYS
 * 1-3                 : draw mode
 * arrow left/right    : number of tiles horizontally
 * arrow up/down       : number of tiles vertically
 * s                   : save png
 */
"use strict";

var count = 0;
var tileCountX = 6;
var tileCountY = 6;

var drawMode = 1;

let port;
let connectBtn;
let connectionInitialized = false;
let microBitConnected = false;

const STATES = {
  WAIT_MICROBIT_CONNECTION: "WAITMICROBIT_CONNECTION",
  RUNNING: "RUNNING",
};

let appState = STATES.WAIT_MICROBIT_CONNECTION;
let microBitX = 0;
let microBitY = 0;
let microBitAState = false;
let microBitBState = false;
let prevmicroBitAState = false;
let prevmicroBitBState = false;
let cnv;

function setup() {
  cnv = createCanvas(windowWidth, windowHeight);
  rectMode(CENTER);
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(0, 0);
  connectBtn.mousePressed(connectBtnClick);
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}

function updateButtonStates(newAState, newBState) {
  // Generar eventos de keypressed
  if (newAState === false && prevmicroBitAState === true) {
    print("A released");
    drawMode = 2;
  }

  // Generar eventos de key released
  if (newBState === false && prevmicroBitBState === true) {
    drawMode = 3;
    print("B released");
  }

  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}

function draw() {
  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
    microBitConnected = false;
  } else {
    microBitConnected = true;
    connectBtn.html("Disconnect");

    if (port.opened() && !connectionInitialized) {
      port.clear();
      connectionInitialized = true;
    }

    if (port.availableBytes() > 0) {
      let data = port.readUntil("\n");
      if (data) {
        data = data.trim();
        let values = data.split(",");
        if (values.length == 4) {
          microBitX = int(values[0]) + windowWidth / 2;
          microBitY = int(values[1]) + windowHeight / 2;
          microBitAState = values[2].toLowerCase() === "true";
          microBitBState = values[3].toLowerCase() === "true";
          updateButtonStates(microBitAState, microBitBState);
        } else {
          print("No se están recibiendo 4 datos del micro:bit");
        }
      }
    }
  }

  switch (appState) {
    case STATES.WAIT_MICROBIT_CONNECTION:
      // No puede comenzar a dibujar hasta que no se conecte el microbit
      // evento 1:
      if (microBitConnected === true) {
        // Preparo todo para el estado en el próximo frame
        print("Microbit ready to draw");
        noCursor();
        appState = STATES.RUNNING;
      }
      break;
    case STATES.RUNNING:
      // EVENTO: estado de conexión del microbit
      if (microBitConnected === false) {
        print("Waiting microbit connection");
        cursor();
        appState = STATES.WAIT_MICROBIT_CONNECTION;
      }

      clear();
      noFill();

      count = microBitX / 10 + 10;
      var para = microBitY / height;

      var tileWidth = width / tileCountX;
      var tileHeight = height / tileCountY;

      //console.log(drawMode);

      for (var gridY = 0; gridY <= tileCountY; gridY++) {
        for (var gridX = 0; gridX <= tileCountX; gridX++) {
          var posX = tileWidth * gridX + tileWidth / 2;
          var posY = tileHeight * gridY + tileHeight / 2;

          push();
          translate(posX, posY);

          // switch between modules
          switch (drawMode) {
            case 1:
              stroke(0);
              for (var i = 0; i < count; i++) {
                rect(0, 0, tileWidth, tileHeight);
                scale(1 - 3 / count);
                rotate(para * 0.1);
              }
              break;
            case 2:
              noStroke();
              for (var i = 0; i < count; i++) {
                var gradient = lerpColor(
                  color(0, 0),
                  color(166, 141, 5),
                  i / count
                );
                fill(gradient, (i / count) * 200);
                rotate(QUARTER_PI);
                rect(0, 0, tileWidth, tileHeight);
                scale(1 - 3 / count);
                rotate(para * 1.5);
              }
              break;
            case 3:
              noStroke();
              for (var i = 0; i < count; i++) {
                var gradient = lerpColor(
                  color(0, 130, 164),
                  color(255),
                  i / count
                );
                fill(gradient, 170);

                push();
                translate(4 * i, 0);
                ellipse(0, 0, tileWidth / 4, tileHeight / 4);
                pop();

                push();
                translate(-4 * i, 0);
                ellipse(0, 0, tileWidth / 4, tileHeight / 4);
                pop();

                scale(1 - 1.5 / count);
                rotate(para * 1.5);
              }
              break;
          }

          pop();
        }
      }
  }
}

function keyReleased() {
  console.log(key);
  if (key == "s" || key == "S") saveCanvas(cnv);
  if (key == "1") drawMode = 1;
  if (key == "2") drawMode = 2;
  if (key == "3") drawMode = 3;
  if (keyCode == DOWN_ARROW) tileCountY = max(tileCountY - 1, 1);
  if (keyCode == UP_ARROW) tileCountY += 1;
  if (keyCode == LEFT_ARROW) tileCountX = max(tileCountX - 1, 1);
  if (keyCode == RIGHT_ARROW) tileCountX += 1;
}
```

## Video

[Video demostratativo](https://youtu.be/T9DtEQdHASk)






