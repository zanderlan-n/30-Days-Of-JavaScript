<div align="center">
  <h1> 30 Dias De JavaScript: Destructuring e Spreading</h1>
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

[<< Dia 10](../Dia_10_Sets_e_Maps/dia_10_sets_e_maps.md) | [Dia 12>>](../Dia_12_Expressoes_Regulares/dia_12_expressoes_regulares.md)

![Dia 11](../../images/banners/day_1_11.png)

- [Dia 11](#dia-11)
	- [Destructuring e Spread](#destructuring-e-spread)
		- [Destructuring de Arrays](#destructuring-de-arrays)
		- [Destructuring durante iteração](#destructuring-durante-iteração)
		- [Destructuring de Objeto](#destructuring-de-objeto)
		- [Renomeando durante o destructuring](#renomeando-durante-o-destructuring)
		- [Parâmetros de objeto sem destructuring](#parâmetros-de-objeto-sem-destructuring)
		- [Parâmetros de objeto com destructuring](#parâmetros-de-objeto-com-destructuring)
		- [Destructuring de objeto durante iteração](#destructuring-de-objeto-durante-iteração)
		- [Operador Spread ou Rest](#operador-spread-ou-rest)
		- [Operador spread para obter o resto dos elementos do array](#operador-spread-para-obter-o-resto-dos-elementos-do-array)
		- [Operador spread para copiar array](#operador-spread-para-copiar-array)
		- [Operador spread para copiar objeto](#operador-spread-para-copiar-objeto)
			- [Operador spread com função arrow](#operador-spread-com-função-arrow)
	- [Exercícios](#exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 11

## Destructuring e Spread

Destructuring é uma maneira de desempacotar arrays e objetos e atribuí-los a uma variável distinta.

### Destructuring de Arrays

```js
  const numbers = [1, 2, 3]
  let [numOne, numTwo, numThree] = numbers

  console.log(numOne, numTwo, numThree)
```

```sh
  1 2 3
```

```js
  const names = ['Asabeneh', 'Brook', 'David', 'John']
  let [firstPerson, secondPerson, thirdPerson, fourthPerson] = names

  console.log(firstPerson, secondPerson,thirdPerson, fourthPerson)
```

```sh
Asabeneh Brook David John
```

```js
  const scientificConstants = [2.72, 3.14, 9.81, 37, 100]
  let [e, pi, gravity, bodyTemp, boilingTemp] = scientificConstants

  console.log(e,pi,gravity, bodyTemp, boilingTemp)
```

```sh
2.72 3.14 9.81 37 100
```

```js
const fullStack = [
  ['HTML', 'CSS', 'JS', 'React'],
  ['Node', 'Express', 'MongoDB']
]
const [frontEnd, backEnd] = fullStack

console.log(frontEnd)
console.log(backEnd)
```

```sh
["HTML", "CSS", "JS", "React"]
["Node", "Express", "MongoDB"]
```

Se quisermos pular um dos valores no array, usamos vírgula adicional. A vírgula ajuda a omitir o valor naquele índice específico

```js
  const numbers = [1, 2, 3]
  let [numOne, , numThree] = numbers //2 é omitido

  console.log(numOne, numThree)
```

```sh
1 3
```

```js
  const names = ['Asabeneh', 'Brook', 'David', 'John']
  let [, secondPerson, , fourthPerson] = names // primeiro e terceiro são omitidos

  console.log(secondPerson, fourthPerson)
```

```sh
Brook John
```

Podemos usar valores padrão caso o valor do array para aquele índice seja undefined:

```js
const names = [undefined, 'Brook', 'David']
let [
  firstPerson = 'Asabeneh',
  secondPerson,
  thirdPerson,
  fourthPerson = 'John'
] = names

console.log(firstPerson, secondPerson, thirdPerson, fourthPerson)  
```

```sh
Asabeneh Brook David John
```

Não podemos atribuir variáveis a todos os elementos do array. Podemos fazer destructuring de alguns dos primeiros e podemos obter os restantes como array usando o operador spread (...).

```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
let [num1, num2, num3, ...rest] = nums

console.log(num1, num2, num3)
console.log(rest)
```

```sh
1 2 3
[4, 5, 6, 7, 8, 9, 10]
```

### Destructuring durante iteração

```js
const countries = [['Finland', 'Helsinki'], ['Sweden', 'Stockholm'], ['Norway', 'Oslo']]

for (const [country, city] of countries) {
console.log(country, city)
}
```

```sh
Finland Helsinki
Sweden Stockholm
Norway Oslo
```

```js
const fullStack = [
  ['HTML', 'CSS', 'JS', 'React'],
  ['Node', 'Express', 'MongoDB']
]

for(const [first, second, third] of fullStack) {
console.log(first, second, third)
}
```

```sh
HTML CSS JS
Node Express MongoDB
```

### Destructuring de Objeto

Quando fazemos destructuring, o nome da variável que usamos para fazer o destructuring deve ser exatamente igual à chave ou propriedade do objeto. Veja o exemplo abaixo.

```js
const rectangle = {
  width: 20,
  height: 10,
  area: 200
}
let { width, height, area, perimeter } = rectangle

console.log(width, height, area, perimeter)
```

```sh
20 10 200 undefined
```

### Renomeando durante o destructuring

```js
const rectangle = {
  width: 20,
  height: 10,
  area: 200
}
let { width: w, height: h, area: a, perimeter: p } = rectangle

console.log(w, h, a, p)
```

```sh
20 10 200 undefined
```

Se a chave não for encontrada no objeto, a variável será atribuída como undefined. Às vezes a chave pode não estar no objeto, nesse caso podemos dar um valor padrão durante a declaração. Veja o exemplo.

```js
const rectangle = {
  width: 20,
  height: 10,
  area: 200
}
let { width, height, area, perimeter = 60 } = rectangle

console.log(width, height, area, perimeter) //20 10 200 60
//Vamos modificar o objeto: width para 30 e perimeter para 80
```

```js
const rectangle = {
  width: 30,
  height: 10,
  area: 200,
  perimeter: 80
}
let { width, height, area, perimeter = 60 } = rectangle
console.log(width, height, area, perimeter) //30 10 200 80
```

Destructuring de chaves como parâmetros de funções. Vamos criar uma função que recebe um objeto retângulo e retorna o perímetro de um retângulo.

### Parâmetros de objeto sem destructuring

```js
// Sem destructuring
const rect = {
  width: 20,
  height: 10
}
const calculatePerimeter = rectangle => {
  return 2 * (rectangle.width + rectangle.height)
}

console.log(calculatePerimeter(rect)) // 60
```

```js
//Outro exemplo
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  job: 'Instrutor e Desenvolvedor',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Redux',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  languages: ['Amharic', 'English', 'Suomi(Finnish)']
}
// Vamos criar uma função que forneça informações sobre o objeto pessoa sem destructuring

const getPersonInfo = obj => {
  const skills = obj.skills
  const formattedSkills = skills.slice(0, -1).join(', ')
  const languages = obj.languages
  const formattedLanguages = languages.slice(0, -1).join(', ')

  personInfo = `${obj.firstName} ${obj.lastName} mora em ${obj.country}. Ele tem ${obj.age} anos. Ele é um ${obj.job}. Ele ensina ${formattedSkills} e ${skills[skills.length - 1]}. Ele fala ${formattedLanguages} e um pouco de ${languages[2]}.`

  return personInfo
}

console.log(getPersonInfo(person))
```

### Parâmetros de objeto com destructuring

```js
const calculatePerimeter = ({ width, height }) => {
  return 2 * (width + height)
}

console.log(calculatePerimeter(rect)) // 60
```

```js
// Vamos criar uma função que forneça informações sobre o objeto pessoa com destructuring
const getPersonInfo = ({
  firstName,
  lastName,
  age,
  country,
  job,
  skills,
  languages
}) => {
  const formattedSkills = skills.slice(0, -1).join(', ')
  const formattedLanguages = languages.slice(0, -1).join(', ')

  personInfo = `${firstName} ${lastName} mora em ${country}. Ele tem ${age} anos. Ele é um ${job}. Ele ensina ${formattedSkills} e ${skills[skills.length - 1]}. Ele fala ${formattedLanguages} e um pouco de ${languages[2]}.`

  return personInfo
}
console.log(getPersonInfo(person))
/*
Asabeneh Yetayeh mora em Finland. Ele tem 250 anos. Ele é um Instrutor e Desenvolvedor. Ele ensina HTML, CSS, JavaScript, React, Redux, Node, MongoDB, Python e D3.js. Ele fala Amharic, English e um pouco de Suomi(Finnish)
*/

## Operador Spread ou Rest

Quando usamos o operador spread (...), os elementos iteráveis, como um array ou uma string, são expandidos em elementos individuais. O operador spread (...) é usado para espalhar um array em lugares onde zero ou mais elementos são esperados. Também é usado para espalhar um objeto em lugares onde zero ou chave são esperadas.

### Operador Spread para obter o resto dos elementos do array

```js
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
let [num1, num2, num3, ...rest] = nums

console.log(num1, num2, num3)
console.log(rest)
```

```sh
1 2 3
[4, 5, 6, 7, 8, 9, 10]
```

```js
const countries = [
  'Germany',
  'France',
  'Belgium',
  'Finland',
  'Sweden',
  'Norway',
  'Denmark',
  'Iceland'
]

let [gem, fra, , ...nordicCountries] = countries

console.log(gem)
console.log(fra)
console.log(nordicCountries)
```

```sh
Germany
France
['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
```

### Operador Spread para copiar um array

```js
const evens = [0, 2, 4, 6, 8, 10]
const evenNumbers = [...evens]

const odds = [1, 3, 5, 7, 9]
const oddNumbers = [...odds]

const wholeNumbers = [...evens, ...odds]

console.log(evenNumbers)
console.log(oddNumbers)
console.log(wholeNumbers)
```

```sh
[0, 2, 4, 6, 8, 10]
[1, 3, 5, 7, 9]
[0, 2, 4, 6, 8, 10, 1, 3, 5, 7, 9]
```

```js
const frontEnd = ['HTML', 'CSS', 'JS', 'React']
const backEnd = ['Node', 'Express', 'MongoDB']
const fullStack = [...frontEnd, ...backEnd]

console.log(fullStack)
```

```sh
["HTML", "CSS", "JS", "React", "Node", "Express", "MongoDB"]
```

### Operador Spread para copiar um objeto
Podemos copiar um objeto usando um operador spread

```js
const user = {
  name: 'Asabeneh',
  title: 'Programador',
  country: 'Finland',
  city: 'Helsinki'
}

const copiedUser = {...user}
console.log(copiedUser)
```

```sh
{name: "Asabeneh", title: "Programador", country: "Finland", city: "Helsinki"}
```

Mesclar objetos: para modificar um objeto e incluir mais propriedades, podemos usar o operador spread.

```js
const user = {
  name: 'Asabeneh',
  title: 'Programador',
  country: 'Finland',
  city: 'Helsinki'
}

const newUser = {...user, title: 'Instrutor'}
console.log(newUser)
```

```sh
{name: "Asabeneh", title: "Instrutor", country: "Finland", city: "Helsinki"}
```

### Operador Spread com função de flecha

Podemos usar o operador spread para passar um número ilimitado de argumentos para uma função de flecha. O argumento passado para uma função spread é um array.

```js
const sumAllNums = (...args) => {
  console.log(args)
}

sumAllNums(1, 2, 3, 4, 5)
```

```sh
[1, 2, 3, 4, 5]
```

```js
const sumAllNums = (...args) => {
  let sum = 0
  for (const num of args){
    sum += num
  }
  return sum
}

console.log(sumAllNums(1, 2, 3, 4, 5))
```

```sh
15
```

🌕 Você alcançou bastante até agora. Agora, seu nível de JavaScript é intermédio superior. Continue indo! Você acabou de completar os desafios do dia 11 e está 11 passos à frente em sua jornada para o grande sucesso. Agora faça alguns exercícios para o seu cérebro e para o seu músculo.

## Exercícios

### Exercícios: Nível 1

```js
const constants = [2.72, 3.14, 9.81, 37, 100]
const countries = ['Finland', 'Estonia', 'Sweden', 'Denmark', 'Norway']
const rectangle = {
  width: 20,
  height: 10,
  area: 200,
  perimeter: 60
}
const users = [
{
  name:'Brook',
  scores:75,
  skills:['HTM', 'CSS', 'JS'],
  age:16
},
{
  name:'Alex',
  scores:80,
  skills:['HTM', 'CSS', 'JS'],
  age:18
},
{
  name:'David',
  scores:75,
  skills:['HTM', 'CSS'],
  age:22
},
{
  name:'John',
  scores:85,
  skills:['HTML'],
  age:25
},
{
  name:'Sara',
  scores:95,
  skills:['HTM', 'CSS', 'JS'],
  age: 26
},
{
  name:'Martha',
  scores:80,
  skills:['HTM', 'CSS', 'JS'],
  age:18
},
{
  name:'Thomas',
  scores:90,
  skills:['HTM', 'CSS', 'JS'],
  age:20
}
]
```

1. Faça o destructuring e atribua os elementos do array `constants` para e, pi, gravity, humanBodyTemp, waterBoilingTemp.
2. Faça o destructuring e atribua os elementos do array `countries` para fin, est, sw, den, nor
3. Faça o destructuring do objeto `rectangle` por suas propriedades ou chaves.


### Exercícios: Nível 2

1. Itere através do array `users` e obtenha todas as chaves do objeto usando destructuring
2. Encontre as pessoas que têm menos de duas habilidades

### Exercícios: Nível 3

1. Faça o destructuring do objeto `countries` e imprima o nome, capital, população e idiomas de todos os países
2. Um desenvolvedor júnior estruturou o nome do aluno, habilidades e pontuação em um array de arrays que pode não ser fácil de ler. Faça o destructuring do seguinte array: nome para name, array de habilidades para skills, array de pontuações para scores, pontuação de JavaScript para jsScore e pontuação de React para reactScore em uma única linha.

  ```js
    const student = ['David', ['HTM', 'CSS', 'JS', 'React'], [98, 85, 90, 95]]
    console.log(name, skills, jsScore, reactScore)
  ```

  ```sh
  David (4) ["HTM", "CSS", "JS", "React"] 90 95
  ```

3. Escreva uma função chamada *convertArrayToObject* que possa converter o array em um objeto estruturado.

  ```js
      const students = [
          ['David', ['HTM', 'CSS', 'JS', 'React'], [98, 85, 90, 95]],
          ['John', ['HTM', 'CSS', 'JS', 'React'], [85, 80, 85, 80]]
        ]

      console.log(convertArrayToObject(students))
      [
        {
          name: 'David',
          skills: ['HTM','CSS','JS','React'],
          scores: [98,85,90,95]
        },
        {
          name: 'John',
          skills: ['HTM','CSS','JS','React'],
          scores: [85, 80,85,80]
        }
      ]
  ```

4. Copie o objeto `student` para `newStudent` sem mutar o objeto original. No novo objeto adicione o seguinte:

- Adicione Bootstrap com nível 8 ao conjunto de habilidades front end
- Adicione Express com nível 9 ao conjunto de habilidades back end
- Adicione SQL com nível 8 ao conjunto de habilidades de banco de dados
- Adicione SQL sem nível ao conjunto de habilidades de data science

```js
    const student = {
      name: 'David',
      age: 25,
      skills: {
        frontEnd: [
          { skill: 'HTML', level: 10 },
          { skill: 'CSS', level: 8 },
          { skill: 'JS', level: 8 },
          { skill: 'React', level: 9 }
        ],
        backEnd: [
          { skill: 'Node',level: 7 },
          { skill: 'GraphQL', level: 8 },
        ],
        dataBase:[
          { skill: 'MongoDB', level: 7.5 },
        ],
        dataScience:['Python', 'R', 'D3.js']
      }
    }
  ```

 O objeto copiado deve ter esta aparência:

```js
    {
    name: 'David',
    age: 25,
    skills: {
      frontEnd: [
        {skill: 'HTML',level: 10},
        {skill: 'CSS',level: 8},
        {skill: 'JS',level: 8},
        {skill: 'React',level: 9},
        {skill: 'BootStrap',level: 8}
      ],
      backEnd: [
        {skill: 'Node',level: 7},
        {skill: 'GraphQL',level: 8},
        {skill: 'Express',level: 9}
      ],
      dataBase: [
        { skill: 'MongoDB',level: 7.5},
        { skill: 'SQL',level: 8}
      ],
      dataScience: ['Python','R','D3.js','SQL']
    }
  }

```

🎉 PARABÉNS ! 🎉

[<< Dia 10](../Dia_10_Sets_e_Maps/dia_10_sets_e_maps.md) | [Dia 12>>](../Dia_12_Expressoes_Regulares/dia_12_expressoes_regulares.md)