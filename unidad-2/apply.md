# Unidad 2


## 🛠 Fase: Apply

### Actividad 04

Así se vería el diagrama de la bomba temporizadora 🫑

<img width="848" height="679" alt="image" src="https://github.com/user-attachments/assets/652e293e-a5da-420a-8761-65bc32080bdf" />

Este diagrama se separa de la siguiente forma:

**-Estados:** en este caso son configuración, armed y explode

**-Eventos:** estos dependen de los estados, pero pueden ser el tiempo, presionar un boton o agitar el dispositivo

**-Acciones:** También dependen del estado, pero serían el mostrar la cuenta regresiva y producir el sonido (además le agrege a configuración el ver una mariposa para identificar el estado actual)

### Atividad 05

El código es el siguiente: 🍱

``` python
from microbit import *
import utime

STATE_INIT = 0
STATE_CONFIGURACION = 1
STATE_ARMED=2
STATE_EXPLODE=3

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
    elif current_state==STATE_EXPLODE:
        display.clear()
        audio.play(Sound.HELLO)
        if pin_logo.is_touched():
            current_state=STATE_CONFIGURACION
```
Para este programa se podrían realizar los siguientes vectores de prueba:

-El primer vector de prueba fue iniciar el programa y sacudir el dispositivo, al ocurrir esto la idea es que empiece una cuenta regresiva y al final de esta cuenta suene como un arma, al comprobar este vector funcionó ☑️

-En el segundo vector cuando se explota la bomba la idea es que al presionar el botón touch vuelva al Estado de configuración. Este vector también funcionó ☑️

-Para el último vector en el estado de configuración le esté usando el botón b más de 10 veces para verificar que el número no llegara a ser menor de 10. Este vector también funcionó ☑️
