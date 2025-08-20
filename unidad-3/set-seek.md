# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 01

El código para esta actividad sería:

``` python
from microbit import *
import utime

class Semaforo:
    def __init__(self,columna, tR,tY,tG):
        self.col= columna
        self.tr= tR
        self.ty =tY
        self.tg= tG
        display.set_pixel(self.col,0,9)
        self.interval= self.tr
        self.starTime=utime.ticks_ms()

        self.state="waitInRed"
        
    def update(self): 
        if self.state == "waitInRed":
            if utime.ticks_diff(utime.ticks_ms(),self.starTime)>= self.interval:
                display.set_pixel(self.col,0,0)
                display.set_pixel(self.col,1,9)
                self.interval= self.ty 
                self.starTime=utime.ticks_ms()
                self.state="waitInYellow"
        if self.state == "waitInYellow":
            if utime.ticks_diff(utime.ticks_ms(),self.starTime)>= self.interval:
                display.set_pixel(self.col,1,0)
                display.set_pixel(self.col,2,9)
                self.interval= self.tg
                self.starTime=utime.ticks_ms()
                self.state="waitInGreen"
        if self.state == "waitInGreen":
            if utime.ticks_diff(utime.ticks_ms(),self.starTime)>= self.interval:
                display.set_pixel(self.col,2,0)
                display.set_pixel(self.col,0,9)
                self.interval= self.tr
                self.starTime=utime.ticks_ms()
                self.state="waitInRed"
           
            

semaforo1 = Semaforo(0,5000,2000,3000)
semaforo2 = Semaforo(2,3000,1000,2000)
semaforo3 = Semaforo(4,4000,3000,2000)

while True:
    semaforo1.update()
    semaforo2.update()
    semaforo3.update()
```

### Actividad 02

``` python
from microbit import *
import utime

STATE_INIT = 0
STATE_CONFIGURACION = 1
STATE_ARMED=2
STATE_EXPLODE=3
keyCount=0
PASSWORD=["A","B","A"]
keys=[" "]*len(PASSWORD)

current_state = STATE_INIT
ARMED_INTERVAL = 20000 
NUM=0
EXPLODE_INTERVAL=1000
start_time = 0
interval = 0

while True:
    if current_state == STATE_INIT:
        start_time = utime.ticks_ms()
        current_state = STATE_CONFIGURACION

    elif current_state == STATE_CONFIGURACION:
        display.show(Image.BUTTERFLY)
        if button_a.was_pressed():
            ARMED_INTERVAL += 1000
            current_state=STATE_CONFIGURACION

        if button_b.was_pressed():
            if ARMED_INTERVAL>1000:
                ARMED_INTERVAL -= 1000
                current_state=STATE_CONFIGURACION

        if accelerometer.was_gesture('shake'):
            start_time = utime.ticks_ms() 
            interval=ARMED_INTERVAL
            current_state= STATE_ARMED
    elif current_state == STATE_ARMED:
        if utime.ticks_diff(utime.ticks_ms(),start_time)>1000:
            display.show(str(NUM))
            start_time=utime.ticks_ms()
            NUM=int(ARMED_INTERVAL/1000)
            ARMED_INTERVAL-=1000
            if NUM>0:
                current_state=STATE_ARMED
            elif NUM<0:
                current_state= STATE_EXPLODE
        if button_a.was_pressed():
            keys[keyCount]="A"
            keyCount = keyCount+1
        if button_b.was_pressed():
             keys[keyCount]="B"
             keyCount = keyCount+1
        if keyCount==3:
            keyCount=0
            if keys==PASSWORD:
                NUM=20
                display.show(NUM,wait=False)
                current_state= STATE_CONFIGURACION
    elif current_state==STATE_EXPLODE:
        display.clear()
        audio.play(Sound.HELLO)
        if pin_logo.is_touched():
            current_state=STATE_CONFIGURACION
```

### Actividad 05

El diagrama de este código se ve de la siguiente manera: 🥣

<img width="702" height="688" alt="image" src="https://github.com/user-attachments/assets/b3a21ad1-9f36-40e5-a1d1-0f027dc91405" />

Ahora, para ver los vectores de prueba de los estados se hizo la siguiente tabla: 🧋

<img width="675" height="659" alt="image" src="https://github.com/user-attachments/assets/9e2585e7-8b26-4ffa-bddc-fa0c4bfafeca" />
<img width="674" height="354" alt="image" src="https://github.com/user-attachments/assets/136011ef-0ec3-4e15-87cc-c9555614653b" />
<img width="678" height="534" alt="image" src="https://github.com/user-attachments/assets/4cad7761-58f7-42a8-b36e-02e561981fd4" />

