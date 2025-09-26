
# Evidencias de la unidad 6

## Actividad 01

**¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?**

Al momento de ejecutar npm install apareció lo siguiente 
<img width="738" height="441" alt="image" src="https://github.com/user-attachments/assets/ae6f4daa-3a08-4f61-84c8-813dc36e87cf" />

Que supongo que se encarga de instalar lo que esta dentro del repositorio descargado 

**¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?**
<img width="734" height="164" alt="image" src="https://github.com/user-attachments/assets/1022a849-c2cc-442c-86c6-3d3c40949ca7" />

Supongo que este mensaje significa que se esta creando una forma de testear el programa con un server de java script, y que este server se puede ver en el enlace que se da para el programa.

**Describe lo que ves inicialmente en page1 y page2 en tu navegador.**

<img width="1447" height="749" alt="image" src="https://github.com/user-attachments/assets/78071be5-e430-42ad-a472-08e15ceb6d8b" />

Al abrir las paginas lo primero que me apareció fueron esos circulos conectados por una linea que al moverse la conección entre los dos continuaba sin importar en que lugar de la página se encontraran ubicados.

**¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?**

<img width="743" height="447" alt="image" src="https://github.com/user-attachments/assets/2c400d63-3677-4f40-bb09-1332b1294742" />

Al momento de abrir estas páginas me aparecieron estos mensajes en el servidor, los cuales supongo que se componen de datos como cuantos clientes hay, su posición y tamaño, y si entre los "clientes" o páginas si hay una sincronización que permite ver la conección entre ellos.

**Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?**

Cuando se mueve una de las ventanas se puede ver como esta sigue la conexión con la otra página y en si visualmente el mayor cambio es que la linea que conecta ambos circulos cambia según donde esten. Ahora en la consolo del navegador se ve lo siguiente: 

<img width="1911" height="990" alt="image" src="https://github.com/user-attachments/assets/911372e4-8ddf-4634-bb1f-a407c2bb7fbc" />

Esto que se ve es el mismo código que se puede ver en el servidor de java script, y especificamente en la consola esta constantemente enviando mensajes sobre su estado de sincronización con la otra página, por ende si hay un cambio en la otra página esto se ve directamente en la consola de chrome.

## Actividad 02

**Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.**

**¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?**

**Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?** 

**Compara HTTP con los protocolos seriales que usaste.**

**¿Qué similitudes encuentras?**

Una similitud que encuetro es el hecho de que cada uno se estos formatos tiene 

**¿Qué diferencias clave ves?**

**¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?**

**Piensa en una página web simple, como un formulario de login.**

- **¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?**
- **¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?**
- **¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?**

**Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.**

**¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?**

**¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?**

**¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?**

**Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?**

## Actividad 03

**Intenta acceder a http://localhost:3000/page1. ¿Funciona?**

<img width="1919" height="992" alt="image" src="https://github.com/user-attachments/assets/40453e0d-6ce2-4237-bd9f-c14750bcef32" />

**Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?**

<img width="1917" height="994" alt="image" src="https://github.com/user-attachments/assets/0d110e1a-35c1-4e97-8168-384ff4369471" />

**¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas?**

**Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.**

Este es el ID
```
ID: 47HrLcZseujET2khAAAB
```
Este es el mensaje que parece al abrir solo /page1
```
Debug - Connected clients: 1, Page1: 1, Page2: 0, Synced: 0
Sync status: pages=false, synced=false, clients=1
Debug - Connected clients: 1, Page1: 1, Page2: 0, Synced: 1
Sync status: pages=false, synced=true, clients=1
```

**Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?**

Este es el ID

```
 ID: rg3N6Ag5Y0BJ8h4bAAAF
```
Este es el mensaje que parece
```
Debug - Connected clients: 2, Page1: 1, Page2: 1, Synced: 1
Sync status: pages=true, synced=false, clients=2
Debug - Connected clients: 2, Page1: 1, Page2: 1, Synced: 2
All clients are fully synced
```

**Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?**

```
User disconnected - ID: 47HrLcZseujET2khAAAB
```
**Cierra la pestaña de page2. Observa la terminal.**
```
User disconnected - ID: rg3N6Ag5Y0BJ8h4bAAAF
```
**Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?**
```
Received win1update from ID: G6NMUG-_nsI_rpahAAAB Data: { x: 146, y: 230, width: 569, height: 420 }
```
**Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?**
```
Received win2update from ID: QdJ5F5xcrp9cHUbgAAAD Data: { x: 1009, y: 132, width: 674, height: 645 }
```
**Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.**

<img width="1395" height="807" alt="image" src="https://github.com/user-attachments/assets/6b58f1e7-d974-4ac1-a926-789a9f4de381" />

**Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando?**
```
Server is listening on http://localhost:3001
```
**Intenta abrir http://localhost:3000/page1. ¿Funciona?**

<img width="1911" height="991" alt="image" src="https://github.com/user-attachments/assets/1376dde6-ed35-4ca6-b4eb-ec997c742461" />

**Intenta abrir http://localhost:3001/page1. ¿Funciona?**

<img width="1917" height="989" alt="image" src="https://github.com/user-attachments/assets/eb187f3b-293b-430d-9b92-42732cb18080" />

**¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.**
