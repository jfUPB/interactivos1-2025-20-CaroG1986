# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 01

¿Qué es un sistema físico interactivo?  

Aquel que permite que el usuario interactue con la maquina para que las acciones físicas de este se vean reflejadas en el sistema. Dichos sistemas se dividen en partes que son: los datos de entrada ,o input, que son las instrucciones que entran al sistema, en este caso pueden ser recibidas por sensores como camáras, microfónos, etc. El sistema como tal que es el encargado de procesar estos datos para que despúes salga el output, o los datos de salida, es decir el resultado final que percibe el usuario.

¿Como podrías aplicar lo que has visto en tu perfil profesional?

Estos sistemas podrían aplicarse en mi perfil debido a que abren la puerta a pensar en la experiencia y participación que tiene el usuario dentro de algun programa de entretenimiento, además de dar pie a nuevas formas de crear dichas experiencias. En el caso específico de la animación, estos sistemas pueden convertir las animaciones en experiencias más dinamicas y permitir la implicación del expectador, por ejemplo, en un caso donde puedan controlar al personaje con sus movimientos o que cambie algo dependiendo de que capten los sensores.

### Actividad 02 

¿Qué es el diseño/arte generativo?

El diseño/arte generativo se refiere a cualquier práctica artistica en el que el artista utiliza un sistema, contribuyendo así a una obra de arte terminada o dando como resultado ella. Dicho sistema posee cierto grado de autonomía, ya sea un conjunto de reglas de lenguaje natural, un programa informático, una máquina u otra invención procedimental, su indepedencia logra crear diversidad de obras sin la necesidad de cambiar las instrucciones.

¿Cómo podrías aplicar lo que has visto en tu perfil profesional?

El arte generativo puede potenciar el impacto que tiene la animación covirtiendola en una experiencia más individual y unica, gracias a la autonomiá que tienen esta clase de proyectos, por lo que apesar de tener el mismo concepto general, la experiencia va a variar entre los observadores.

### Actividad 03

En el ejemplo los Inputs serian los botones que hay en el micro:bit, el acelerometro y el serial que lo conesta con el computador y le informa cuando se presiona el botón de send love. El proceso de este sistema sería el programa en Python, que es el encargado de mandar lo que se ve en las luces de la computadora y P5.js que recibe la información detectada por los sensores y botones. Finalmente el output sería las imagenes que se ven proyectadas en los LEDs, y el cambio de color y letra en la pantalla del computador.

### Actividad 04

Para este programa, después de experimentar un rato con las funciones, se llevo a cabo un programa que representa un faro proyectando su luz a través del canvas y bajo este se puede divisar una onda que actua como la onda del agua. [Este es el enlace](https://editor.p5js.org/CaroG1986/sketches/hF6SXlwUY) 

``` javascript
let lighthouse;

function preload() {
  lighthouse = loadImage("assets/faro1.jpg");
}
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background('rgba(255, 255, 255, 0.7)');
  image(lighthouse,100,180,200,250);
  stroke ('rgba(225, 223, 25, 0.7)');
  strokeWeight(20)
  let x = 1500 * sin(frameCount * 0.05) + random (100,200);
  let y= 40;
    line (x,y,200,250);
  stroke ('rgba(225, 223, 25, 0.7)');
  strokeWeight(20)
  let x1 = 1500 * sin(frameCount * -0.05) + random (100,200);
  let y1= 40;
    line (x1,y1,200,250);
  stroke('blue')
  strokeWeight(3)
  let amplitude = 10;
  let frequency = 0.05;
  let offsetY = 380;

  for (let x = 0; x < width; x += 2) {
    let angle = x * frequency + frameCount * 0.05;
    let y = offsetY + cos(angle) * amplitude;
    point(x, y);
  }
}
```

<img width="1388" height="537" alt="image" src="https://github.com/user-attachments/assets/a30125e2-55dd-4fed-b43a-91f12e95bb78" />

_Nota:Las luces y las ondas se mueven en el programa_

_Nota:Se puede encontrar la imagen utilizada en el siguiente [enlace](https://www.deviantart.com/dibujosparacolorear/art/Dibujos-para-Colorear-Faro-976226367)_
