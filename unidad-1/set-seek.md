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

En el ejemplo los Inputs serian los botones que hay en el micro:bit, el acelerometro y el serial que lo conecta con el computador y le informa cuando se presiona el botón de "send love", ya que estos captan las acciones del usuario. El proceso de este sistema sería el programa en Python, que es el encargado de mandar lo que se ve en las luces de la computadora y P5.js que recibe la información detectada por los sensores y botones. Finalmente el output sería las imagenes que se ven proyectadas en los LEDs, y el cambio de color y letra en la pantalla del computador, es decir, el resultado final que recibe el usuario.

### Actividad 04

Para esta actividad, después de experimentar un rato con las funciones, se llevo a cabo un programa que sigue con lineas que van desde las puntas del canvas la forma de un infinito, estas lineas cambian de colores de forma aleatoria y dejan cierto rastro en la pantalla. 
[Este es el enlace al programa](https://editor.p5js.org/CaroG1986/sketches/l4YYT0cZu).

``` javascript
function setup() {
  createCanvas(400, 400);
  noStroke();
  //frameRate(70);
}

function draw() {
  background(20, 20, 30, 50); 

  let x = 200 * cos(frameCount * 0.1) + 200;
  let y = 150 * sin(frameCount * 0.2) + 200;

   stroke (random(100,200),random(100,200),random(150,250),200);
  strokeWeight(3);
    line(x,y,0,0);
  
  let x1 = 200 * cos(frameCount * 0.1) + 200;
  let y1 = 150 * sin(frameCount * 0.2) + 200;

   stroke (random(100,200),random(100,200),random(150,250),200);
  strokeWeight(3);
    line(x1,y1,400,400);
  let x2 = 200 * cos(frameCount * 0.1) + 200;
  let y2 = 150 * sin(frameCount * 0.2) + 200;

   stroke (random(100,200),random(100,200),random(150,250),200);
  strokeWeight(3);
    line(x2,y2,0,400);
  
  let x3 = 200 * cos(frameCount * 0.1) + 200;
  let y3 = 150 * sin(frameCount * 0.2) + 200;

   stroke (random(100,200),random(100,200),random(150,250),200);
  strokeWeight(3);
    line(x3,y3,400,0);
}
```
Estas son imagenes del programa en ejecución

<img width="1461" height="573" alt="image" src="https://github.com/user-attachments/assets/ead2c8d8-7e12-4f15-b9fb-596230ececa1" />

<img width="498" height="501" alt="image" src="https://github.com/user-attachments/assets/2f22e95c-a4f9-4153-bfce-7cccc8a6f7d7" />

