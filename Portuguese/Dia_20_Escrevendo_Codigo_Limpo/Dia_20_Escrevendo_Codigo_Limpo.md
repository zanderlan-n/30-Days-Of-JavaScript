<div align="center">
  <h1> 30 Dias De JavaScript: Escrevendo Código Limpo</h1>
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

[<< Dia 19](../Dia_19_Closures/Dia_19_Closures.md) | [Dia 21 >>](../Dia_21_Document_Object_Model/Dia_21_Document_Object_Model.md)

![Trinta Dias De JavaScript](../images/banners/day_1_20.png)
- [Dia 20](#dia-20)
	- [Escrevendo código limpo](#escrevendo-código-limpo)
		- [Guia de Estilo JavaScript](#guia-de-estilo-javascript)
		- [Por que precisamos de um guia de estilo](#por-que-precisamos-de-um-guia-de-estilo)
			- [Guia de Estilo JavaScript do Airbnb](#guia-de-estilo-javascript-do-airbnb)
			- [Guia de Estilo JavaScript Padrão](#guia-de-estilo-javascript-padrão)
			- [Guia de Estilo JavaScript do Google](#guia-de-estilo-javascript-do-google)
		- [Convenções de Codificação JavaScript](#convenções-de-codificação-javascript)
			- [Convenções usadas em 30DiasDeJavaScript](#convenções-usadas-em-30diasdejavascript)
			- [Variáveis](#variáveis)
			- [Arrays](#arrays)
			- [Funções](#funções)
			- [Loops](#loops)
			- [Objetos](#objetos)
			- [Condicional](#condicional)
			- [Classes](#classes)

# Dia 20

## Escrevendo código limpo

### Guia de Estilo JavaScript

Um guia de estilo JavaScript é um conjunto de padrões que informa como o código JavaScript deve ser escrito e organizado. Nesta seção, falaremos sobre guias JavaScript e como escrever um código limpo.

JavaScript é uma linguagem de programação e, como a linguagem humana, possui sintaxe. A sintaxe do JavaScript deve ser escrita seguindo uma determinada diretriz de estilo por conveniência e simplicidade.

### Por que precisamos de um guia de estilo

Você está codificando sozinho há tanto tempo, mas agora parece que vai trabalhar em equipe. Não importa de forma alguma como você escreve seu código, desde que esteja funcionando; no entanto, quando você trabalha em uma equipe de 10, 20 ou mais desenvolvedores em um projeto e na mesma base de código, o código ficará confuso e difícil de gerenciar se não houver diretrizes a seguir.

Você pode desenvolver suas próprias diretrizes e convenções ou também pode adaptar diretrizes bem desenvolvidas. Vejamos as diretrizes mais comuns conhecidas.
Guias de Estilo JavaScript Mais Comuns

- Guia de Estilo JavaScript do Airbnb
- Guia de Estilo JavaScript Padrão
- Guia de Estilo JavaScript do Google

#### Guia de Estilo JavaScript do Airbnb

O Airbnb possui um dos guias de estilo JavaScript mais populares da internet. Ele cobre quase todos os aspectos do JavaScript e é adotado por muitos desenvolvedores e empresas. Você pode conferir o [guia de estilo do Airbnb](https://github.com/airbnb/javascript). Eu também recomendo experimentá-lo. O estilo deles é muito fácil de usar e simples de entender.

#### Guia de Estilo JavaScript Padrão

Esta diretriz não é tão popular quanto a do Airbnb, mas vale a pena dar uma olhada. Eles removeram o ponto e vírgula em seu [guia de estilo](https://standardjs.com/).

#### Guia de Estilo JavaScript do Google

Não direi muito sobre a diretriz do Google e não a usei; em vez disso, sugiro que você dê uma olhada neste [link](https://google.github.io/styleguide/jsguide.html).

### Convenções de Codificação JavaScript

Neste desafio também usamos as convenções e guias gerais de escrita de código JavaScript. As convenções de codificação são diretrizes de estilo para programação desenvolvidas por um indivíduo, uma equipe ou uma empresa.

As convenções de codificação ajudam:

- a escrever código limpo
- a melhorar a legibilidade do código
- a melhorar a reutilização e a capacidade de manutenção do código

As convenções de codificação incluem

- Regras de nomenclatura e declaração para variáveis
- Regras de nomenclatura e declaração para funções
- Regras para o uso de espaços em branco, indentação e comentários
- Práticas e princípios de programação

#### Convenções usadas em 30DiasDeJavaScript

Neste desafio, seguimos a convenção regular do JavaScript, mas também adicionei minha preferência de escrita.

- Usamos camelCase para variáveis e funções.
- Todos os nomes de variáveis começam com uma letra.
- Optamos por usar *const* para constantes, arrays, objetos e funções. Em vez de aspas duplas, optamos por usar aspas simples ou crase. Aspas simples estão se tornando tendência.
- Também removemos os pontos e vírgulas do nosso código, mas isso é uma questão de preferência pessoal.
- Espaço ao redor de operadores aritméticos, operadores de atribuição e após vírgula
- Função de seta em vez de declaração de função
- Retorno explícito em vez de retorno implícito se a função for de uma linha
- Sem vírgula final no último valor de um objeto
- Preferimos this +=, -=, *= /=, **= em vez da versão mais longa
- Quando usamos console.log(), é bom imprimir com uma string de tag para identificar de onde o console está vindo

#### Variáveis

```js

let firstName = 'Asabeneh'
let lastName = 'Yetayeh'
let country = 'Finlândia'
let city = 'Helsinki'

const PI = Math.PI
const gravity = 9.81
```

#### Arrays

Optamos por tornar os nomes dos arrays no plural

- names
- numbers
- countries
- languages
- skills
- fruits
- vegetables

```js
// arrays
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const numbers = [0, 3.14, 9.81, 37, 98.6, 100]
const countries = ['Finlândia', 'Dinamarca', 'Suécia', 'Noruega', 'Islândia']
const languages = ['Amárico', 'Árabe', 'Inglês', 'Francês', 'Espanhol']
const skills = ['HTML', 'CSS', 'JavaScript', 'React', 'Python']
const fruits = ['banana', 'laranja', 'manga', 'limão']
const vegetables = ['Tomate', 'Batata', 'Repolho', 'Cebola', 'Cenoura']
```

#### Funções

Até agora você está muito familiarizado com declaração de função, função de expressão, função de seta e função anônima. Neste desafio, tendemos a usar a função de seta em vez de outras funções. A função de seta não substitui outras funções. Além disso, as funções de seta e as declarações de função não são exatamente iguais. Portanto, você deve saber quando usar e quando não usar. Abordarei a diferença em detalhes em outras seções. Usaremos retorno explícito em vez de retorno implícito se a função for de uma linha.

```js
// função que retorna o nome completo de uma pessoa
const printFullName = (firstName, lastName) => firstName + ' ' + lastName

// função que calcula o quadrado de um número
const square = (n) => n * n

// uma função que gera cores hexa aleatórias
const hexaColor = () => {
  const str = '0123456789abcdef'
  let hexa = '#'
  let index
  for (let i = 0; i < 6; i++) {
    index = Math.floor(Math.random() * str.length)
    hexa += str[index]
  }
  return hexa
}

// uma função que mostra data e hora
const showDateTime = () => {
  const now = new Date()
  const year = now.getFullYear()
  const month = now.getMonth() + 1
  const date = now.getDate()
  let hours = now.getHours()
  let minutes = now.getMinutes()
  if (hours < 10) {
    hours = '0' + hours
  }
  if (minutes < 10) {
    minutes = '0' + minutes
  }

  const dateMonthYear = date + '.' + month + '.' + year
  const time = hours + ':' + minutes
  const fullTime = dateMonthYear + ' ' + time
  return fullTime
}
```

O `new Date().toLocaleString()` também pode ser usado para exibir a data e hora atuais. Os métodos `toLocaleString()` recebem argumentos diferentes. Você pode aprender mais sobre data e hora neste [link](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString).

#### Loops

Cobrimos muitos tipos de loops nestes desafios. O loop for regular, loop while, loop do while, loop for of, loop forEach e loop for in.
Vejamos como os usamos:

```js
for (let i = 0; i < n; i++){
    console.log()
}

// declarando uma variável de array
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']

// iterando um array usando loop for regular
let len = names.length;
for(let i = 0; i < len; i++){
    console.log(names[i].toUpperCase())
}


// iterando um array usando for of
for( const name of names) {
    console.log(name.toUpperCase())
}

// iterando array usando forEach
names.forEach((name) => name.toUpperCase())


const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finlândia',
  city: 'Helsinki',
  skills: ['HTML','CSS','JavaScript','React','Node','MongoDB','Python','D3.js'],
  isMarried: true
}
for(const key in person) {
    console.log(key)
}

```

#### Objetos

Declaramos objeto literal com *const*.

```js
// declarando objeto literal
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finlândia',
  city: 'Helsinki',
  skills: ['HTML','CSS','JavaScript','TypeScript', 'React','Node','MongoDB','Python','D3.js'],
  isMarried: true
}
// iterando através das chaves do objeto
for(const key in person) {
    console.log(key, person[key])
}

```

#### Condicional

 Vimos if, if else, if else if else, switch e operadores ternários em desafios anteriores.

 ```js
 // sintaxe
if (condition) {
  // esta parte do código é executada para condição verdadeira
} else {
  // esta parte do código é executada para condição falsa
}
 ```

 ```js
 // if else
let num = 3
if (num > 0) {
  console.log(`${num} é um número positivo`)
} else {
  console.log(`${num} é um número negativo`)
}
//  3 é um número positivo
 ```

 ```js
 // if else if else if else

let a = 0
if (a > 0) {
  console.log(`${a} é um número positivo`)
} else if (a < 0) {
  console.log(`${a} é um número negativo`)
} else if (a == 0) {
  console.log(`${a} é zero`)
} else {
  console.log(`${a} não é um número`)
}
 ```

 ```js
 // Switch Mais Exemplos
let dayUserInput = prompt('Que dia é hoje ?')
let day = dayUserInput.toLowerCase()

switch (day) {
  case 'segunda-feira':
    console.log('Hoje é Segunda-feira')
    break
  case 'terça-feira':
    console.log('Hoje é Terça-feira')
    break
  case 'quarta-feira':
    console.log('Hoje é Quarta-feira')
    break
  case 'quinta-feira':
    console.log('Hoje é Quinta-feira')
    break
  case 'sexta-feira':
    console.log('Hoje é Sexta-feira')
    break
  case 'sábado':
    console.log('Hoje é Sábado')
    break
  case 'domingo':
    console.log('Hoje é Domingo')
    break
  default:
    console.log('Não é um dia da semana.')
}
 ```

 ```js
 // ternário

 let isRaining = true
isRaining
  ? console.log('Você precisa de uma capa de chuva.')
  : console.log('Não precisa de capa de chuva.')
 ```

#### Classes

Declaramos classes com CamelCase que começa com letra maiúscula.

```js
// sintaxe
class NomeDaClasse {
    // código vai aqui
}
```

```js
// definindo classe
class Person {
  constructor(firstName, lastName) {
    console.log(this) // Verifique a saída daqui
    this.firstName = firstName
    this.lastName = lastName
  }
}

```

Qualquer que seja o guia de estilo que você seguir, seja consistente. Siga alguns paradigmas de programação e padrões de design. Lembre-se, se você não escrever seu código de uma certa ordem ou maneira, será difícil ler seu código. Então, faça um favor a si mesmo ou a alguém que vai ler seu código escrevendo um código legível.

🌕 Você é organizado. Agora, você sabe como escrever código limpo, para que qualquer pessoa que conheça a língua inglesa possa entender seu código. Você está sempre progredindo e está 20 passos à frente em seu caminho para a grandeza.

🎉 PARABÉNS ! 🎉

[<< Dia 19](../Dia_19_Closures/Dia_19_Closures.md) | [Dia 21 >>](../Dia_21_Document_Object_Model/Dia_21_Document_Object_Model.md)
