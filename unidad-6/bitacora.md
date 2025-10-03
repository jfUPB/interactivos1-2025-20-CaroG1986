
# Evidencias de la unidad 6

## Actividad 01 🍒

**¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?** 🌸

Al momento de ejecutar npm install apareció lo siguiente 
<img width="738" height="441" alt="image" src="https://github.com/user-attachments/assets/ae6f4daa-3a08-4f61-84c8-813dc36e87cf" />

Que supongo que se encarga de instalar lo que esta dentro del repositorio descargado 

**¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?** 🌸
<img width="734" height="164" alt="image" src="https://github.com/user-attachments/assets/1022a849-c2cc-442c-86c6-3d3c40949ca7" />

Supongo que este mensaje significa que se esta creando una forma de testear el programa con un server de java script, y que este server se puede ver en el enlace que se da para el programa.

**Describe lo que ves inicialmente en page1 y page2 en tu navegador.** 🌸

<img width="1447" height="749" alt="image" src="https://github.com/user-attachments/assets/78071be5-e430-42ad-a472-08e15ceb6d8b" />

Al abrir las paginas lo primero que me apareció fueron esos circulos conectados por una linea que al moverse la conección entre los dos continuaba sin importar en que lugar de la página se encontraran ubicados.

**¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?** 🌸

<img width="743" height="447" alt="image" src="https://github.com/user-attachments/assets/2c400d63-3677-4f40-bb09-1332b1294742" />

Al momento de abrir estas páginas me aparecieron estos mensajes en el servidor, los cuales supongo que se componen de datos como cuantos clientes hay, su posición y tamaño, y si entre los "clientes" o páginas si hay una sincronización que permite ver la conección entre ellos.

**Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?** 🌸

Cuando se mueve una de las ventanas se puede ver como esta sigue la conexión con la otra página y en si visualmente el mayor cambio es que la linea que conecta ambos circulos cambia según donde esten. Ahora en la consolo del navegador se ve lo siguiente: 

<img width="1911" height="990" alt="image" src="https://github.com/user-attachments/assets/911372e4-8ddf-4634-bb1f-a407c2bb7fbc" />

Esto que se ve es el mismo código que se puede ver en el servidor de java script, y especificamente en la consola esta constantemente enviando mensajes sobre su estado de sincronización con la otra página, por ende si hay un cambio en la otra página esto se ve directamente en la consola de chrome.

## Actividad 02 🍒

**Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.** 🌸

Supongo que en el caso de que se corta la conexión a internet, por ejemplo cuando se va la señal o se va la luz, no habría como un puente de conexión entre el dispositivo que esté utilizando y la página o a la información a la que quisiera llegar.

**¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?** 🌸

Claro que hay muchas relaciones cliente servidor en la vida cotidiana, entre estas estan: 
- Pedir un paquete por internet donde el mensajero sería el servidor y el receptor sería el cliente.
- Cuando te atiende un cajero en un supermercado y él sería el encargado de brindar el servicio procesar la compra.
- Cuando se llama al servicio al cliente de una empresa y ellos te proporcionan la información que necesites.

**Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?** 🌸

https://www.youtube.com/watch?v=AZWJNXQAngM

- Protocolo: ahí se puede ver muy claramente que es el https://, que son las reglas estandar que usan los navegadores.
- Nombre del dominio: este básicamente es www.youtube.com, que es una plataforma de video online.
- Ruta: watch?v=AZWJNXQAngM, es la ruta, que es básicamente lo que permite saber que video es al que se esta llamando o buscando, en este caso la primera pelicula de equistria girls.

  Al momento de solo poner el nombre del dominio simplemente me lleva a la página oficial de youtube.

**Compara HTTP con los protocolos seriales que usaste.** 🌸

**¿Qué similitudes encuentras?** 🌸

Una similitud que encuetro es el hecho de que cada uno se estos formatos tiene cierto orden definido que es lo que le permite transmitir la información. Especialmente si lo comparo con cada protocolo individualmente creo que similitudes con ASCII es que es sencillo para las personas comprender cómo ingresar la información necesaria. 

**¿Qué diferencias clave ves?** 🌸

Creo que una diferencia clave que veo es que en los protocolos anteriores simplemente la información llegaba desde puerto serial y con los protocolos se traducía para el código que esté utilizando, sin embargo, en este caso se usa este protocolo para tener una relación tipo cliente servidor donde se solicita que se regrese la información necesaria. 

**¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?** 🌸

Sí, la verdad creo que es ser mucho más complejo ya que en los casos anteriores solo necesitaba pocos datos como la posición o sí se oprimía un botón, pero en este caso estamos hablando de un protocolo que conecta a un usuario con miles de bibliotecas con información, por lo que creo que este sistema si se revisa de una forma menos superficial nos debemos encontrar con un sistema engorroso.

**Piensa en una página web simple, como un formulario de login.** 🌸

- **¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?** 🌸

Supongo que esa parte sería básicamente la estructura que uno puede leer como por ejemplo el título del formulario o les puse las preguntas que hayan o la información que hayan los botones, es decir, los datos en general que tiene el formulario.

- **¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?** 🌸

Bueno como el CSS enfrenté el diseño o la identidad visual de una página web yo supondría que en un formulario sería por ejemplo el cómo se ven los cuadros con las preguntas, El tipo de letra, los colores que tenga el formulario, cómo se van a ver ciertos botones y las formas en general que va a usar la página. 

- **¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?** 🌸

El JavaScript lo asoció con el feedback qué se recibe ay ingresar cosas en la página, como por ejemplo el hecho de que al presionar un botón este cambie de color oh que te indiques y te falta rellenar alguna parte del formulario, además que lo que pasa cuando ingresas un dato o realizas alguna acción dentro de la página, es decir cómo el sistema está procesando las acciones del usuario. 

**Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.**

- **¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?**

La mayor banda que le veo es que el comportamiento del programa va a ser guiado completamente por las decisiones del usuario, ya que en caso de hacer una página donde llega una persona y está manipula lo que encuentre según sus necesidades no es útil hacer un bucle predecible porque el usuario en sí es impredecible, de hecho muchas veces que el usuario reta al programa, así que no se puede esperar que este siga el mismo patrón de eventos.

- **¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?**

Como expliqué en el ejemplo anterior no sería útil ya que era una página web la intención no es que una persona vea siempre lo mismo, sino que la página se adapte de acuerdo Asus necesidades. Por ejemplo, si una persona entra a YouTube no van a ver todos exactamente los mismos vídeos ni van a esperar las mismas recomendaciones, La idea de hecho es que sea diferente y que la experiencia sea personalizada.

**¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?**

Pues supongo que uno de los beneficios el motor es su rapidez, pero también Creo que porque es más sencillo para un programador en organizar bien el código si sabe que el programa que está creando y que el cliente va a ver tienen la misma conexión y el mismo lenguaje. Creo que con un lenguaje que unifique todo es más sencillo comprender a la final que está ocurriendo y en caso de errores estos cuáles son. Además por el lado del cliente creo que es útil para comprender cuáles eran las ideas y objetivos del programador en el código original.

**Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?**

La diferencia que encuentro entre ambos es que el método tradicional es más lento y menos efectivo en momentos en donde se necesita información en tiempo real. Algunos ejemplos que he visto con el sistema WebSocket o Socket.IO creo que son los tableros virtuales en los que se trabajan conjunto con una persona y se puede ver qué está haciendo esa persona en ese momento.

## Actividad 03 🍒

### Experimento 1 🍓

**Intenta acceder a http://localhost:3000/page1. ¿Funciona?** 🌸

No en este caso no funciona

<img width="1919" height="992" alt="image" src="https://github.com/user-attachments/assets/40453e0d-6ce2-4237-bd9f-c14750bcef32" />

**Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?**🌸

Ahora si funciona correctamente.

<img width="1917" height="994" alt="image" src="https://github.com/user-attachments/assets/0d110e1a-35c1-4e97-8168-384ff4369471" />

**¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas?** 🌸

Supongo que el servidor asignada a los clientes con unas URLS definidas, es por eso que deben tener el mismo nombre que se les asigna desde el código. Si no directamente eso es una dirección diferente.

### Experimento 2 🍓

**Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.** 🌸

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

**Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?** 🌸

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

**Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?** 🌸

```
User disconnected - ID: 47HrLcZseujET2khAAAB
```
Si este ID si coincide con el que anote del page1 anterioirmente.

**Cierra la pestaña de page2. Observa la terminal.**
```
User disconnected - ID: rg3N6Ag5Y0BJ8h4bAAAF
```
En este caso lo mismo, se puede ver el mismo ID de la page2.

### Experimiento 3 🍓

**Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?** 🌸
```
Received win1update from ID: G6NMUG-_nsI_rpahAAAB Data: { x: 146, y: 230, width: 569, height: 420 }
```
Básicamente los datos que se pueden ver estan relacionados con su posición y el tamaño de la ventana, que supongo es lo que permite a la otra ventana determinar una buena sincronia.

**Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?** 🌸
```
Received win2update from ID: QdJ5F5xcrp9cHUbgAAAD Data: { x: 1009, y: 132, width: 674, height: 645 }
```
Se registran los datos de posición y tamaño, pero ahora se refieren a la page2.

**Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.** 🌸

<img width="1395" height="807" alt="image" src="https://github.com/user-attachments/assets/6b58f1e7-d974-4ac1-a926-789a9f4de381" />

En este experimiento se ve como al cambiar esta parte del código, la primera página se desconecta por completo de la segunda, pero la segunda intenta continuar la conexión, supongo que esto es porque se corto la transmisión entre los dos clientes, entonces la page2 en realidad no sabe que la page1 esta desconectada, por lo que sigue con su tarea. 

### Experimiento 4 🍓

**Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando?** 🌸
```
Server is listening on http://localhost:3001
```
**Intenta abrir http://localhost:3000/page1. ¿Funciona?** 🌸

No, no funciona.

<img width="1911" height="991" alt="image" src="https://github.com/user-attachments/assets/1376dde6-ed35-4ca6-b4eb-ec997c742461" />

**Intenta abrir http://localhost:3001/page1. ¿Funciona?** 🌸

Ahora si.
 
<img width="1917" height="989" alt="image" src="https://github.com/user-attachments/assets/eb187f3b-293b-430d-9b92-42732cb18080" />

**¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.** 🌸

Esta variable en el código aparece como una constante, supongo que esto quiere decir que la función listen siempre se va a encargar de escuchar al mismo local host identificado por la variable port, es por esto que si se intenta conectarse a un local host con un nombre algo diferente ya no hay respuesta por parte del programa.

## Actividad 04 🍒

### Experimiento 1 🍓

**Refresca la página page2.html. Observa la consola del navegador. ¿Ves algún error relacionado con la conexión? ¿Qué indica?** 🌸

<img width="673" height="385" alt="image" src="https://github.com/user-attachments/assets/7f897305-3d76-4ccc-af44-8738cef0b240" />

Este error indica que la conexión fue denegada.

**Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores?** 🌸

<img width="680" height="356" alt="image" src="https://github.com/user-attachments/assets/a43327bc-0776-4943-b3e4-5eca6584d4a3" />

Aparece como un historial con que si hubo errores, sin embargo ya sale que hay conexión y sincronización. 

### Experimento 2 🍓 

<img width="1380" height="775" alt="image" src="https://github.com/user-attachments/assets/a3948d25-6ea3-4ffa-8f3f-9ed91bc7fd76" />

**¿Qué pasó? ¿Por qué?** 🌸

Se desconecto el cliente de la page1 .Esta parte esta dentro del método que revisa la posición de la ventana, al comentar esto es como si ya no se transmitieran los datos de la segunda página cuando esta cambia, es decir, no se acrualiza la información de su posición. 

### Experimento 3 🍓

Básicamente la idea de esta experimiento era demostrar que al mover la page2 se van a ver los datos de esta en la page1 y vicesversa. Eto con el fin de comprender mejor como funciona la conexión entre ambas páginas.

### Experimento 4 🍓

<img width="803" height="625" alt="image" src="https://github.com/user-attachments/assets/c6e8c8a9-eda3-4385-9385-89dee9813a68" />

**¿Qué puedes concluir y por qué?** 🌸

Con este mensaje se puede ver que al esta parte de la función checkWindowPosition si se esta utilizando y se activa con el movimeinto de la pestaña o el cambiar el tamaño de esta.

### Experimento 5 🍓

**Cambia el background(220) para que dependa de la distancia entre las ventanas. Puedes calcular la magnitud del resultingVector usando let distancia = resultingVector.mag(); y luego usa map() para convertir esa distancia a un valor de gris o color. background(map(distancia, 0, 1000, 255, 0)); (ajusta el rango 0-1000 según sea necesario).** 🌸

<img width="1728" height="703" alt="image" src="https://github.com/user-attachments/assets/2da540d3-6a19-4c24-a7b7-20dd6145ba3f" />

**Inventa otra modificación creativa.** 🌸

para esta modificación tome como inspiración a mi profesora de metodología, y sus historias el compromiso y no meterse con hombres casados. Consiste en que si estan muy juntos se casan y si los separas se divorcian. 

<img width="1136" height="517" alt="image" src="https://github.com/user-attachments/assets/4e3aeef7-e153-4873-b380-5bb2f2c18838" />
<img width="1322" height="531" alt="image" src="https://github.com/user-attachments/assets/95e559f2-b8df-4743-84a0-7affe9e23c75" />


## Actividad 5 🍒

**Explica tu idea y realiza algunos bocetos.** 🌸

Para la fase de apply la idea que se me ocurrió fue qué programa mostrará dos corazones y dependiendo de qué tan cerca estuvieran uno del otro esos aumentaron o disminuyeran su tamaño. Además de esto cuando las dos páginas de los clientes están muy juntas La idea es que aparezca un texto que digan romance

<img width="958" height="538" alt="image" src="https://github.com/user-attachments/assets/cfe831f0-9a34-4fff-b8c4-137dbf15e553" />

<img width="958" height="537" alt="image" src="https://github.com/user-attachments/assets/e9adc090-aab8-4758-b632-c62bb833eb6d" />

**Implementa tu idea.** 🌸

Así se ven cuando esta muy separados

<img width="1896" height="762" alt="image" src="https://github.com/user-attachments/assets/23121978-1d9e-4594-a3b6-8f6148f2e539" />

Así se ven cuando estan más juntos

<img width="1245" height="757" alt="image" src="https://github.com/user-attachments/assets/d2f55d4b-0c65-44e6-a3a7-d489ed27ca62" />


**Incluye todos los códigos (servidor y clientes) en tu bitácora.** 🌸

Servidor 

``` java script
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
const path = require('path');
const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

let page1 = { x: 0, y: 0, width: 100, height: 100 };
let page2 = { x: 0, y: 0, width: 100, height: 100 };
let connectedClients = new Map();
let syncedClients = new Set();

app.use(express.static(path.join(__dirname, 'views')));

app.get('/page1', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page1.html'));
});

app.get('/page2', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page2.html'));
});

io.on('connection', (socket) => {
    console.log('A user connected - ID:', socket.id);
    connectedClients.set(socket.id, { page: null, synced: false });
    
    socket.on('disconnect', () => {
        console.log('User disconnected - ID:', socket.id);
        connectedClients.delete(socket.id);
        syncedClients.delete(socket.id);
        // Notificar a otros clientes que se perdió la sincronización
        socket.broadcast.emit('peerDisconnected');
    });

    socket.on('win1update', (window1, sendid) => {
        console.log('Received win1update from ID:', socket.id, 'Data:', window1);
        if (isValidWindowData(window1)) {
            page1 = window1;
            connectedClients.set(socket.id, { page: 'page1', synced: false });
            socket.broadcast.emit('getdata', { data: page1, from: 'page1' });
            checkAndNotifySyncStatus();
        }
    });

    socket.on('win2update', (window2, sendid) => {
        console.log('Received win2update from ID:', socket.id, 'Data:', window2);
        if (isValidWindowData(window2)) {
            page2 = window2;
            connectedClients.set(socket.id, { page: 'page2', synced: false });
            socket.broadcast.emit('getdata', { data: page2, from: 'page2' });
            checkAndNotifySyncStatus();
        }
    });

    socket.on('requestSync', () => {
        const clientInfo = connectedClients.get(socket.id);
        if (clientInfo?.page === 'page1') {
            socket.emit('getdata', { data: page2, from: 'page2' });
        } else if (clientInfo?.page === 'page2') {
            socket.emit('getdata', { data: page1, from: 'page1' });
        }
    });

    socket.on('confirmSync', () => {
        syncedClients.add(socket.id);
        const clientInfo = connectedClients.get(socket.id);
        if (clientInfo) {
            connectedClients.set(socket.id, { ...clientInfo, synced: true });
        }
        checkAndNotifySyncStatus();
    });    
});

function isValidWindowData(data) {
    return data && 
           typeof data.x === 'number' && 
           typeof data.y === 'number' && 
           typeof data.width === 'number' && data.width > 0 &&
           typeof data.height === 'number' && data.height > 0;
}

function checkAndNotifySyncStatus() {
    const page1Clients = Array.from(connectedClients.entries()).filter(([id, info]) => info.page === 'page1');
    const page2Clients = Array.from(connectedClients.entries()).filter(([id, info]) => info.page === 'page2');
    
    const bothPagesConnected = page1Clients.length > 0 && page2Clients.length > 0;
    const allClientsSynced = Array.from(connectedClients.keys()).every(id => syncedClients.has(id));
    const hasMinimumClients = connectedClients.size >= 2;

    console.log(`Debug - Connected clients: ${connectedClients.size}, Page1: ${page1Clients.length}, Page2: ${page2Clients.length}, Synced: ${syncedClients.size}`);

    
    if (bothPagesConnected && allClientsSynced && hasMinimumClients) {
        io.emit('fullySynced', true);
        console.log('All clients are fully synced');
    } else {
        io.emit('fullySynced', false);
        console.log(`Sync status: pages=${bothPagesConnected}, synced=${allClientsSynced}, clients=${connectedClients.size}`);
    }
}

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
});
```

Cliente page1

``` java script
let currentPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
}

let previousPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
};

let remotePageData = { x: 0, y: 0, width: 100, height: 100 };
let point1 = [currentPageData.width / 2, currentPageData.height / 2];
let socket;
let isConnected = false;
let hasRemoteData = false;
let isFullySynced = false;
let connectionTimeout;

function setup() {
    createCanvas(windowWidth, windowHeight);
    frameRate(60);
    socket = io();

    socket.on('connect', () => {
        console.log('Connected with ID:', socket.id);
        isConnected = true;
        socket.emit('win1update', currentPageData, socket.id);
        
        // Solicitar sincronización después de un breve delay
        setTimeout(() => {
            socket.emit('requestSync');
        }, 500);
    });

    socket.on('getdata', (response) => {
        if (response && response.data && isValidRemoteData(response.data)) {
            remotePageData = response.data;
            hasRemoteData = true;
            console.log('Received valid remote data:', remotePageData);
            socket.emit('confirmSync');
        }
    });

    socket.on('fullySynced', (synced) => {
        isFullySynced = synced;
        console.log('Sync status:', synced ? 'SYNCED' : 'NOT SYNCED');
    });

    socket.on('peerDisconnected', () => {
        hasRemoteData = false;
        isFullySynced = false;
        console.log('Peer disconnected, waiting for reconnection...');
    });

    socket.on('disconnect', () => {
        isConnected = false;
        hasRemoteData = false;
        isFullySynced = false;
        console.log('Disconnected from server');
    });
}

function isValidRemoteData(data) {
    return data && 
           typeof data.x === 'number' && 
           typeof data.y === 'number' && 
           typeof data.width === 'number' && data.width > 0 &&
           typeof data.height === 'number' && data.height > 0;
}

function checkWindowPosition() {
    currentPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
        currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height) {

        point1 = [currentPageData.width / 2, currentPageData.height / 2]
        socket.emit('win1update', currentPageData, socket.id);
        previousPageData = currentPageData;
    }
}


function draw() {
    background(220);
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);
    
    if (!isConnected) {
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }
    
    if (!hasRemoteData) {
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }
    
    if (!isFullySynced) {
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }

    // Solo dibujar cuando esté completamente sincronizado
    let scale = map(resultingVector.mag(), 0, 1000,2,0.1);
    console.log(`scale: ${scale}`);
    drawHeart(point1[0], point1[1],scale);
    checkWindowPosition();
    
  
    if (resultingVector.mag() < 500)
    {
            
        textSize(30);
        textAlign(CENTER, CENTER);
        noStroke();
        fill(0, 0, 0, 150);
        text("Romance", width / 2, 1*height / 2);
      
    }
   
    stroke(50);
    strokeWeight(20);
    //drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
    //line(point1[0], point1[1], resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
}

function showStatus(message, statusColor) {
    textSize(24);
    textAlign(CENTER, CENTER);
    noStroke();
    // Dibujar rectángulo de fondo para el texto
    fill(0, 0, 0, 150); // Negro semi-transparente
    rectMode(CENTER);
    let textW = textWidth(message) + 40;
    let textH = 40;
    rect(width / 2, 1*height / 6, textW, textH, 10);
    // Dibujar el texto
    fill(statusColor);
    text(message, width / 2, 1*height / 6);
}

function drawHeart(x, y,scale) {
    fill(255, 0, 0);
    noStroke();
  
    push();
    translate(x,y);



     // dos círculos arriba
  ellipse(- 40*scale, - 40*scale, 100*scale, 100*scale);
  ellipse(40*scale,- 40*scale, 100*scale, 100*scale);
  
  // triángulo abajo
  triangle(- 80*scale, - 10*scale, 80*scale,- 10*scale, 0, 80*scale);

    pop();

}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}
```

Page 2

``` java script
let currentPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight

}

let previousPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
};

let remotePageData = { x: 0, y: 0, width: 100, height: 100 };
let point2 = [currentPageData.width / 2, currentPageData.height / 2];
let socket;
let isConnected = false;
let hasRemoteData = false;
let isFullySynced = false;
let connectionTimeout;

function setup() {
    createCanvas(windowWidth, windowHeight);
    frameRate(60);
    socket = io();

    socket.on('connect', () => {
        console.log('Connected with ID:', socket.id);
        isConnected = true;
        socket.emit('win2update', currentPageData, socket.id);
        
        // Solicitar sincronización después de un breve delay
        setTimeout(() => {
            socket.emit('requestSync');
        }, 500);
    });

    socket.on('getdata', (response) => {
        if (response && response.data && isValidRemoteData(response.data)) {
            remotePageData = response.data;
            hasRemoteData = true;
            console.log('Received valid remote data:', remotePageData);
            socket.emit('confirmSync');
        }
    });

    socket.on('fullySynced', (synced) => {
        isFullySynced = synced;
        console.log('Sync status:', synced ? 'SYNCED' : 'NOT SYNCED');
    });

    socket.on('peerDisconnected', () => {
        hasRemoteData = false;
        isFullySynced = false;
        console.log('Peer disconnected, waiting for reconnection...');
    });

    socket.on('disconnect', () => {
        isConnected = false;
        hasRemoteData = false;
        isFullySynced = false;
        console.log('Disconnected from server');
    });
}

function isValidRemoteData(data) {
    return data && 
           typeof data.x === 'number' && 
           typeof data.y === 'number' && 
           typeof data.width === 'number' && data.width > 0 &&
           typeof data.height === 'number' && data.height > 0;
}

function checkWindowPosition() {
    currentPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (currentPageData.x !== previousPageData.x || currentPageData.y !== previousPageData.y || 
        currentPageData.width !== previousPageData.width || currentPageData.height !== previousPageData.height) {

        //console.log('In checkWindowPosition the if statament is true');

        point2 = [currentPageData.width / 2, currentPageData.height / 2]
        socket.emit('win2update', currentPageData, socket.id);
        
        previousPageData = currentPageData; 
    }
}


function draw() {

    //let distancia = resultingVector.mag();
    background(220);

    
    if (!isConnected) {
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }
    
    if (!hasRemoteData) {
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }
    
    if (!isFullySynced) {
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }
     let vector2 = createVector(remotePageData.x, remotePageData.y);
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);
    // Solo dibujar cuando esté completamente sincronizado

    let scale = map(resultingVector.mag(), 0, 1000,2,0.1);
    console.log(`scale: ${scale}`);

    drawHeart(point2[0], point2[1],scale);
    checkWindowPosition();
     if (resultingVector.mag() < 500)
    {
            
        textSize(30);
        textAlign(CENTER, CENTER);
        noStroke();
        fill(0, 0, 0, 150);
        text("Romance", width / 2, 1*height / 2);
      
    }
    stroke(50);
    strokeWeight(20);
    //drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
    //ine(point2[0], point2[1], resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
}

function showStatus(message, statusColor) {
    textSize(24);
    textAlign(CENTER, CENTER);
    noStroke();
    // Dibujar rectángulo de fondo para el texto
    fill(0, 0, 0, 150); // Negro semi-transparente
    rectMode(CENTER);
    let textW = textWidth(message) + 40;
    let textH = 40;
    rect(width / 2, 1*height / 6, textW, textH, 10);
    // Dibujar el texto
    fill(statusColor);
    text(message, width / 2, 1*height / 6);
}

function drawHeart(x, y,scale) {
    fill(255, 0, 0);
    noStroke();
  
    push();
    translate(x,y);



     // dos círculos arriba
     ellipse(- 40*scale, - 40*scale, 100*scale, 100*scale);
     ellipse(40*scale,- 40*scale, 100*scale, 100*scale);
  
      // triángulo abajo
      triangle(- 80*scale, - 10*scale, 80*scale,- 10*scale, 0, 80*scale);

    pop();
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}
```

## Autoevaluación 🌸

Mi nota es: 

| Actividad | Nota  | Justificación |
