<div align="center">
  <h1> 30 Dias De JavaScript: Objetos</h1>
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

[<< Dia 7](../Dia_07_Funcoes/Dia_07_Funcoes.md) | [Dia 9 >>](../Dia_09_Funcoes_Ordem_Superior/dia_09_funcoes_ordem_superior.md)

![Trinta Dias De JavaScript](../../images/banners/day_1_8.png)

- [📔 Dia 8](#-dia-8)
	- [Escopo](#escopo)
		- [Objeto Global Window](#objeto-global-window)
		- [Escopo Global](#escopo-global)
		- [Escopo Local](#escopo-local)
	- [📔 Objeto](#-objeto)
		- [Criando um objeto vazio](#criando-um-objeto-vazio)
		- [Criando um objeto com valores](#criando-um-objeto-com-valores)
		- [Obtendo valores de um objeto](#obtendo-valores-de-um-objeto)
		- [Criando métodos de objetos](#criando-métodos-de-objetos)
		- [Definindo nova chave para um objeto](#definindo-nova-chave-para-um-objeto)
		- [Métodos de Objeto](#métodos-de-objeto)
			- [Obtendo chaves do objeto usando Object.keys()](#obtendo-chaves-do-objeto-usando-objectkeys)
			- [Obtendo valores do objeto usando Object.values()](#obtendo-valores-do-objeto-usando-objectvalues)
			- [Obtendo chaves e valores do objeto usando Object.entries()](#obtendo-chaves-e-valores-do-objeto-usando-objectentries)
			- [Verificando propriedades usando hasOwnProperty()](#verificando-propriedades-usando-hasownproperty)
	- [💻 Exercícios](#-exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# 📔 Dia 8

## Escopo

Variável é a parte fundamental na programação. Declaramos variáveis para armazenar diferentes tipos de dados. Para declarar uma variável, usamos as palavras-chave _var_, _let_ e _const_. Uma variável pode ser declarada em diferentes escopos. Nesta seção, veremos o escopo das variáveis, o escopo das variáveis quando usamos var ou let.
Os escopos das variáveis podem ser:

- Global
- Local

A variável pode ser declarada em escopo global ou local. Veremos tanto o escopo global quanto o local.
Qualquer coisa declarada sem let, var ou const tem escopo a nível global.

Vamos imaginar que temos um arquivo scope.js.

### Objeto Global Window

Sem usar console.log(), abra seu navegador e verifique, você verá o valor de a e b se escrever a ou b no navegador. Isso significa que a e b já estão disponíveis na janela.

```js
//scope.js
a = 'JavaScript' // declarando uma variável sem let ou const a torna disponível no objeto window e pode ser encontrada em qualquer lugar
b = 10 // esta é uma variável de escopo global e encontrada no objeto window
function letsLearnScope() {
  console.log(a, b)
  if (true) {
    console.log(a, b)
  }
}
console.log(a, b) // acessível
```

### Escopo Global

Uma variável declarada globalmente pode ser acessada em qualquer lugar no mesmo arquivo. Mas o termo global é relativo. Pode ser global para o arquivo ou pode ser global em relação a algum bloco de código.

```js
//scope.js
let a = 'JavaScript' // é um escopo global, será encontrado em qualquer lugar neste arquivo
let b = 10 // é um escopo global, será encontrado em qualquer lugar neste arquivo
function letsLearnScope() {
  console.log(a, b) // JavaScript 10, acessível
  if (true) {
    let a = 'Python'
    let b = 100
    console.log(a, b) // Python 100
  }
  console.log(a, b)
}
letsLearnScope()
console.log(a, b) // JavaScript 10, acessível
```

### Escopo Local

Uma variável declarada como local só pode ser acessada em determinado bloco de código.

- Escopo de Bloco
- Escopo de Função

```js
//scope.js
let a = 'JavaScript' // é um escopo global, será encontrado em qualquer lugar neste arquivo
let b = 10 // é um escopo global, será encontrado em qualquer lugar neste arquivo
// Escopo de função
function letsLearnScope() {
  console.log(a, b) // JavaScript 10, acessível
  let value = false
// escopo de bloco
  if (true) {
    // podemos acessar de dentro da função e fora da função, mas
    // variáveis declaradas dentro do if não serão acessadas fora do bloco if
    let a = 'Python'
    let b = 20
    let c = 30
    let d = 40
    value = !value
    console.log(a, b, c, value) // Python 20 30 true
  }
  // não podemos acessar c porque o escopo de c é apenas o bloco if
  console.log(a, b, value) // JavaScript 10 true
}
letsLearnScope()
console.log(a, b) // JavaScript 10, acessível
```

Agora, você tem uma compreensão de escopo. Uma variável declarada com *var* só tem escopo para a função, mas uma variável declarada com *let* ou *const* tem escopo de bloco (bloco de função, bloco if, bloco de loop, etc). Um bloco em JavaScript é um código entre duas chaves ({}).

```js
//scope.js
function letsLearnScope() {
  var gravity = 9.81
  console.log(gravity)

}
// console.log(gravity), Uncaught ReferenceError: gravity is not defined

if (true){
  var gravity = 9.81
  console.log(gravity) // 9.81
}
console.log(gravity)  // 9.81

for(var i = 0; i < 3; i++){
  console.log(i) // 0, 1, 2
}
console.log(i) // 3

```

No ES6 e acima, existem *let* e *const*, então você não sofrerá com a astúcia de *var*. Quando usamos *let*, nossa variável tem escopo de bloco e não afetará outras partes do nosso código.

```js
//scope.js
function letsLearnScope() {
  // você pode usar let ou const, mas gravity é constante, prefiro usar const
  const gravity = 9.81
  console.log(gravity)

}
// console.log(gravity), Uncaught ReferenceError: gravity is not defined

if (true){
  const  gravity = 9.81
  console.log(gravity) // 9.81
}
// console.log(gravity), Uncaught ReferenceError: gravity is not defined

for(let i = 0; i < 3; i++){
  console.log(i) // 0, 1, 2
}
// console.log(i), Uncaught ReferenceError: i is not defined

```

O escopo de *let* e *const* é o mesmo. A diferença é apenas na reatribuição. Não podemos mudar ou reatribuir o valor da variável `const`. Eu sugeriria fortemente que você use *let* e *const*, usando *let* e *const* você escreverá código limpo e evitará erros difíceis de depurar. Como regra geral, você pode usar *let* para qualquer valor que mude, *const* para qualquer valor constante, e para um array, objeto, função de seta e expressão de função.

## 📔 Objeto

Tudo pode ser um objeto e objetos têm propriedades e as propriedades têm valores, então um objeto é um par de chave e valor. A ordem da chave não é reservada, ou não há ordem.
Para criar um objeto literal, usamos duas chaves.

### Criando um objeto vazio

Um objeto vazio

```js
const person = {}
```

### Criando um objeto com valores

Agora, o objeto person tem propriedades firstName, lastName, age, location, skills e isMarried. O valor das propriedades ou chaves pode ser uma string, número, booleano, um objeto, nulo, indefinido ou uma função.

Vamos ver alguns exemplos de objeto. Cada chave tem um valor no objeto.

```js
const rectangle = {
  length: 20,
  width: 20
}
console.log(rectangle) // {length: 20, width: 20}

const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  isMarried: true
}
console.log(person)
```

### Obtendo valores de um objeto

Podemos acessar valores de um objeto usando dois métodos:

- usando . seguido pelo nome da chave se o nome da chave for uma palavra
- usando colchetes e aspas

```js
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName}${this.lastName}`
  },
  'phone number': '+3584545454545'
}

// acessando valores usando .
console.log(person.firstName)
console.log(person.lastName)
console.log(person.age)
console.log(person.location) // undefined

// valores podem ser acessados usando colchetes e nome da chave
console.log(person['firstName'])
console.log(person['lastName'])
console.log(person['age'])
console.log(person['age'])
console.log(person['location']) // undefined

// por exemplo, para acessar o número de telefone, usamos apenas o método de colchetes
console.log(person['phone number'])
```

### Criando métodos de objetos

Agora, o objeto person tem propriedades getFullName. A propriedade getFullName é uma função dentro do objeto person e a chamamos de método do objeto. A palavra-chave _this_ refere-se ao próprio objeto. Podemos usar a palavra _this_ para acessar os valores de diferentes propriedades do objeto. Não podemos usar uma função de seta como método de objeto porque a palavra this se refere à janela dentro de uma função de seta em vez do próprio objeto. Exemplo de objeto:

```js
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`
  }
}

console.log(person.getFullName())
// Asabeneh Yetayeh
```

### Definindo nova chave para um objeto

Um objeto é uma estrutura de dados mutável e podemos modificar o conteúdo de um objeto depois que ele é criado.

Definindo novas chaves em um objeto

```js
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`
  }
}
person.nationality = 'Ethiopian'
person.country = 'Finland'
person.title = 'teacher'
person.skills.push('Meteor')
person.skills.push('SasS')
person.isMarried = true

person.getPersonInfo = function() {
  let skillsWithoutLastSkill = this.skills
    .splice(0, this.skills.length - 1)
    .join(', ')
  let lastSkill = this.skills.splice(this.skills.length - 1)[0]

  let skills = `${skillsWithoutLastSkill}, and ${lastSkill}`
  let fullName = this.getFullName()
  let statement = `${fullName} is a ${this.title}.\nHe lives in ${this.country}.\nHe teaches ${skills}.`
  return statement
}
console.log(person)
console.log(person.getPersonInfo())
```

```sh
Asabeneh Yetayeh is a teacher.
He lives in Finland.
He teaches HTML, CSS, JavaScript, React, Node, MongoDB, Python, D3.js, Meteor, and SasS.
```

### Métodos de Objeto

Existem diferentes métodos para manipular um objeto. Vamos ver alguns dos métodos disponíveis.

_Object.assign_: Para copiar um objeto sem modificar o objeto original

```js
const person = {
  firstName: 'Asabeneh',
  age: 250,
  country: 'Finland',
  city:'Helsinki',
  skills: ['HTML', 'CSS', 'JS'],
  title: 'teacher',
  address: {
    street: 'Heitamienkatu 16',
    pobox: 2002,
    city: 'Helsinki'
  },
  getPersonInfo: function() {
    return `I am ${this.firstName} and I live in ${this.city}, ${this.country}. I am ${this.age}.`
  }
}

//Métodos de objeto: Object.assign, Object.keys, Object.values, Object.entries
//hasOwnProperty

const copyPerson = Object.assign({}, person)
console.log(copyPerson)
```

#### Obtendo chaves do objeto usando Object.keys()

_Object.keys_: Para obter as chaves ou propriedades de um objeto como um array

```js
const keys = Object.keys(copyPerson)
console.log(keys) //['firstName', 'age', 'country','city', 'skills','title', 'address', 'getPersonInfo']
const address = Object.keys(copyPerson.address)
console.log(address) //['street', 'pobox', 'city']
```

#### Obtendo valores do objeto usando Object.values()

_Object.values_: Para obter valores de um objeto como um array

```js
const values = Object.values(copyPerson)
console.log(values)
```

#### Obtendo chaves e valores do objeto usando Object.entries()

_Object.entries_: Para obter as chaves e valores em um array

```js
const entries = Object.entries(copyPerson)
console.log(entries)
```

#### Verificando propriedades usando hasOwnProperty()

_hasOwnProperty_: Para verificar se uma chave ou propriedade específica existe em um objeto

```js
console.log(copyPerson.hasOwnProperty('name'))
console.log(copyPerson.hasOwnProperty('score'))
```

🌕 Você é surpreendente. Agora, você está super carregado com o poder dos objetos. Você acabou de completar os desafios do dia 8 e está 8 passos à frente no seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para seus músculos.

## 💻 Exercícios

### Exercícios: Nível 1

1. Crie um objeto vazio chamado dog
2. Imprima o objeto dog no console
3. Adicione propriedades name, legs, color, age e bark para o objeto dog. A propriedade bark é um método que retorna _woof woof_
4. Obtenha name, legs, color, age e valor bark do objeto dog
5. Defina novas propriedades para o objeto dog: breed, getDogInfo

### Exercícios: Nível 2

1. Encontre a pessoa que tem muitas habilidades no objeto users.
2. Conte usuários logados, conte usuários com pontos maiores ou iguais a 50 do objeto a seguir.

   ```js
   const users = {
     Alex: {
       email: 'alex@alex.com',
       skills: ['HTML', 'CSS', 'JavaScript'],
       age: 20,
       isLoggedIn: false,
       points: 30
     },
     Asab: {
       email: 'asab@asab.com',
       skills: ['HTML', 'CSS', 'JavaScript', 'Redux', 'MongoDB', 'Express', 'React', 'Node'],
       age: 25,
       isLoggedIn: false,
       points: 50
     },
     Brook: {
       email: 'daniel@daniel.com',
       skills: ['HTML', 'CSS', 'JavaScript', 'React', 'Redux'],
       age: 30,
       isLoggedIn: true,
       points: 50
     },
     Daniel: {
       email: 'daniel@alex.com',
       skills: ['HTML', 'CSS', 'JavaScript', 'Python'],
       age: 20,
       isLoggedIn: false,
       points: 40
     },
     John: {
       email: 'john@john.com',
       skills: ['HTML', 'CSS', 'JavaScript', 'React', 'Redux', 'Node.js'],
       age: 20,
       isLoggedIn: true,
       points: 50
     },
     Thomas: {
       email: 'thomas@thomas.com',
       skills: ['HTML', 'CSS', 'JavaScript', 'React'],
       age: 20,
       isLoggedIn: false,
       points: 40
     },
     Paul: {
       email: 'paul@paul.com',
       skills: ['HTML', 'CSS', 'JavaScript', 'MongoDB', 'Express', 'React', 'Node'],
       age: 20,
       isLoggedIn: false,
       points: 40
     }
   }
   ```

3. Encontre pessoas que são desenvolvedores MERN stack do objeto users
4. Defina seu nome no objeto users sem modificar o objeto users original
5. Obtenha todas as chaves ou propriedades do objeto users
6. Obtenha todos os valores do objeto users
7. Use o objeto countries para imprimir o nome do país, capital, populações e idiomas.

### Exercícios: Nível 3

1. Crie um objeto literal chamado _personAccount_. Ele possui _firstName, lastName, incomes, expenses_ como propriedades e possui _totalIncome, totalExpense, accountInfo, addIncome, addExpense_ e _accountBalance_ como métodos. Incomes é um conjunto de renda e sua descrição e expenses é um conjunto de despesas e sua descrição.
2. **** As questões 2, 3 e 4 são baseadas nos dois arrays a seguir: users e products ()

  ```js
      const users = [
      {
          _id: 'ab12ex',
          username: 'Alex',
          email: 'alex@alex.com',
          password: '123123',
          createdAt:'08/01/2020 9:00 AM',
          isLoggedIn: false
      },
      {
          _id: 'fg12cy',
          username: 'Asab',
          email: 'asab@asab.com',
          password: '123456',
          createdAt:'08/01/2020 9:30 AM',
          isLoggedIn: true
      },
      {
          _id: 'zwf8md',
          username: 'Brook',
          email: 'brook@brook.com',
          password: '123111',
          createdAt:'08/01/2020 9:45 AM',
          isLoggedIn: true
      },
      {
          _id: 'eefamr',
          username: 'Martha',
          email: 'martha@martha.com',
          password: '123222',
          createdAt:'08/01/2020 9:50 AM',
          isLoggedIn: false
      },
      {
          _id: 'ghderc',
          username: 'Thomas',
          email: 'thomas@thomas.com',
          password: '123333',
          createdAt:'08/01/2020 10:00 AM',
          isLoggedIn: false
      }
      ];

      const products = [
    {
      _id: 'eedfcf',
      name: 'mobile phone',
      description: 'Huawei Honor',
      price: 200,
      ratings: [
        { userId: 'fg12cy', rate: 5 },
        { userId: 'zwf8md', rate: 4.5 }
      ],
      likes: []
    },
    {
      _id: 'aegfal',
      name: 'Laptop',
      description: 'MacPro: System Darwin',
      price: 2500,
      ratings: [],
      likes: ['fg12cy']
    },
    {
      _id: 'hedfcg',
      name: 'TV',
      description: 'Smart TV:Procaster',
      price: 400,
      ratings: [{ userId: 'fg12cy', rate: 5 }],
      likes: ['fg12cy']
    }
  ]
  ```

  Imagine que você está recebendo a coleção de usuários acima de um banco de dados MongoDB.
    a. Crie uma função chamada signUp que permita ao usuário adicionar à coleção. Se o usuário existir, informe ao usuário que ele já tem uma conta.  
    b. Crie uma função chamada signIn que permita ao usuário fazer login na aplicação  

1. O array products tem três elementos e cada um deles tem seis propriedades.
    a. Crie uma função chamada rateProduct que avalia o produto
    b. Crie uma função chamada averageRating que calcula a avaliação média de um produto  

2. Crie uma função chamada likeProduct. Esta função ajudará a curtir o produto se ele não for curtido e removerá a curtida se já tiver sido curtido.

🎉 PARABÉNS ! 🎉

[<< Dia 7](../Dia_07_Funcoes/Dia_07_Funcoes.md) | [Dia 9 >>](../Dia_09_Funcoes_Ordem_Superior/dia_09_funcoes_ordem_superior.md)
