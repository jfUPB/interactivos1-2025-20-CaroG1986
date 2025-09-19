
# Evidencias de la unidad 5

## Set: 💡

### **Actividad 01** 🧑‍🚀

**Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?** ⭐

El micro:bit se esta comunicando con el sketch de p5.js por medio del puerto USB, ya que el sketch en algunas lineas indica que esta leyendo la información en este puerto.

``` java script
function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}
```
Los datos que esta enviando el micro:bit son su posición, ya sea en X o en Y, y en caso de que se esten presionando los botones. Para el botón de A es necesario leer si lo esta presionado actualmente para que funcione el programa, en cambio el botón B se lee cuando este es liberado.

**¿Cómo es la estructura del protocolo ASCII usado?** ⭐

<a name="exp1"></a>

Básicamente los datos estan estructurados de forma que se separan por conjuntos por medio del salto de renglon, y entre el conjunto se dividen por comas "," esto para que se puede identificar que dato es el que se esta recibiendo.

>En el código se ve de esta forma:
>
>**PYTHON:**
>```Python
>data = "{},{},{},{}\n".format(xValue, yValue, aState,bState)
>```
**Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.** ⭐

``` java script
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
```
Esta parte del código se puede explicar de la siguiente forma:
>Para separar lineas de datos:
>``` java script
>  let data = port.readUntil("\n");
>```
Aquí usan el enter para identificar que apartir de ahí inicia una nueva linea
>Para separar los datos en un linea:
>``` java script
>let values = data.split(",");
>```
Este código es para usar las comas como separador de los datos que hay en una linea.
>``` java script
> if (values.length == 4) {
>          microBitX = int(values[0]) + windowWidth / 2;
>          microBitY = int(values[1]) + windowHeight / 2;
>          microBitAState = values[2].toLowerCase() === "true";
>          microBitBState = values[3].toLowerCase() === "true";
>```
Finalmente esta parte clasifica la información que llega en diferentes tipos de datos, esto permite identificar cuales son de posición y cuales se tratan de el uso d elos botones.

**¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?**

```java script
updateButtonStates(microBitAState, microBitBState);
```
En esta linea de aquí se ve como al ingresar los datos de los botones se actualiza el estado de los botones

```java script
function updateButtonStates(newAState, newBState) {
  // Generar eventos de keypressed
  if (newAState === true && prevmicroBitAState === false) {
    // create a new random color and line length
    lineModuleSize = random(50, 160);
    // remember click position
    clickPosX = microBitX;
    clickPosY = microBitY;
    print("A pressed");
```
Despúes en esta información se usa en esta función y se ejecuta un acción dependiendo del evento.

**Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.** ⭐
<img width="876" height="808" alt="image" src="https://github.com/user-attachments/assets/dd047036-564a-4812-a308-2dd28342eb39" />
<img width="877" height="812" alt="image" src="https://github.com/user-attachments/assets/32dc3bbc-498d-4075-a1d0-0952897b14de" />
<img width="876" height="809" alt="image" src="https://github.com/user-attachments/assets/f94490af-b2ac-4f96-8d89-acfee7533edb" />

## Seek: 🔎

### Actividad 02 🧑‍🚀

**Texto en la aplicación serial terminal**
> ¿Por qué se ve este resultado? ⭐
> 
> El resultado se ve así gracias al módulo struct, el cual empaqueta los datos en un formato binario, en este caso separandolo en dos enteros cortos y dos caracteres sin simbolo que representan lo que reciben los botones del micro:bit.
<img width="1028" height="749" alt="image" src="https://github.com/user-attachments/assets/2ccbc2de-e11b-49ab-8cb5-c31b5ef648b2" />

**Todo en HEX en la aplicación serial**
> 
> ¿Cómo está relacionado con esta línea de código? ⭐
> 
> En este se ve como los simbolos raros del código anterior se ven representados por ceros , los otros son caracteres donde se ve la información que se ve representada en el código binario.
<img width="1023" height="746" alt="image" src="https://github.com/user-attachments/assets/6948c9dc-4357-4e17-a7de-db41eca68cd2" />

>¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?⭐
>
> Una ventaja del formato binario es que al ser más corto sintetiza mejor la información por lo que supongo que podría ser más rápido que el otro formato, por otro lado una desventaja que le veo es que hace más complejo el visualizar lo que esta pasando con el código y que información entra por el puerto serial.

<img width="1008" height="734" alt="image" src="https://github.com/user-attachments/assets/fbea25ab-fb6e-4fe5-a8d6-2e4bba7c2956" />

> ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían? ⭐
> 
> Por mensaje se estan enviando 6 bytes, por lo que supongo que según ese formato dos de esos bytes deben representar espacios, y el resto deben representar la información siendo los 00s los simbolos extraños y el resto de bytes los demás números y/o letras.
> 
>  posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'? ⭐
> <img width="1007" height="733" alt="image" src="https://github.com/user-attachments/assets/33dea758-c78d-4ba1-84a9-78889931300b" />
<a name="exp4"></a>
>los primeros que se ven como dos cuadrados son números positivos y los segundos que son cuatro cuadrados son los números negativos. Esto logré verificarlo enviando valores conocidos desde el editor de Python para validar bien la lectura de esos datos.

<img width="999" height="731" alt="image" src="https://github.com/user-attachments/assets/ec1062f7-cd62-4d9e-a575-0a5ef0a09893" />
<a name="exp2"></a>

>¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario? ⭐
>
>Las principales diferencias entre los dos son que el binario es más corto que el otro pero es muy confuso, siendo estas caracteristicas sus ventajas y desventajas respectivamente. Por otro lado, el ASCII es un lenguaje mucho más claro y fácil de comprender, donde facilmente se podian diferenciar las coordenadas que se enviaban a traves del micro:bit y el true o false de los botones.
>Por otra parte es importante que esta diferencia en cuanto al largo o la cantidad de bytes que usa cada uno esta fuertemente relacionado con la eficiencia de estos.
>
>Es por esto y con algo relacionado a lo que investigué, que el formato binario se utiliza simplemente para dar instrucciones sencillas para la computadora sin necesidad que una persona pueda leerlas, mientras  que ASCII (que de hecho se llama American Standard Code for Information Interchange, que tenía la duda de porque se llamaba así) se toma como una aplicación de ese formato binario pero para codificar caracteres de texto lo que lo hace un nivel más alto ilegible para las personas, pero en el fondo sigue siendo una secuencia binaria.
>
>Por esto mismo, una desventaja del ASCII es su peso y la falta de efectividad que podía tener una computadora a la hora de traducir o leer dicho formato.

### Actividad 03 🧑‍🚀

 **Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.** ⭐

Esto es debido al cambio de formato, este ahora lee separando los datos por sus bytes, así que los primeros dos bytes representan el valor en x, los siguientes en y y los últimos dos los valores true o false de los botones A y B. Este es el formato que llamamos '>2h2B', donde se indican dos enteros cortos y dos sin signo.

**Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?** ⭐

El principal cambio que puedo observar es que en el anterior se daba la instrucción leer los hasta "/n" y que se separaran entre si con una coma, en cabio aquí, si no me equivoco, esta separandolos según su orden. También es cierto que ahora a diferencia de ejemplos anteriores se proporciona con antelación la cantidad de bytes que va atener cada parte del código, por lo que no es necesario ningún simbolo para separalos

<a name="exp3"></a>

>**CUANDO SE EJECUTA EL CÓDIGO**
<img width="938" height="721" alt="image" src="https://github.com/user-attachments/assets/96da6518-3eb7-4b06-9789-cea244e18ce5" />

**¿Qué ves en la consola? ¿Por qué crees que se produce este error?** ⭐

Supongo que este error se causó porque hay algún error al momento de leer los datos qué es están ingresando y que el programa en sí no entiende muy bien o es capaz de traducir la información que recibe. 

**Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves?** ⭐

Ahora la comunicación es mejor ya que se implementó la técnica del framing. Framing se traduce literalmente como enmarcado, y eso es literalmente lo que se busca hacer con este código es decir delimitarlo con un fin y un principio. En este caso lo que se está haciendo es indicar un header ( una cabeza o inicio, posicionado en el byte 0 ) y un checksum (el fin que en este caso es el módulo de la suma de los datos anteriores)

>**pero... ¿Porqué se hace así el checksum?**
>Bueno esto es para asegurarse que sin importar qué números estén sumando esté siempre sea un número entre 0 y 255. El módulo entonces es el resto de dividir por 256.
>
>--------------------------------------------------------------------------------------------------------------------------------------------------------------
>
>**Otros datos sobre el framing**
>
>👉El framing es un concepto que se extiende más allá de la comunicación serial, de hecho incluso de la programación. El framing se refiere a cualquier actividad con el objetivo de encuadrar o encasillar cierta información. Por ejemplo, en comunicación el framing de la información se refiere a manipulación de medios donde se suele omitir cierta información. También hay otros ejemplos relacionados con la programación y la tecnología, por ejemplo los frames de la animación de originan desde el mismo concepto y estos de hecho usan el tiempo como un método de separación.
>
>👉Relacionado con estos métodos de separación, de hecho se podría decir que hay varios ya que no solo es el tiempo ( como lo mencioné antes) o por UART ( que es el ejemplo que estamos trabajando actualmente, con un tamaño fijo), también se clasifican por carácteres o por patrones.

**¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js?** ⭐

Ahora la comunicación es más fácil entre los 2 programas ya que se enmarca hubo un inicio y un final para los datos. Lo cual puede hacer el programa más robusto pero también asegura una buena comunicación y manejo de los datos.

### Actividad 04 🧑‍🚀

**Primer intento** ⭐

``` java script
// P_2_1_3_04
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

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
function readSerialData() {
  // Acumula los bytes recibidos en el buffer
  let available = port.availableBytes();
  if (available > 0) {
    let newData = port.readBytes(available);
    serialBuffer = serialBuffer.concat(newData);
  }

  // Procesa el buffer mientras tenga al menos 8 bytes (tamaño de un paquete)
  while (serialBuffer.length >= 8) {
    // Busca el header (0xAA)
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift(); // Descarta bytes hasta encontrar el header
      continue;
    }

    // Si hay menos de 8 bytes, espera a que llegue el paquete completo
    if (serialBuffer.length < 8) break;

    // Extrae los 8 bytes del paquete
    let packet = serialBuffer.slice(0, 8);
    serialBuffer.splice(0, 8); // Elimina el paquete procesado del buffer

    // Separa datos y checksum
    let dataBytes = packet.slice(1, 7);
    let receivedChecksum = packet[7];
    // Calcula el checksum sumando los datos y aplicando módulo 256
    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

    if (computedChecksum !== receivedChecksum) {
      console.log("Checksum error in packet");
      continue; // Descarta el paquete si el checksum no es válido
    }

    // Si el paquete es válido, extrae los valores
    let buffer = new Uint8Array(dataBytes).buffer;
    let view = new DataView(buffer);
    microBitX = view.getInt16(0) + windowWidth / 2;
    microBitY = view.getInt16(2) + windowHeight / 2;
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;
    updateButtonStates(microBitAState, microBitBState);

  }
}

function draw() {
   if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
    microBitConnected = false;
  } else {
    microBitConnected = true;
    connectBtn.html("Disconnect");
 
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

- No estoy muy segura si este código funciona porque no he podido verificarlo en el micro:bit. Para esto quite la partes que ya no tenian sentido como leer hasta las "," o hasta "/n" porque ahora el puerto serial se comunica con un lenguaje diferente.
-  También reemplaze ciertas cosas con el código del ejemplo anterior pero aun así no se si funciona.

  <img width="1919" height="869" alt="image" src="https://github.com/user-attachments/assets/7a470c9a-edd7-4e74-90b5-9f5f7ca1855a" />

  -Efectivamente no funcionó, ni siquiera corrió por que dice que el createSerial no esta definido.


**Segundo intento** ⭐

```java script
// P_2_1_3_04
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

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

let serialBuffer=[];

"use strict";

var count = 0;
var tileCountX = 6;
var tileCountY = 6;

var drawMode = 1;

let port;
let connectBtn;
//let connectionInitialized = false;
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

function readSerialData() {
  // Acumula los bytes recibidos en el buffer
  let available = port.availableBytes();
  if (available > 0) {
    let newData = port.readBytes(available);
    serialBuffer = serialBuffer.concat(newData);
  }

  // Procesa el buffer mientras tenga al menos 8 bytes (tamaño de un paquete)
  while (serialBuffer.length >= 8) {
    // Busca el header (0xAA)
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift(); // Descarta bytes hasta encontrar el header
      continue;
    }

    // Si hay menos de 8 bytes, espera a que llegue el paquete completo
    if (serialBuffer.length < 8) break;

    // Extrae los 8 bytes del paquete
    let packet = serialBuffer.slice(0, 8);
    serialBuffer.splice(0, 8); // Elimina el paquete procesado del buffer

    // Separa datos y checksum
    let dataBytes = packet.slice(1, 7);
    let receivedChecksum = packet[7];
    // Calcula el checksum sumando los datos y aplicando módulo 256
    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

    if (computedChecksum !== receivedChecksum) {
      console.log("Checksum error in packet");
      continue; // Descarta el paquete si el checksum no es válido
    }

    // Si el paquete es válido, extrae los valores
    let buffer = new Uint8Array(dataBytes).buffer;
    let view = new DataView(buffer);
    microBitX = view.getInt16(0) + windowWidth / 2;
    microBitY = view.getInt16(2) + windowHeight / 2;
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;
    updateButtonStates(microBitAState, microBitBState);

  }
}

function draw() {
  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
    microBitConnected = false;
  } else {
    microBitConnected = true;
    connectBtn.html("Disconnect");
  }

  switch (appState) {
    case STATES.WAIT_MICROBIT_CONNECTION:
      if (microBitConnected === true) {
        print("Microbit ready to draw");
        noCursor();
        prevmicroBitAState = false;
        prevmicroBitBState = false;
        appState = STATES.RUNNING;
      }
      break;

    case STATES.RUNNING:
      if (microBitConnected === false) {
        print("Waiting microbit connection");
        cursor();
        appState = STATES.WAIT_MICROBIT_CONNECTION;
      }

      if (microBitAState === true) {
        let x = microBitX;
        let y = microBitY;

        if (keyIsPressed && keyCode === SHIFT) {
          if (abs(clickPosX - x) > abs(clickPosY - y)) {
            y = clickPosY;
          } else {
            x = clickPosX;
          }
        }

        clear();
        noFill();

        count = microBitX / 10 + 10;
        var para = microBitY / height;

        var tileWidth = width / tileCountX;
        var tileHeight = height / tileCountY;

        for (var gridY = 0; gridY <= tileCountY; gridY++) {
          for (var gridX = 0; gridX <= tileCountX; gridX++) {
            var posX = tileWidth * gridX + tileWidth / 2;
            var posY = tileHeight * gridY + tileHeight / 2;

            push();
            translate(posX, posY);

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
      break; // <-- CIERRE del case STATES.RUNNING
  } // <-- CIERRE del switch(appState)
} // <-- CIERRE de function draw()


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

- Este tampoco estoy segura si funciona pero según yo ya mejoró porque compare bien cada parte del código para ver exactamente que se cambio.

<img width="1919" height="863" alt="image" src="https://github.com/user-attachments/assets/081d75db-4ed2-4ed7-a015-a141f7b3c434" />

-Como se puede ver si corre y se conecta pero no aparece nada del programa, así que voy a revisar de nuevo

**Tercer Intento** ⭐

>Y final

[Este es el link](https://editor.p5js.org/CaroG1986/sketches/9IIE0WloA)

```java scrpt
let serialBuffer = [];

"use strict";

var count = 0;
var tileCountX = 6;
var tileCountY = 6;

var drawMode = 1;

let port;
let connectBtn;
let microBitConnected = false;

const STATES = {
  WAIT_MICROBIT_CONNECTION: "WAIT_MICROBIT_CONNECTION",
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
  } else {
    port.close();
  }
}

function updateButtonStates(newAState, newBState) {
  if (newAState === false && prevmicroBitAState === true) {
    print("A released");
    drawMode = 2;
  }

  if (newBState === false && prevmicroBitBState === true) {
    drawMode = 3;
    print("B released");
  }

  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}

function readSerialData() {
  let available = port.availableBytes();
  if (available > 0) {
    let newData = port.readBytes(available);
    serialBuffer = serialBuffer.concat(newData);
  }

  while (serialBuffer.length >= 8) {
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift();
      continue;
    }

    if (serialBuffer.length < 8) break;

    let packet = serialBuffer.slice(0, 8);
    serialBuffer.splice(0, 8);

    let dataBytes = packet.slice(1, 7);
    let receivedChecksum = packet[7];
    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

    if (computedChecksum !== receivedChecksum) {
      console.log("Checksum error in packet");
      continue;
    }

    let buffer = new Uint8Array(dataBytes).buffer;
    let view = new DataView(buffer);
    microBitX = view.getInt16(0) + windowWidth / 2;
    microBitY = view.getInt16(2) + windowHeight / 2;
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;
    updateButtonStates(microBitAState, microBitBState);
  }
}

function draw() {
  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
    microBitConnected = false;
  } else {
    microBitConnected = true;
    connectBtn.html("Disconnect");
  }

  switch (appState) {
    case STATES.WAIT_MICROBIT_CONNECTION:
      if (microBitConnected === true) {
        print("Microbit ready to draw");
        noCursor();
        prevmicroBitAState = false;
        prevmicroBitBState = false;
        appState = STATES.RUNNING;
      }
      break;

    case STATES.RUNNING:
      if (microBitConnected === false) {
        print("Waiting microbit connection");
        cursor();
        appState = STATES.WAIT_MICROBIT_CONNECTION;
      }

      // 🔹 Leer datos cada frame
      readSerialData();

      // 🔹 Generar arte siempre, aunque A no esté presionado
      clear();
      noFill();

      count = microBitX / 10 + 10;
      var para = microBitY / height;

      var tileWidth = width / tileCountX;
      var tileHeight = height / tileCountY;

      for (var gridY = 0; gridY <= tileCountY; gridY++) {
        for (var gridX = 0; gridX <= tileCountX; gridX++) {
          var posX = tileWidth * gridX + tileWidth / 2;
          var posY = tileHeight * gridY + tileHeight / 2;

          push();
          translate(posX, posY);

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

      break; // cierre case RUNNING
  } // cierre switch
} // cierre draw()

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
<img width="1918" height="871" alt="image" src="https://github.com/user-attachments/assets/23f1457e-e3a1-40e5-910b-d1b9d5baed0a" />
<img width="1919" height="872" alt="image" src="https://github.com/user-attachments/assets/48673733-7437-4848-858a-6bfa625bbe9d" />

-Lo logre (yeyyyyyy), resulta que en intento anterior nunca llame a la lectura del puerto en la función draw, por eso es que no me funcionaba.
-Ahora que ya puede ver su funcionamiento siento que si fluye mucho más rápido que cuando lo intentamos la vez pasada, siento que fluye más, supongo que por ser más eficiente.

### Autoevaluación 🧑‍🚀

**Mi nota propuesta: 4.45**

| **Criterio** | **Autoevaluación**    | **Justificación/evidencias** |
|:----------|:----------:|--------:|
| **Profundidad de indagación:**   | Excelente  | Siento que en esta unidad tuve la oportunidad de profundizar mucho en los temas propuestos, además de preguntarme cosas más allá, a comparación de las anteriores, por ejemplo en [esta explicación](#exp2) pude investigar más a fondo en que casos se usaban estos dos formatos y en  [esta parte](#exp3) investigue más a fondo el tipo de framing que estabamos usado para este experimento.|
| **Calidad de experimentación:**  | Logrado   | Para esta parte aunque no hice más experimentos creativos, si probe el programa de distintas formas para poder estudiar su comportamiento, por ejemplo en [este experimento](#exp4) cambie los valores directamente para saber que ocurriría.|
| **Análisis y reflexión:**        | Logrado     | Durante toda la bitacora estuve proporcionando evidencia de mis experimentos y descomponiendo el código por partes para una mejor comprensión, como en [el primer experimento](#exp1), además tambíen analize como el framing apesar de ser más robusto es til e importante para una comunicación guiada y mejorada. |
| **Apropiación y Articulación de Conceptos:**  | Logrado    | En esta unidad me asegure de descompener las partes que podría no entender y traducirlas a mi propio "idioma", además en [este segmento](#exp3) también revise que otros usos y posibilidades tiene el framing en ambitos de mi interes, como la animación |

