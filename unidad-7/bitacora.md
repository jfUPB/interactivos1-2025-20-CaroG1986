
# Evidencias de la unidad 7

## Actividad 01 👰

**¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?** 🤵

https://k3nfwl9g-3000.use2.devtunnels.ms/mobile/

Yo creo que se debe usar este porque el servidor no esta conectandos dos páginas desde el mismo dispositivo, sino que busca conectar dos dispositivos diferentes   

**Describe brevemente qué hace npm install y npm start.**

npm install lo que hace es que intalar las dependencias del programa, es decir, básicamente las bibliotecas necesarias, mientras que npm start inicia el servidor que es lo que permite la conexión. 

**¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**

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

**Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?**

Sí funcionó la interacción sin problema y también descubrimos que si se llegara a conectar otro cliente pues en sí el programa tendría como cierto fallo o se volvería loco en cierta forma porque no sabría muy bien a dónde mandar el círculo. Por otro lado si hay un poco de retraso pero no es muy significativo y son sí mucho menos de un segundo. Supongo que este a diferencia del de computador va a tener cierto retraso porque no se trata del mismo dispositivo.

## Actividad 02 👰

**Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**

Dev tunnels es necesario en ese escenario porque está conectando el servidor local que está en mi dispositivo portátil con mi teléfono móvil. Este funciona conectando a través del internet ambos dispositivos, lo que permite que ahora no sea necesario conectar a través de la IP del computador o que ambos dispositivos deban tener la misma red de wi-fi, por lo que ahora simplemente usa el internet como un medio para dar esa intermediación entre ambos dispositivos.

**Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.**

Esa función es la encargada de dar las coordenadas respecto a la posición que esta tocando dentro del canvas en el dispositivo móvil y utiliza la variable threshold para que no se llene de mensajes Todo el tiempo que se haga algún movimiento pequeño sino que cuando sea algo más significativo y de esa forma que no se llene el puerto de mensajes innecesarios.

**Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?**

Las ventajas de usar este método de conexión es que permite una conexión más segura sin necesidad de tener la misma conexión wi-fi y funciona  incluso si los dispositivos siguen alguna clase de protección.sin embargo algo que funciona en este caso pero podría ver como desventaja es que sí o sí es necesario que ambos dispositivos estén conectados al internet.

**Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**

<img width="1715" height="836" alt="image" src="https://github.com/user-attachments/assets/f16136cf-ebce-496b-81e4-3a291c2c7e46" />
<img width="621" height="821" alt="image" src="https://github.com/user-attachments/assets/4329ebe7-94dc-4995-af98-dc59ad80d64a" />
<img width="402" height="574" alt="image" src="https://github.com/user-attachments/assets/27e18543-9e3c-4f3a-ae31-05c12ef8d3e4" />

## Actividad 03 👰‍♀️

**¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?**

