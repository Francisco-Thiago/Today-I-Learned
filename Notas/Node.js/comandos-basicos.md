Revisão do curso de Node.js (rocketseat)

# O que é Node?

Ao contrário do que muitos podem pensar o node não se trata de nenhuma linguagem ou framework.

O Node.js é um Runtime Enviroment (ambiente de execução), criado original por Ryan Dhal com o objetivo de tornar os processos de requisições da web mais flexíveis.

Atualmente Ryan não tem mais Node.js como seu principal foco, seu último projeto mais bem sucedido foi o Dino.

O Node.js aproveita os recursos do JavaScript utilizando um poderoso compilador (o V8). Ele oferece funcionalidades que o JavaScript puro não ofereceria normalmente, além disso ele facilita o trabalho com códigos de terceiros com o seu maravilhoso `npm`.

# O que é assincronia.

O JavaScript não é uma linguagem completamente síncrona, ele é single-thread. 

Isso que nem todas as respostas do código são lineares. Se algum código pode parar a execução do código ele será colocado em uma lista de espera e só será executado quando o código tiver sido executado totalmente.

Por ter essa característica tão dinâmica ele acaba se tornando um pouco complexo se tratado da mesma forma de outras linguagens, por isso é importante estar ciente de suas peculiaridades.

O Node faz uso exarcebado da assincronia do JS, afinal é graças a essa característica do JS que o Node.js foi criado.

# Comandos básicos de Node.js

O node js pode ser executado no próprio `git bash`, algo que achei bem conveniente. Para começar a trabalhar com o node basta instalá-lo no site oficial e logo em seguida abrir um terminal no Visual Studio Code.

O Node possui suas variáveis globais e objetos que possuem suas propriedades. Se você já trabalhou com DOM em JavaScript você poderá entender facilmente como o Node.js funciona. 

O Node pode rodar qualquer arquivo JavaScript, basta colocar `node [nome-do-arquivo]` isso no seu terminal, nem mesmo é preciso que você coloque `.js` no final, pois o node entende automaticamente que o que você está passando é um arquivo JavaScript.

## Globals

Para ter acesso a todas as variáveis globais basta digitar globals dentro de um `console.log` e executá-lo no terminal.

```js

// Seu arquivo js (app.js)
console.log(global)

```

```js
// (imagine que aqui é seu terminal)

> node app
<ref *1> Object [global] {
  global: [Circular *1],
  clearInterval: [Function: clearInterval],
  clearTimeout: [Function: clearTimeout],
  setInterval: [Function: setInterval],
  setTimeout: [Function: setTimeout] {
    [Symbol(nodejs.util.promisify.custom)]: [Getter]
  },
  queueMicrotask: [Function: queueMicrotask],
  performance: Performance {
    nodeTiming: PerformanceNodeTiming {
      name: 'node',
      entryType: 'node',
      startTime: 0,
      duration: 41.65649998188019,
      nodeStart: 1.001099944114685,
      v8Start: 2.708899974822998,
      bootstrapComplete: 30.212000012397766,
      environment: 17.06029999256134,
      loopStart: -1,
      loopExit: -1,
      idleTime: 0
    },
    timeOrigin: 1642881425183.593
  },
  clearImmediate: [Function: clearImmediate],
  setImmediate: [Function: setImmediate] {
    [Symbol(nodejs.util.promisify.custom)]: [Getter]
  }
}
```

Códigos bizarros aparecerão na sua tela no momento que vocÊ fizer isso. Ele lhe mandará informações e apresentará recursos globais que você poderá ter acesso.

## Comandos

Os comandos apresentados na RocketSeat (pelo menos até o tópico 5) são: 

```js
__dirname // nome de todos os diretórios até o diretório atual
__filename // nome de todos os diretórios até o arquivo atual.
require('') // permite você acessar pacotes/módulos/recursos externos.
require('path').basename() // Exibe o último arquivo/diretório de um caminho.
module.expression = "Olá, Mundo!" // Permite você criar seus próprios módulos.
process // permite você ter acesso a todo e qualquer tipo de informação relacionado ao processo que está sendo executado.
process.argv // Mostra todos os argumentos/caminhos necessários para a ocorrência do processo.
process.exit() // Encerra um processo.
process.stdout.write() // Permite escrever no console, o mesmo que um console.log só que menos formatado, é necessário adiciona \n ao final de cada texto (ou o texto sumirá).
process.on('event', callback) // isso é como um evento do js comum, é um addEventListener.
process.stdin.on('data', () => "Olá") // 'data' é o nome do evento. Toda vez que um texto for recebido ele reagirá mandando um "Olá".
process.on('exit' () => "Adeus") // 'exit' é o nome do evento. Toda vez que um processo for encerrado ele reagirá mandando um "Adeus"
npm init // Inicia um projeto com recursos externos, isso cria um arquivo .json (um arquivo que armazena dados da aplicação).
npm i / npm install // Permite você baixar módulos externos. Se aplicado sozinho ele instala todos os recursos necessários pro funcionamento do projeto.
npm i -D // instalação de um recurso para ser usado apenas em Desenvolvimento, não necessário para o funcionamento normal do projeto.
npm i -g // instalação de um recurso sendo feita de forma global, é possível usar o recurso em qualquer projeto.
npm root -g // Mostra o caminho do diretório global, que armazena seus recursos globais.
npm uninstal // Permite você desinstalar os módulos que baixou.
npm uninstal [recurso] -g // Desinstalação de um recurso global.
npm -v // permite você ver a versão do seu npm. 
npm start // execução de um scrit nomeado como start (comando único)
npm run [sript] // o mesmo que 'node [script]', ele executa um script passado no arquivo .json.
npm outdated // Exibe as versões do seu pacote.
npm i [pacote]@1.5.1 // instala um pacote e após @ especifica a versão daquele pacote.
npm i [pacote]@latest // instala a última versão do seu pacote.
npm update // Atualiza as informações de tudo.

```

Uma série de comandos cheios de conceitos e detalhes. Com esses comandos encerramos os tópicos 1 ao 5.

## package.json, package-lock.json e node_modules

Um arquivo json armazena as informações referentes ao seu projeto. Ele é criado assim que você coloca `git init` no seu terminal. Ele tem informações como:

- Quem criou o projeto?
- Do que se trata o projeto?
- Qual o nome do projeto?

Perguntas básicas sobre o projeto como essas. Essas informações podem ser colocadas todas de uma vez com o comando `npm init -y` onde ele coloca apenas informações padrões ao projeto. As informações podem ser mudadas facilmente e vem no formato de um objeto comum em JavaScript.

```js
// Arquivo package.json
{
  "name": "nodejs",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

Ao baixar mais módulos ao seu projeto uma pasta chamado `package-lock.json` se torna muito importante, ele armazena as informações exatas de tudo que precisa ser ou não baixado, é um mapeamento de todas as suas instalações, por isso não é bom alterá-lo.

Outra pasta enorme surge ao instalar pacotes, o `node_modules`, nele estão todos os pacotes que são necessários para executar o seu projeto. Ele pode ser excluido e não é necessário colocá-lo no github. Esses arquivos são baixados automaticamente no momento que você digita `npm i` (por isso os .json são tão importantes).

## Best.me

No fim do tópico 5 criamos um pequeno app chamado Best.me.

```js
// Código do app

const questions = [
    "O que você fez hoje, seus planos deram certo?",
    "Quais são os seus planos para melhorar?",
    "O que você pretende fazer amanhã?"
]

const ask = (index = 0) => {
    process.stdout.write("\nPergunta: "+questions[index]+"\n\n")
}

const answers = []

ask(0)

process.stdin.on('data', data => {
    answers.push(data.toString().trim())
    if(answers.length < questions.length) {
        ask(answers.length);
    }else {
        process.exit();
    }
})

process.on('exit', () => {
    questions.forEach((elemento, index) => {
        console.log(`
            # Pergunta ${index + 1}: ${elemento}
            > ${answers[index]}
        `)
    })
})


```

Resumo do app: ele lhe faz três perguntas simples e ao responder três perguntas ele exibe todas as perguntas e repostas. Uma coisa interessante é que todo o process é assíncrono, se você colocar códigos na frente dele ele executará os da frente primeiro e só então ele executará o process.

> Fim (2022-01-22).