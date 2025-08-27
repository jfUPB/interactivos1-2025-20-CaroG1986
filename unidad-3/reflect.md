# Unidad 3


## 🤔 Fase: Reflect

### Actividad 08

**Parte 1: recuperación de conocimiento (Retrieval Practice)**

*Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?*

Una máquina de estados es aquella que como su nombre indica funciona gracias al cambio de los estados. En este hay cuatro componentes, los cuales son: el estado como tal, un evento que es necesario para el cambio de estado, la transición y finalmente la acción que es el resultado o el output del estado.

*Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender varios eventos y tareas “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?*

La técnica de máquina de estado es util ya que facilita la administración de las tareas que debe ejecuta el programa. Los estados permiten que dependiendo de donde se encuentre reaccione de forma diferente a los eventos que recibe. Este es mejor que funciones como sleep porque estas pueden de alguna forma"descudrar" el programa ya que este solo espera untiempo y no tiene la capacidad de realizar otas tareas.

*Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial (por ejemplo, una combinación de botones o un comando serial) mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?*

Para que esto sea posible se debería unir un evento en el estado de ARMED donde en el caso de que ocurra el evento que sea, reduzca el contador del tiempo y luego regrese de nuevo al mismo estado, y que después de se regrese muestre en la pantalla el nuevo valor del conteo.

*Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.*

Un vector de prueba es una revisión paso a paso del código, donde se revisa el estado inicial, un posible evento que genre una acción, la acción y el estado final, esto con el fin de comprobar su correcta ejecución.

**Parte 2: reflexión sobre tu proceso (Metacognición)**

*¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?*

En sí el hacer el dragrama no es complejo ya cuando se comprende como funciona el código y los estados, pero creo que lo más difícil para mi fue el conectar un programa conotro o cambiar el código de un lenguaje a otro ya que no hay muchas cosas de estos lenguajes que no sé o no entiendo y por miedo a que no funcione o que no se pueda hacer algo siento que me pierdo en lo que tengo que hacer. Es decir, entiendo en teoría pero me cuesta un poco en la práctica.

*Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?*

Pues uno de los errores fue que me equive en escritura, como en mayúsculas y así, pero el mayor error fue que siento que me falto poder mostrar algo en p5.js para comprobar el programa ya que como no alcance a terminar la clase pasada no estoy segura de su funcionalidad al pasarlo a micro:bit, además creo que no esta muy bien hecha la parte d ela conección con el puerto ya que use un código que hicimos anteriormente como inspiración pero no lo comprendi muy ben.

*El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?*

Para abordarlo primero cree la clase de la bomba y luego le fue añadiendo los estados necesarios y los eventos que estos necesitaban, se podría decir que si añadi funcionalidades poco a poco sin embargo fue más como que complete un estado y luego el siguiente, y después comprobaba y si algo estaba mal o no funcionaba intentaba corregirlo.

*Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?*

Pues además de una experiencia interactiva (porque este permite que después de ejecutarse una acción como presionar un botón se lleve a cabo una acción) creo que también podría aplicarse a proyectos como viedeojuegos donde también se espere que el jugador o el personaje cumpla con cierto evento para que avance el juego.

### Actividad 09

*Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?*

Creo que la que más me ayudo fue el hacer la bomba desde el diseño del diagrama hasta el programa como tal en la fase set and seek, siento que so fue lo que más me ayudó a comprender como funcionan las máquinas de estado.

*Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso? ¿Qué cambiarías o eliminarías?*

La última actividad fue lo que me pareció más confuso porque hay ciertas cosas que no pueden traducir de un programa a otro o que funcionan muy diferentes y muchas veces no era conciente de estas diferencias, por lo que senti que me perdi al hacer la fase apply.

*Empezar a hacer: ¿Qué te habría ayudado a entender mejor?*

Creo que el tener más espacio para preguntar sobre dudas, por que en la clase de apply no logre avanzar mucho, entonces el poder traer luego el código para poder revisarlo siento que sería más oportuno.

*Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa a diseñar y programar uno complejo? ¿Por qué?*

El analizar u  programa le doy un 3 porque aunque no diría que fue super fácil, una vez ya se entiende la lógica no es tan malo, pero programar un programa complejo le doy un 4, ya que hay partes que ya sabía por el analisis pero otras que sentia que estaba trabajando sin una base.

*Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?*

Mi mayor momento de frustación fue que me aparecian en un momento varias errores y al final fue un problema más de semántica que de lógica y por esto pense por mucho rato que tenia todo el código malo.
