# Unidad 1

## 🛠 Fase: Apply

### Actividad 05

### Actividad 06

```phyton
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
