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
