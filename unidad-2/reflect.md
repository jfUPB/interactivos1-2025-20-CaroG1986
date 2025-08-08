# Unidad 2


## 🤔 Fase: Reflect

### Actividad 06

**Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?**

Una máquina de estados es aquella que se guía a través de estados de espera, es decir, espera que ocurra algo para que ocurra otra cosa. En estas maquínas hay 4 partes fundamentales: Los estados, que son los encargados de esperar que ocurra un evento; Eventos, que son sucesos que al activarse representan un cambio para el los estados. Las acciones que son el Output de los estados, es decir, lo que debe generar el programa. Las transiciones, cuando pasa de un estado a otro.

**Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?**

Esta técnica es util ya que puede 

**Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?**

