# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01

Este programa funciona primero creando la clase Pixel y estableciendo un constructor el cual sirve como referencia sobre los objetos que van a ser creados de esta clase. Es entonces qué Se llaman a 2 estados el primero es “Intit” Como un semi estado para llamar a los valores iniciales del objeto después está el estado “WaitTimeout” el cual llama primero a un píxel se espera cierto tiempo y luego llama a otro Pixel. Finalmente se crea un ciclo con while en el que se llaman a los 2 pixeles y la función “update”.

#### ¿Cuáles son los estados en el programa? 🦋

Los estados de este programa son "Init" Y "WaitTimeout", los cuales se espera que ocurra un evento.

#### ¿Cuáles son los eventos/inputs en el programa? 🐻

Los eventos o inputs de este programa serian el tiempo que se debe esperar para seguir las instrucciones.

#### ¿Cuáles son las acciones en el programa? 🐬

La acciones de este programa serian prender un LED, dejarlo por un intervalo y hacer lo mismo con el otro LED.

### Actividad 02

``` python
from microbit import *
import utime

class Pixel:
    def __init__(self,pixelX,pixelY,initState,interval):
        self.state = "Init"
        self.pixelX = pixelX
        self.pixelY = pixelY
        self.start =0
        self.pixelState = initState
        self.interval = interval

    def prende(self):
         if self.state == "Init":
            self.start =utime.ticks_ms()
            self.state == "Espera"
            self.pixelState = 9
            display.set_pixel(self.pixelX, self.pixelY,self.pixelState)
         elif self.state == "Espera":
            if utime.ticks_diff(utime.ticks_ms(),self.start) > self.interval:
                self.start = utime.ticks_ms()
                self.pixelState=9
                display.set_pixel(self.pixelX, self.pixelY,self.pixelState)
        
    def apaga(self): 
        if self.state == "Init":
            self.start =utime.ticks_ms()
            self.state == "Espera"
            self.pixelState=0
            display.set_pixel(self.pixelX, self.pixelY,self.pixelState)
        elif self.state == "Espera":
            if utime.ticks_diff(utime.ticks_ms(),self.start) > self.interval:
                self.start = utime.ticks_ms()
                self.pixelState=0
                display.set_pixel(self.pixelX, self.pixelY,self.pixelState)       
            
pixels=[
Pixel (2,0,0,500),
Pixel (2,1,0,500),
Pixel (2,2,0,500)
]

Actual=0
num_pix =len(pixels)
intervalo = 500
ultimo =utime.ticks_ms()

while True:
    now = utime.ticks_ms()
    if utime.ticks_diff(now, ultimo) > intervalo:
       pixels[Actual].apaga ()
       Actual=(Actual-1)%num_pix
       pixels[Actual].prende()
       ultimo =now
```

Este código se compone de la siguiente manera: 🐜

-Los estados= en esta caso serían init, que es el estado incial y Espera que se usa para que cuando un Led realize una acción este espere para poder realizar la siguiente.

-Los eventos= En este caso sería el tiempo que debe esperar para que se encienda el siguiente LED 

-Las acciones= En este programa las acciones sería, prender, esperar un momento y luego encender el proxímo LED.
