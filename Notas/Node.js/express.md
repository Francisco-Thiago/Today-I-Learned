# Criando servidor com o Express

O express é um modulo do Node JS que surgiu para facilitar na criação de um servidor http.

Primeiro de tudo, baixe o express.

```js
npm i express
```

Ao baixar o express você precisa inseri-lo no seu código, o que é muito simples.

```js
const express = require('express');
const app = express();
```

O express retorna uma função, isso quer dizer que é necessário uma variável para recebê-la.

Agora só precisamos criar o nosso servidor.

```js
// Deve ser o último trecho de código que você colocar, tudo do servidor aparece antes disso.
app.listen(8090, () => {
    console.log("O servidor conectou!")
})
```

O número se refere a porta do servidor (o que poderia ser qualquer outro número) e a função nada mais é do que um simples callback que retorna uma mensagem no momento que o servidor for ativo.

Agora que temos um servidor, mas ele está completamente em branco e não serve pra muita coisa.

Você deve passar uma página pra ele, não é mesmo?

```js
app.get('/', (req, res) => {
    res.sendFile(__dirname+"/index.html");
})

// Você adiciona isso pra cada página que criar, lembrando que deve estar atrás do app.listen().
```

```js
__dirname //é uma variável global que mostra todo o caminho até o diretório atual. - c://users/thiago/Documents/Node
```

O get vai criar um caminho (nesse caso '/' mas poderia ser '/home', '/blog', '/sobre' ou qualquer outra coisa) e vai receber uma função callback com dois parâmetros, o primeiro se chama request que recebe as informações do cliente e o segundo response que envia informações pro cliente.

Qualquer dado do cliente que queiramos saber está relacionado ao `req` e qualquer coisa que queremos retornar de pedido está relacionado ao `res`. 

No nosso trechinho de código nós retornamos pro cliente uma página html chamada "index.html" toda vez que ele acessa o nosso servidor sem especificar um caminho.

**Com isso você já sabe usar express.**

Parece até mentira, mas isso só mostra o quão simples express é. Claro ele tem muito mais funcionalidades do que isso, mas se você apenas queria montar um servidor local e montar páginas isso é tudo que você precisa.

# Parâmetros

Você pode receber informações através da URL do cliente, isso explica porque existe tantas URLs enormes por aí.

```
localhost:8090/:nome/:sobrenome
```

Esses `/:` são parâmetros, que são como variáveis comuns, você pode ter acesso a elas através do `req`, assim:

```js
// localhost:8090/Thiago/Vieira

app.get('/:nome/:sobrenome', (req, res) => {
    res.send(req.params.nome+" "+req.params.sobrenome)
}) // Reposta: Thiago Vieira
```

É como se você recebesse um objeto comum em JavaScript e apenas acessasse alguma de suas propriedades. É bem simples de utilizar.

Embora eu não tenha citado o `send()` você já deve ter notado que ele é utilizado para mandar mensagens ao servidor. O `send` só pode ser invocado uma vez e o texto por si só não tem nenhuma formatação.

> Fim (2022-01-23).
