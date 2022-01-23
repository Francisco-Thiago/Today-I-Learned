# Disparar Eventos

Assim como no DOM, o node permite que você dispare eventos e é bem simples.

## Instanciar eventos.

```js
const { EventEmitter } = require('events');
console.log( EventEmitter );

// Configurações gerais dos eventos.

<ref *1> [Function: EventEmitter] {
  once: [AsyncFunction: once],
  on: [Function: on],
  getEventListeners: [Function: getEventListeners],
  EventEmitter: [Circular *1],
  usingDomains: false,
  captureRejectionSymbol: Symbol(nodejs.rejection),
  captureRejections: [Getter/Setter],
  errorMonitor: Symbol(events.errorMonitor),
  defaultMaxListeners: [Getter/Setter],
  setMaxListeners: [Function (anonymous)],
  init: [Function (anonymous)],
  listenerCount: [Function (anonymous)]
}

```

## on, once, emit

**Conceitos**
- O `on` diz que sempre que um evento for emitido o callback será executado.
- O `once` diz que o evento só pode ser emitido uma vez.
- O `emit` executa um evento e possibilita passar argumentos.

## Executando e emitindo eventos.

```js
const { EventEmitter } = require('events');
const ev = new EventEmitter(); // Necessário instanciar para usar eventos.

ev.on('saySomething', (message = "Nada") => {
    console.log("Sua mensagem foi: ")
}) // Criando um evento chamado saySomething.

ev.emit('saySomething', "argumento-da-função-callback") //Emitindo o evento.

//Retorna: Sua mensagem foi: argumento-da-função-callback

```

# Intervalos de tempo.

Você pode fazer funções aparecerem só depois de um determinado tempo com 

```js
setTimeout(callback, tempo em milisegundos) // A função será executada depois do tempo especificado.
setInterval(callback, tempo em milisegundos) // A função será executada a cada quantidade de tempo especificada.
```

Você pode parar essas duas funções com: 

```js
clearTimeout() // Para um setTimeout
clearInterval() // Para um setInterval
```

Essas funções só valem a pena se estiverem dentro de outras funções ou de um setTimeout, caso contrário elas pararão imediatamente o setInterval/setTimout.

```js
const timer = setTimeout(sayMyName, 5000) 
process.stdin.on('data', () =>{
    clearTimeout(time);
}) // Quando um dado for inserido o timer será interrompido, se for inserido antes de 5 segundos a função "sayMyName" não será executada.

// no caso de usar o clear você precisa salvar o set dentro de uma variavel. 

setInterval(sayMyName, 1000) // Executa a função a cada segundo.

setTimeout(clearInterval, 5000) // Depois de cinco segundos o intervalo será parado.

```

> Fim (2022-01-23).
