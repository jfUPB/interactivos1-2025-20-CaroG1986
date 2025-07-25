# Unidad 1

## 🛠 Fase: Apply

### Actividad 05

Este programa tiene dos partes: El código de micro:bit que esta en python y es el encargado de detectar si el dispositivo esta conectado y si se detecta un cambio, ya sea que los botones sean presionados o que algún sensor detecte algo, en este caso solo detecta si los botonees fueron presionados y los distingue entre si. La otra parte es el código del programa p5.js que recibe la información sobre lo que pasa en el micro:bit y lo transforma en una respuesta dentro del programa, en este caso es el cambiar el color del cuadro mientras el botón este presionado.

### Actividad 06

_Crea un programa en p5.js que muestre un círculo en la pantalla. Utiliza los botones A y B del micro:bit para controlar la posición en x del círculo en el canvas de p5.js._

Este es el [enlace](https://editor.p5js.org/CaroG1986/sketches/6BhcGjDzI) para el programa, y el siguente es el código en javascript.

``` javascript
  let port;
  let connectBtn;
  let connectionInitialized = false;
 let x=200;

  function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton("Connect to micro:bit");
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
  }

  function draw() {
    background(220);

    if (port.opened() && !connectionInitialized) {
      port.clear();
      connectionInitialized = true;
    }
   fill ('red');
    if (port.availableBytes() > 0) {
      let dataRx = port.read(1);
      if (dataRx == "A") {
        x= x-20;
        fill('blue');
      } else if (dataRx == "N") {
        x= x+20;
        fill ('green');
      }
    }
    circle(x,height/2,100);

    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  }

  function connectBtnClick() {
    if (!port.opened()) {
      port.open("MicroPython", 115200);
      connectionInitialized = false;
    } else {
      port.close();
    }
  }
```

Este es el código del micro:bit 

```python
# Imports go at the top
from microbit import *

uart.init(baudrate=115200)
display.show(Image.SILLY)

while True:
    if button_a.was_pressed():
        uart.write('A')
    if button_b.was_pressed():
        uart.write('N')
    sleep(100)
```

