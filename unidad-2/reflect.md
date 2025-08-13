 # Unidad 2


## 🤔 Fase: Reflect

### Actividad 06

#### Parte 1

**Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?**

Una máquina de estados es aquella que se guía a través de estados de espera, es decir, espera que ocurra algo para que ocurra otra cosa. En estas maquínas hay 4 partes fundamentales: Los estados, que son los encargados de esperar que ocurra un evento; Eventos, que son sucesos que al activarse representan un cambio para el los estados. Las acciones que son el Output de los estados, es decir, lo que debe generar el programa. Las transiciones, cuando pasa de un estado a otro.

**Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?**

Esta técnica es util ya que otras funciones pueden generar un bloqueo en La continuidad del programa, por lo que si en un momento está activa la función sleep esto podría causar un un retraso en  el código 

**Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?**

Para agregar esta nueva funcionalidad en el diagrama lo que haría sería en el estado ARMED añadiría el evento en el que al agitarlo se reduzcan el intervalo de este estado a la mitad y después que regrese al estado.

**Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.**

Un vector de prueba es una herramienta que permite verificar sí las partes de la máquina de estados o cualquier programa en general si son funcionales y congruentes con la idea que se tiene del código.  Bien es por esto que para elaborar un vector de prueba primero se piensa lo que se espera en vez de cierta parte del código y después se hace la prueba, y finalmente comprueba si funciona o no.

#### Parte 2

**¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?**

Para mí la parte más desafiante fue elaborar el diagrama de estados porque en cierta forma no podía haber si estaba cometiendo algún error mientras lo hacía, en cambio cuando desarrollé el código podía hacer pruebas para verificar si era correcto. Es por esto que al final decidí usar lo que tenía en el diagrama convertirlo en código y después realizar correcciones a lo que tenía.

**Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?**

El error que encontré en mi programa fue que en la cuenta regresiva como usé una variable para guardar ahí los números que se iban a presentar en los leds, pero hacía la suma y la resta en el intervalo, lo que se veía en la pantalla eran a veces números negativos. Sin embargo, el pensar en cómo estaba estructurado el estado me hizo darme cuenta de que esta variable estaba mal representada y que era necesario corregirlo según la lógica del programa.

**El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?**

Sí principalmente lo que hice en primera instancia fue verificar que si hubiera cambio en los estados para allá después agregar bien los eventos y las acciones que necesitaba que cada uno de estos hiciera. Es por eso que primero verifiqué la parte de que pasara de configuración a ARMED y que y se da la cuenta regresiva, ya después elaboré él estado EXPLODE las acciones que este conlleva y el evento que lo regresa al estado de configuración.

**Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?**

Yo creo que una máquina estados podría ser implementada para proyectos cómo la elaboración de videojuegos en la cual sí necesite de la verificación de ciertos eventos para que ocurran ciertas acciones, como por ejemplo qué pase un tiempo o que se oprima alguna tecla.

### Actividad 07

**Bitácora de Sara Ruíz Arboleda:**

**- ACTIVIDAD 04:** El diagrama en términos generales está bien sin embargo lo único que cambiaría sería la parte del estado ARMED en el momento en el que o sea de la cuenta regresiva ya que no se comprende muy bien el que al pasar 1 segundo vuelva al mismo estado para que se vea el conteo.

**- ACTIVIDAD 05:** Creo que su código está muy bien y cumple con lo que pedía el programa, además me gusta que su reflexión sobre el problema y los posibles errores que pueda ser visibles en el vector de prueba sea tan cercana y fa facíl de comprender.

> Creo que algo que siempre queda por resaltar de la bitácora de mi compañera es que ya comprende muy bien el lenguaje Markdown que usa github y es por esto que sus trabajos siempre están muy organizados.

### Acitidad 08

**Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?**

Partido que me ayudó más para comprender cómo funciona la máquina de estado fue la actividad 3 ya que el poder ver paso por paso cómo se elaboran esas máquinas fue muy útil para mejorar mi comprensión.

**Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso, innecesariamente complicado o que aportó poco a tu aprendizaje? ¿Qué cambiarías o eliminarías?**

No ninguna me pareció innecesaria, sin embargo, la que me pareció más complicada fue la actividad 2 ya que al no haber hecho nunca una máquina de estados fue complejo intentar crear un programa basado en esta lógica.

**Empezar a hacer: ¿Qué te habría ayudado a entender mejor?**

Algo que podría haberme ayudado sería el tomar los códigos que ya habíamos hecho y después hace una retroalimentación sobre dicho código, para ver qué tan diferente era y se atenciones más creativas que habíamos tomado al respecto si eran funcionales o simplemente afectaban al programa. 

**Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa (Actividad 03) al diseño desde cero de uno complejo (Actividad 04 y 05)? ¿Por qué?**

Considero que la actividad 3 sería como un cuatro en dificultad ya que como no tenía previa experiencia realizando máquinas de estados fue muy complejo saber por dónde iniciar, aún más teniendo en cuenta que sé muy poco de lenguaje de Python. Sin embargo, creo que las otras 2 actividades fueron como un 2 en dificultad ya que lo más complejo fue comprobar que se cumpla todo lo que pide el programa y en realidad el código en sí no fue tan difícil cuando ya tenía más conocimiento.

**Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?**

Lo que más me gustó de esta actividad fue darme cuenta de que hay formas distintas de solucionar el mismo problema, es decir, crear el mismo código, y que muchas veces estas formas nuevas pueden ser más sencillas y mejores para la elaboración de un programa.

