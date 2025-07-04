<div align="center">
  <h1> 30 Dias De JavaScript: Promises</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

  <sub>Autor:
  <a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
  <small> Janeiro, 2020</small>
  </sub>
</div>

[<< Dia 17](../Dia_17_Web_Storages/Dia_17_Web_Storages.md) | [Dia 19 >>](../Dia_19_Closures/Dia_19_Closures.md)

![Trinta Dias De JavaScript](../images/banners/day_1_18.png)

- [Dia 18](#dia-18)
	- [Promise](#promise)
	- [Callbacks](#callbacks)
		- [Construtor de Promise](#construtor-de-promise)
	- [Fetch API](#fetch-api)
	- [Async e Await](#async-e-await)
	- [Exercícios](#exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 18

## Promise

Nós, humanos, damos ou recebemos uma promessa de fazer alguma atividade em algum momento. Se cumprirmos a promessa, deixamos os outros felizes, mas se não cumprirmos a promessa, isso pode levar ao descontentamento. Promise em JavaScript tem algo em comum com os exemplos acima.

Uma Promise é uma forma de lidar com operações assíncronas em JavaScript. Ela permite que manipuladores com o valor de sucesso eventual de uma ação assíncrona ou o motivo da falha. Isso permite que métodos assíncronos retornem valores como métodos síncronos: em vez de retornar imediatamente o valor final, o método assíncrono retorna uma promessa de fornecer o valor em algum momento no futuro.

Uma Promise está em um destes estados:

- pendente: estado inicial, nem cumprida nem rejeitada.
- cumprida: significa que a operação foi concluída com sucesso.
- rejeitada: significa que a operação falhou.

Uma promise pendente pode ser cumprida com um valor ou rejeitada com um motivo (erro). Quando qualquer uma dessas opções acontece, os manipuladores associados enfileirados pelo método then de uma promise são chamados. (Se a promise já foi cumprida ou rejeitada quando um manipulador correspondente é anexado, o manipulador será chamado, portanto, não há condição de corrida entre a conclusão de uma operação assíncrona e a anexação de seus manipuladores.)

Como os métodos Promise.prototype.then() e Promise.prototype.catch() retornam promises, eles podem ser encadeados.

## Callbacks

Para entender muito bem as promises, vamos primeiro entender os callbacks. Vejamos os seguintes callbacks. Nos blocos de código a seguir, você notará a diferença entre callback e promises.

- callback
  Vejamos uma função de callback que pode receber dois parâmetros. O primeiro parâmetro é err e o segundo é result. Se o parâmetro err for falso, não haverá erro, caso contrário, retornará um erro.

Neste caso, o err tem um valor e retornará o bloco err.

```js
//Callback
const doSomething = callback => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    callback('Não correu bem', skills)
  }, 2000)
}

const callback = (err, result) => {
  if (err) {
    return console.log(err)
  }
  return console.log(result)
}

doSomething(callback)
```

```sh
// após 2 segundos, ele imprimirá
Não correu bem
```

Neste caso, o err é falso e retornará o bloco else, que é o resultado.

```js
const doSomething = callback => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    callback(false, skills)
  }, 2000)
}

doSomething((err, result) => {
  if (err) {
    return console.log(err)
  }
  return console.log(result)
})
```

```sh
// após 2 segundos, ele imprimirá as skills
["HTML", "CSS", "JS"]
```

### Construtor de Promise

Podemos criar uma promise usando o construtor Promise. Podemos criar uma nova promise usando a palavra-chave `new` seguida da palavra `Promise` e seguida por parênteses. Dentro dos parênteses, ela recebe uma função de `callback`. A função de callback da promise tem dois parâmetros que são as funções _`resolve`_ e _`reject`_.

```js
// sintaxe
const promise = new Promise((resolve, reject) => {
  resolve('sucesso')
  reject('falha')
})
```

```js
// Promise
const doPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    if (skills.length > 0) {
      resolve(skills)
    } else {
      reject('Algo deu errado')
    }
  }, 2000)
})

doPromise
  .then(result => {
    console.log(result)
  })
  .catch(error => console.log(error))
```

```sh
["HTML", "CSS", "JS"]
```

A promise acima foi resolvida com resolve.
Vejamos outro exemplo quando a promise é resolvida com reject.

```js
// Promise
const doPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const skills = ['HTML', 'CSS', 'JS']
    if (skills.includes('Node')) {
      resolve('desenvolvedor fullstack')
    } else {
      reject('Algo deu errado')
    }
  }, 2000)
})

doPromise
  .then(result => {
    console.log(result)
  })
  .catch(error => console.error(error))
```

```sh
Algo deu errado
```

## Fetch API

A Fetch API fornece uma interface para buscar recursos (inclusive pela rede). Parecerá familiar para quem já usou XMLHttpRequest, mas a nova API fornece um conjunto de recursos mais poderoso e flexível. Neste desafio, usaremos fetch para solicitar URLs e APIs. Além disso, vejamos um caso de uso de demonstração de promises no acesso a recursos de rede usando a API fetch.

```js
const url = 'https://restcountries.com/v2/all' // api de países
fetch(url)
  .then(response => response.json()) // acessando os dados da API como JSON
  .then(data => {
    // obtendo os dados
    console.log(data)
  })
  .catch(error => console.error(error)) // tratando erro se algo der errado
```

## Async e Await

Async e await é uma forma elegante de lidar com promises. É fácil de entender e limpo de escrever.

```js
const square = async function (n) {
  return n * n
}

square(2)
```

```sh
Promise {<resolved>: 4}
```

A palavra _async_ na frente de uma função significa que essa função retornará uma promise. A função square acima, em vez de um valor, retorna uma promise.

Como acessamos o valor da promise? Para acessar o valor da promise, usaremos a palavra-chave _await_.

```js
const square = async function (n) {
  return n * n
}
const value = await square(2)
console.log(value)
```

```sh
4
```

Agora, como você pode ver no exemplo acima, escrever async na frente de uma função cria uma promise e para obter o valor de uma promise usamos await. Async e await andam juntos, um não pode existir sem o outro.

Vamos buscar dados da API usando o método de promise e o método async e await.

- promise

```js
const url = 'https://restcountries.com/v2/all'
fetch(url)
  .then(response => response.json())
  .then(data => {
    console.log(data)
  })
  .catch(error => console.error(error))
```

- async e await

```js
const fetchData = async () => {
  try {
    const response = await fetch(url)
    const countries = await response.json()
    console.log(countries)
  } catch (err) {
    console.error(err)
  }
}
console.log('===== async e await')
fetchData()
```

🌕 Você é real e cumpriu sua promessa e chegou ao dia 18. Mantenha sua promessa e resolva o desafio com resolve. Você está 18 passos à frente em seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e músculos.

## Exercícios

```js
const countriesAPI = 'https://restcountries.com/v2/all'
const catsAPI = 'https://api.thecatapi.com/v1/breeds'
```

### Exercícios: Nível 1

1. Leia a API de países usando fetch e imprima o nome do país, capital, idiomas, população e área.

### Exercícios: Nível 2

1. Imprima todos os nomes de gatos na variável catNames.

### Exercícios: Nível 3

1. Leia a API de gatos e encontre o peso médio do gato em unidade métrica.
2. Leia a API de países e descubra os 10 maiores países.
3. Leia a API de países e conte o número total de idiomas no mundo usados como oficiais.

🎉 PARABÉNS ! 🎉

[<< Dia 17](../Dia_17_Web_Storages/Dia_17_Web_Storages.md) | [Dia 19 >>](../Dia_19_Closures/Dia_19_Closures.md)
