<div align="center">
  <h1> 30 Dias De JavaScript: JSON</h1>
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

[<< Dia 15](../Dia_15_Classes/Dia_15_Classes.md) | [Dia 17 >>](../Dia_17_Web_Storages/Dia_17_Web_Storages.md)

![Trinta Dias De JavaScript](../images/banners/day_1_16.png)

- [Dia 16](#dia-16)
	- [JSON](#json)
		- [Convertendo JSON para Objeto JavaScript](#convertendo-json-para-objeto-javascript)
			- [JSON.parse()](#jsonparse)
		- [Usando uma função reviver com JSON.parse()](#usando-uma-função-reviver-com-jsonparse)
		- [Convertendo Objeto para JSON](#convertendo-objeto-para-json)
		- [Usando um Array de Filtro com JSON.stringify()](#usando-um-array-de-filtro-com-jsonstringify)
	- [Exercícios](#exercícios)
		- [Exercícios Nível 1](#exercícios-nível-1)
		- [Exercícios Nível 2](#exercícios-nível-2)
		- [Exercícios Nível 3](#exercícios-nível-3)

# Dia 16

## JSON

JSON significa JavaScript Object Notation. A sintaxe JSON é derivada da sintaxe de notação de objeto JavaScript, mas o formato JSON é apenas texto ou string. JSON é um formato de dados leve para armazenamento e transporte. JSON é usado principalmente quando os dados são enviados de um servidor para um cliente. JSON é uma alternativa mais fácil de usar ao XML.

**Exemplo:**

```js
{
"users":[
  {
    "firstName":"Asabeneh",
    "lastName":"Yetayeh",
    "age":250,
    "email":"asab@asb.com"
  },
  {
    "firstName":"Alex",
    "lastName":"James",
    "age":25,
    "email":"alex@alex.com"
  },
  {
  "firstName":"Lidiya",
  "lastName":"Tekle",
  "age":28,
  "email":"lidiya@lidiya.com"
  }
]
}
```

O exemplo JSON acima não é muito diferente de um objeto normal. Então, qual é a diferença? A diferença é que a chave de um objeto JSON deve estar entre aspas duplas ou deve ser uma string. Objeto JavaScript e JSON são muito semelhantes, de modo que podemos transformar JSON em Objeto e Objeto em JSON.

Vejamos o exemplo acima com mais detalhes, ele começa com uma chave. Dentro da chave, existe a chave "users" que tem um valor de array. Dentro do array temos objetos diferentes e cada objeto tem chaves, cada chave deve ter aspas duplas. Por exemplo, usamos "firstName" em vez de apenas firstName, no entanto, em objeto usamos chaves sem aspas duplas. Esta é a principal diferença entre um objeto e um JSON. Vejamos mais exemplos sobre JSON.

**Exemplo:**

```js
{
    "Alex": {
        "email": "alex@alex.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 30
    },
    "Asab": {
        "email": "asab@asab.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "Redux",
            "MongoDB",
            "Express",
            "React",
            "Node"
        ],
        "age": 25,
        "isLoggedIn": false,
        "points": 50
    },
    "Brook": {
        "email": "daniel@daniel.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React",
            "Redux"
        ],
        "age": 30,
        "isLoggedIn": true,
        "points": 50
    },
    "Daniel": {
        "email": "daniel@alex.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "Python"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    },
    "John": {
        "email": "john@john.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React",
            "Redux",
            "Node.js"
        ],
        "age": 20,
        "isLoggedIn": true,
        "points": 50
    },
    "Thomas": {
        "email": "thomas@thomas.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    },
    "Paul": {
        "email": "paul@paul.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "MongoDB",
            "Express",
            "React",
            "Node"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    }
}
```

### Convertendo JSON para Objeto JavaScript

Principalmente, buscamos dados JSON de uma resposta HTTP ou de um arquivo, mas podemos armazenar o JSON como uma string e podemos transformá-lo em Objeto para fins de demonstração. Em JavaScript, a palavra-chave _JSON_ possui os métodos _parse()_ e _stringify()_. Quando queremos transformar o JSON em um objeto, analisamos o JSON usando _JSON.parse()_. Quando queremos transformar o objeto em JSON, usamos _JSON.stringify()_.

#### JSON.parse()

```js
JSON.parse(json[, reviver])
// json ou texto, os dados
// reviver é uma função de callback opcional
/* JSON.parse(json, (key, value) => {

})
*/
```

```js
const usersText = `{
"users":[
  {
    "firstName":"Asabeneh",
    "lastName":"Yetayeh",
    "age":250,
    "email":"asab@asb.com"
  },
  {
    "firstName":"Alex",
    "lastName":"James",
    "age":25,
    "email":"alex@alex.com"
  },
  {
  "firstName":"Lidiya",
  "lastName":"Tekle",
  "age":28,
  "email":"lidiya@lidiya.com"
  }
]
}`

const usersObj = JSON.parse(usersText, undefined, 4)
console.log(usersObj)
```

### Usando uma função reviver com JSON.parse()

Para usar a função reviver como um formatador, colocamos as chaves que queremos formatar (firstName e lastName) como valor. Digamos que estamos interessados em formatar o firstName e o lastName dos dados JSON.

```js
const usersText = `{
"users":[
  {
    "firstName":"Asabeneh",
    "lastName":"Yetayeh",
    "age":250,
    "email":"asab@asb.com"
  },
  {
    "firstName":"Alex",
    "lastName":"James",
    "age":25,
    "email":"alex@alex.com"
  },
  {
  "firstName":"Lidiya",
  "lastName":"Tekle",
  "age":28,
  "email":"lidiya@lidiya.com"
  }
]
}`

const usersObj = JSON.parse(usersText, (key, value) => {
  let newValue =
    typeof value == 'string' && key != 'email' ? value.toUpperCase() : value
  return newValue
})
console.log(usersObj)
```

O _JSON.parse()_ é muito prático de usar. Você não precisa passar o parâmetro opcional, pode usá-lo apenas com o parâmetro obrigatório e conseguirá bastante coisa.

### Convertendo Objeto para JSON

Quando queremos transformar o objeto em JSON, usamos _JSON.stringify()_. O método stringify recebe um parâmetro obrigatório e dois parâmetros opcionais. O replacer é usado como filtro e o space é uma indentação. Se não quisermos filtrar nenhuma das chaves do objeto, podemos simplesmente passar undefined.

```js
JSON.stringify(obj, replacer, space)
// json ou texto, os dados
// reviver é uma função de callback opcional
```

Vamos converter o seguinte objeto em uma string. Primeiro, vamos manter todas as chaves e também vamos ter uma indentação de 4 espaços.

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
    skills: [
      'HTML',
      'CSS',
      'JavaScript',
      'Redux',
      'MongoDB',
      'Express',
      'React',
      'Node'
    ],
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
    skills: [
      'HTML',
      'CSS',
      'JavaScript',
      'MongoDB',
      'Express',
      'React',
      'Node'
    ],
    age: 20,
    isLoggedIn: false,
    points: 40
  }
}

const txt = JSON.stringify(users, undefined, 4)
console.log(txt) // text significa JSON - porque json é uma forma de string de um objeto.
```

```sh
{
    "Alex": {
        "email": "alex@alex.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 30
    },
    "Asab": {
        "email": "asab@asab.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "Redux",
            "MongoDB",
            "Express",
            "React",
            "Node"
        ],
        "age": 25,
        "isLoggedIn": false,
        "points": 50
    },
    "Brook": {
        "email": "daniel@daniel.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React",
            "Redux"
        ],
        "age": 30,
        "isLoggedIn": true,
        "points": 50
    },
    "Daniel": {
        "email": "daniel@alex.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "Python"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    },
    "John": {
        "email": "john@john.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React",
            "Redux",
            "Node.js"
        ],
        "age": 20,
        "isLoggedIn": true,
        "points": 50
    },
    "Thomas": {
        "email": "thomas@thomas.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    },
    "Paul": {
        "email": "paul@paul.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "MongoDB",
            "Express",
            "React",
            "Node"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    }
}
```

### Usando um Array de Filtro com JSON.stringify

Agora, vamos usar o replacer como um filtro. O objeto user tem uma longa lista de chaves, mas estamos interessados apenas em algumas delas. Colocamos as chaves que queremos manter em um array, como mostrado no exemplo, e o usamos no lugar do replacer.

```js
const user = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  country: 'Finlândia',
  city: 'Helsinki',
  email: 'alex@alex.com',
  skills: ['HTML', 'CSS', 'JavaScript', 'React', 'Python'],
  age: 250,
  isLoggedIn: false,
  points: 30
}

const txt = JSON.stringify(user,['firstName', 'lastName', 'country', 'city', 'age'],4)
console.log(txt)
```

```sh
{
    "firstName": "Asabeneh",
    "lastName": "Yetayeh",
    "country": "Finlândia",
    "city": "Helsinki",
    "age": 250
}
```

🌕 Você é extraordinário. Agora, você conhece um formato de dados leve que pode usar para armazenar dados ou enviá-los para um servidor HTTP. Você está 16 passos à frente em seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

```js
const skills = ['HTML', 'CSS', 'JS', 'React','Node', 'Python']
let age = 250;
let isMarried = true
const student = {
  firstName:'Asabeneh',
  lastName:'Yetayehe',
  age:250,
  isMarried:true,
  skills:['HTML', 'CSS', 'JS', 'React','Node', 'Python', ]
}
const txt = `{
    "Alex": {
        "email": "alex@alex.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 30
    },
    "Asab": {
        "email": "asab@asab.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "Redux",
            "MongoDB",
            "Express",
            "React",
            "Node"
        ],
        "age": 25,
        "isLoggedIn": false,
        "points": 50
    },
    "Brook": {
        "email": "daniel@daniel.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React",
            "Redux"
        ],
        "age": 30,
        "isLoggedIn": true,
        "points": 50
    },
    "Daniel": {
        "email": "daniel@alex.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "Python"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    },
    "John": {
        "email": "john@john.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React",
            "Redux",
            "Node.js"
        ],
        "age": 20,
        "isLoggedIn": true,
        "points": 50
    },
    "Thomas": {
        "email": "thomas@thomas.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "React"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    },
    "Paul": {
        "email": "paul@paul.com",
        "skills": [
            "HTML",
            "CSS",
            "JavaScript",
            "MongoDB",
            "Express",
            "React",
            "Node"
        ],
        "age": 20,
        "isLoggedIn": false,
        "points": 40
    }
}
`
```

### Exercícios Nível 1

1. Converta o array skills para JSON usando JSON.stringify()
2. Converta a variável age para string usando JSON.stringify()
3. Converta a variável isMarried para string usando JSON.stringify()
4. Converta o objeto student para string usando JSON.stringify()

### Exercícios Nível 2

1. Converta o objeto students para string apenas com as propriedades firstName, lastName e skills

### Exercícios Nível 3

1. Analise o JSON *txt* para objeto.
2. Encontre o usuário que tem mais habilidades a partir da variável armazenada em *txt*.

🎉 PARABÉNS ! 🎉

[<< Dia 15](../Dia_15_Classes/Dia_15_Classes.md) | [Dia 17 >>](../Dia_17_Web_Storages/Dia_17_Web_Storages.md)
