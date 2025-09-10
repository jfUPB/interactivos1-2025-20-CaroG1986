
# Evidencias de la unidad 5

## **Actividad 01**

**Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**

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

**¿Cómo es la estructura del protocolo ASCII usado?**

