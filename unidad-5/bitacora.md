
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
> El resultado se ve así gracias al módulo struct, el cual empaqueta los datos en un formato binario, en este caso separandolo en dos enteros cortos y dos caracteres sin simbolo que representan lo que reciben los botones del micro:bit.
<img width="1028" height="749" alt="image" src="https://github.com/user-attachments/assets/2ccbc2de-e11b-49ab-8cb5-c31b5ef648b2" />
**Todo en HEX en la aplicación serial**
> ¿Cómo está relacionado con esta línea de código? ⭐
> En este se ve como los simbolos raros del código anterior se ven representados por ceros , los otros son caracteres donde se ve la información que se ve representada en el código binario.
<img width="1023" height="746" alt="image" src="https://github.com/user-attachments/assets/6948c9dc-4357-4e17-a7de-db41eca68cd2" />

>¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?⭐
> Una ventaja del formato binario es que al ser más corto sintetiza mejor la información por lo que supongo que podría ser más rápido que el otro formato, por otro lado una desventaje que le veo es que hace más complejo el visualizar lo que esta pasando con el código y que información entra por el puerto serial.

<img width="1008" height="734" alt="image" src="https://github.com/user-attachments/assets/fbea25ab-fb6e-4fe5-a8d6-2e4bba7c2956" />

> ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían? ⭐
> Por mensaje se estan enviando 6 bytes, por lo que supongo que según ese formato dos de esos bytes deben representar espacios, y el resto deben representar la información siendo los 00s los simbolos extraños y el resto de bytes los demás números y/o letras.
>  posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'? ⭐
> <img width="1007" height="733" alt="image" src="https://github.com/user-attachments/assets/33dea758-c78d-4ba1-84a9-78889931300b" />
>los primeros que se ven como dos cuadrados son números positivos y los segundos que son cuatro cuadrados son los números negativos.

<img width="999" height="731" alt="image" src="https://github.com/user-attachments/assets/ec1062f7-cd62-4d9e-a575-0a5ef0a09893" />

>¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario? ⭐
>Las principales diferencias entre los dos son que el binario es más corto que el otro pero es muy confuso, siendo estas caracteristicas sus ventajas y desventajas respectivamente. por otro lado, el ASCII es un lenguaje mucho más claro y fácil de comprender.

### Actividad 03

 **Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.** ⭐

Esto es debido al cambio de formato, este ahora lee separando los datos por sus bytes, así que los primeros dos bytes representan el valor en x, los siguientes en y y los últimos dos los valores true o false de los botones A y B.

**Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?** ⭐

El principal cambio que puedo observar es que en el anterior se daba la instrucción leer los hasta "/n" y que se separaran entre si con una coma, en cabio aquí, si no me equivoco, esta separandolos según su orden.

>**CUANDO SE EJECUTA EL CÓDIGO**
<img width="938" height="721" alt="image" src="https://github.com/user-attachments/assets/96da6518-3eb7-4b06-9789-cea244e18ce5" />

**¿Qué ves en la consola? ¿Por qué crees que se produce este error?** ⭐
