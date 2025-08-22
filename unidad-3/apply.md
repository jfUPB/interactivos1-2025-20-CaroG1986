# Unidad 3


## 🛠 Fase: Apply

### Actividad 06

[Este es el link al programa](https://editor.p5js.org/CaroG1986/sketches/N7SY7VIPb)

>Para generar este código traduje el código de python casi que literal, sin embrago hay cosas que en python funcionan diferente por lo que en lugar de poner todo en un solo método hice más métodos para cuando se den los distintos casos. También se prodría con otras clases, sin embargo ese código es el de la bomba 3.0, por eso intente hacer todo en una sola clase.

``` java script
let port;
let connectBtn;
let connectionInitialized = false;
let bombTask;

let bombtask1;

class Bombtask {
  constructor(){
    this.PASSWORD = ['A','B','A'];
    this.key = new Array(this.PASSWORD.length).fill('');
    this.keyindex = 0;
    this.count = 20;
    this.startTime = millis();
    this.state = 'CONFIG';
    
  }
  update(){
    background(0);
    fill(255);
    textSize(48);
    textAlign(CENTER, CENTER);
    
    if (this.state === 'CONFIG') {
      text(this.count, width/2, height/2);
    }
    else if (this.state === 'ARMED'){
      if (millis()-this.starTime > 1000){
        this.starTime= millis();
        this.count --;
        if(this.count<=0){
           this.state= 'EXPLODED';
           }
      }
      text(this.count, width/2, height/2);
    }
    else if (this.state === 'EXPLODED') {
      text("Explotó", width/2, height/2);
    
    }
  }
  buttonA(){
    if(this.state==='CONFIG'){
       this.count=min(this.count+1,60)
       }
    else if(this.state==='ARMED'){
      this.key[this.keyindex]='A';
      this.keyindex++;
    }
  }
  buttonB(){
    if(this.state==='CONFIG'){
       this.count=min(this.count-1,60)
       }
    else if(this.state==='ARMED'){
      this.key[this.keyindex]='B';
      this.keyindex++;
    }
  }
  shake(){
    this.starTime=millis();
    this.state='ARMED';
  }
  touch(){
    if(state==='EXPLODED'){
      this.count=20;
      text(this.count, width/2, height/2);
      this.starTime= millis();
      this.state='CONFIG';
    }
  }
  checkpassword(){
    if(this.keyindex===this.PASSWORD.length){
      passIsOk=false;
      for(let i=0;i< this.PASSWORD.length;i++){
        if(passIsOk==true){
           this.count=20;
          text(this.count, width/2, height/2);
          this.keyindex = 0;
          this.state= 'CONFIG';
           }
      }
    }
    else {
      this.keyindex=0;
    }
  }
}

function setup() {
  createCanvas(400, 400);
  background(220);
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(80, 300);
  connectBtn.mousePressed(connectBtnClick);
  
  bombtask1= new Bombtask(0);
}

function draw() {
  background(220);
  if (port.opened() && !connectionInitialized) {
    port.clear();
    connectionInitialized = true;
    
    bombtask.update();
  }


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

function readPort(data){
  if(data=='A') bombtask1.buttonA();
  else if(data=='B') bombtask1.buttonB();
  else if(data=='S') bombtask1.shake();
  else if(data=='T') bombtask1.touch();
}
```

### Actividad 07

Código de micro:bit 

>Este código de aquí es para que el programa de python traduzca lo que viene del micro:bit al puerto y que lo pueda leer p5.js

``` python
from microbit import *
import utime

while True:
    if button_a.was_pressed():
        uart.write("A\n")
    if button_b.was_pressed():
        uart.write("B\n")
    if accelerometer.was_gesture("shake"):
        uart.write("S\n")
    if pin_logo.is_touched():
        uart.write("T\n")
    utime.sleep_ms(100)
```


