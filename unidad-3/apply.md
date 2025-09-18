# Unidad 3


## 🛠 Fase: Apply

### Atividad 06 

>Correcciones: La vez pasada en realidad no pude correr el código con micro:bit entonces no me di cuenta de muchos errores que habían en el programa. Empezando porque habían funciones que no llamaba en ningún punto como la función de actualizar el puerto serial o la función para que se vea algo en la pantalla de p5.js y qué está se actualice. Además de esto siento que me faltó escribir o representar bien las cosas en la pantalla para que se comprendiera mejor que estaba pasando mientras se llevaba acabo este experimento,  y en algunos momentos confundía el nombre de la clase Bombtask con el objeto bombtask. También, me había faltado definir bien la clase de evento y luego llamarla en la función setup, por esto me salía mucho que ese evento no existía. Pero ya comprendí mejor que paso con el programa y al visualizarlo con el micro:bit fue más sencillo.

[Es el link al programa](https://editor.p5js.org/CaroG1986/sketches/N7SY7VIPb)

``` java script
let bombtask;
let serialtask;
let event;
let port;
let connectBtn;

function setup() {
  createCanvas(400, 400);
  background(220);
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(80, 300);
  connectBtn.mousePressed(connectBtnClick);

  bombtask= new BombTask();
  event = new BombEvent();
  serialtask = new SerialTask();

}

function draw() {
  background(100);
  bombtask.update(); // siempre actualizar
  serialtask.update();
  bombtask.display();


  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
  } else {
    connectBtn.html("Disconnect");
  }
}

class BombEvent {
  constructor(){
    this.value = null;
  }
  set(val){ this.value = val; }
  clear(){ this.value = null; }
  read() {return this.value; }
}


class SerialTask {
  update(){
    if(port.availableBytes() > 0){
      let dataRx = port.read(1);
      if(dataRx === 'A') event.set('A');
      else if(dataRx === 'B') event.set('B');
      else if(dataRx === 'S') event.set('S');
      else if(dataRx === 'T') event.set('T');
    }

    // Actualizar texto del botón según estado del puerto
    if (!port.opened()) connectBtn.html('Connect to micro:bit');
    else connectBtn.html('Disconnect');
  }
}


class BombTask {
  constructor(){
    this.PASSWORD = ['A','B','A'];
    this.key = [];
    this.count = 20;
    this.startTime = millis();
    this.state = 'CONFIG';
  }

 update()
{
    if(this.state === 'CONFIG'){
      if(event.read() === 'A'){
        event.clear();
        this.count = min(this.count + 1, 60);
      }
      else if(event.read() === 'B'){
        event.clear();
        this.count = max(this.count - 1, 10);
      }
      else if(event.read() === 'S'){
        event.clear();
        this.startTime = millis();
        this.state = 'ARMED';
      }
    }

    else if(this.state === 'ARMED'){
      if(millis() - this.startTime > 1000){
        this.count--;
        this.startTime = millis();
        if(this.count <= 0){
          this.state = 'EXPLODED';
        }
      }

      if(event.read() === 'A' || event.read() === 'B'){
        this.key.push(event.read());
        event.clear();
        if(this.key.length === this.PASSWORD.length){
          if(this.key.join('') === this.PASSWORD.join('')){
            this.state = 'CONFIG';
            this.count = 20;
          }
          this.key = [];
        }
      }
    }

    else if(this.state === 'EXPLODED'){
      if(event.read() === 'T'){
        event.clear();
        this.state = 'CONFIG';
        this.count = 20;
        this.startTime = millis();
      }
    }
  }
  display(){
    fill(255);
    textAlign(CENTER, CENTER);
    textSize(32);

    if(this.state === 'CONFIG'){
      text(`CONFIG\n${this.count} `, width/2, height/2);
    }
    else if(this.state === 'ARMED'){
      text(`ARMED\n${this.count} `, width/2, height/2);
    }
    else if(this.state === 'EXPLODED'){
      fill(255,0,0);
      text("EXPLODED", width/2, height/2);
      text("💀",width/2,height/3);
    }
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

function readPort(data){
  if(data=='A') bombtask.buttonA();
  else if(data=='B') bombtask.buttonB();
  else if(data=='S') bombtask.shake();
  else if(data=='T') bombtask.touch();
}
```

**Código para conectar al micro:bit**

```python
# Imports go at the top
from microbit import *

uart.init(baudrate=115200)
display.show(Image.SAD)

while True:
    display.show(Image.SAD)
    if button_a.was_pressed():
        uart.write('A')
        display.show(Image.ARROW_N)
        sleep(200)
    if button_b.was_pressed():
        uart.write('B')
        display.show(Image.ARROW_S)
        sleep(200)
    if accelerometer.was_gesture('shake'):
        uart.write('S')
        display.show(Image.SAD)
        sleep(200)
    if pin_logo.is_touched():
        uart.write('T')
        display.show(Image.HAPPY)
        sleep(200)
```
