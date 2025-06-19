<div align="center">
  <h1> 30 Dias De JavaScript: Sets e Maps</h1>
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

[<< Dia 9](../Dia_09_Funcoes_Ordem_Superior/dia_09_funcoes_ordem_superior.md) | [Dia 11>>](../Dia_11_Destructuring_e_Spreading/dia_11_destructuring_e_spreading.md)

![Dia 10](../../images/banners/day_1_10.png)

- [Dia 10](#dia-10)
	- [Set](#set)
		- [Criando um set vazio](#criando-um-set-vazio)
		- [Criando um set a partir de um array](#criando-um-set-a-partir-de-um-array)
		- [Adicionando um elemento a um set](#adicionando-um-elemento-a-um-set)
		- [Excluindo um elemento de um set](#excluindo-um-elemento-de-um-set)
		- [Verificando se um elemento existe no set](#verificando-se-um-elemento-existe-no-set)
		- [Limpando o set](#limpando-o-set)
		- [União de sets](#união-de-sets)
		- [Interseção de sets](#interseção-de-sets)
		- [Diferença de sets](#diferença-de-sets)
	- [Map](#map)
		- [Criando um Map vazio](#criando-um-map-vazio)
		- [Criando um Map a partir de um array](#criando-um-map-a-partir-de-um-array)
		- [Adicionando valores ao Map](#adicionando-valores-ao-map)
		- [Obtendo um valor de um Map](#obtendo-um-valor-de-um-map)
		- [Verificando uma chave em um Map](#verificando-uma-chave-em-um-map)
	- [Exercícios](#exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 10

## Set

Set é uma coleção de elementos. Um Set só pode conter elementos únicos.
Vamos ver como criar um set na seção abaixo.

### Criando um set vazio

```js
const companies = new Set()
console.log(companies)
```

```sh
Set(0) {}
```

### Criando um set a partir de um array

```js
const languages = [
  'English',
  'Finnish',
  'English',
  'French',
  'Spanish',
  'English',
  'French',
]

const setOfLanguages = new Set(languages)
console.log(setOfLanguages)
```

```sh
Set(4) {"English", "Finnish", "French", "Spanish"}
```

Set é um objeto iterável e podemos iterar através de cada elemento.

```js
const languages = [
  'English',
  'Finnish',
  'English',
  'French',
  'Spanish',
  'English',
  'French',
]

const setOfLanguages = new Set(languages)

for (const language of setOfLanguages) {
  console.log(language)
}
```

```sh
  English
  Finnish
  French
  Spanish
```

### Adicionando um elemento a um set

```js
const companies = new Set() // criando um set vazio
console.log(companies.size) // 0

companies.add('Google') // adicionando elemento ao set
companies.add('Facebook')
companies.add('Amazon')
companies.add('Oracle')
companies.add('Microsoft')
console.log(companies.size) // 5 elementos no set
console.log(companies)
```

```sh
Set(5) {"Google", "Facebook", "Amazon", "Oracle", "Microsoft"}
```

Também podemos usar um loop para adicionar elementos a um set.

```js
const companies = ['Google', 'Facebook', 'Amazon', 'Oracle', 'Microsoft']
setOfCompanies = new Set()
for (const company of companies) {
  setOfCompanies.add(company)
}
```

```sh
Set(5) {"Google", "Facebook", "Amazon", "Oracle", "Microsoft"}

```

### Excluindo um elemento de um set

Podemos excluir um elemento de um set usando o método delete.

```js
console.log(companies.delete('Google'))
console.log(companies.size) // 4 elementos restantes no set
```

### Verificando se um elemento existe no set

O método has pode ajudar a saber se um determinado elemento existe em um set.

```js
console.log(companies.has('Apple')) // false
console.log(companies.has('Facebook')) // true
```

### Limpando o set

Remove todos os elementos de um set.

```js
companies.clear()
console.log(companies)
```

```sh
Set(0) {}
```

Veja o exemplo abaixo para aprender como usar um set.

```js
const languages = [
  'English',
  'Finnish',
  'English',
  'French',
  'Spanish',
  'English',
  'French',
]
const langSet = new Set(languages)
console.log(langSet) // Set(4) {"English", "Finnish", "French", "Spanish"}
console.log(langSet.size) // 4

const counts = []
const count = {}

for (const l of langSet) {
  const filteredLang = languages.filter((lng) => lng === l)
  console.log(filteredLang) // ["English", "English", "English"]
  counts.push({ lang: l, count: filteredLang.length })
}
console.log(counts)
```

```js
[
  { lang: 'English', count: 3 },
  { lang: 'Finnish', count: 1 },
  { lang: 'French', count: 2 },
  { lang: 'Spanish', count: 1 },
]
```

Outro caso de uso de set. Por exemplo, para contar itens únicos em um array.

```js
const numbers = [5, 3, 2, 5, 5, 9, 4, 5]
const setOfNumbers = new Set(numbers)

console.log(setOfNumbers)
```

```sh
Set(5) {5, 3, 2, 9, 4}
```

### União de sets

Para encontrar a união de dois sets, podemos usar o operador spread. Vamos encontrar a união dos sets A e B (A U B)

```js
let a = [1, 2, 3, 4, 5]
let b = [3, 4, 5, 6]
let c = [...a, ...b]

let A = new Set(a)
let B = new Set(b)
let C = new Set(c)

console.log(C)
```

```sh
Set(6) {1, 2, 3, 4, 5, 6}
```

### Interseção de sets

Para encontrar a interseção de dois sets, pode-se usar o método filter. Vamos encontrar a interseção dos sets A e B (A ∩ B)

```js
let a = [1, 2, 3, 4, 5]
let b = [3, 4, 5, 6]

let A = new Set(a)
let B = new Set(b)

let c = a.filter((num) => B.has(num))
let C = new Set(c)

console.log(C)
```

```sh
Set(3) {3, 4, 5}
```

### Diferença de sets

Para encontrar a diferença entre dois sets, pode-se usar o método filter. Vamos encontrar a diferença entre os sets A e B (A \ B)

```js
let a = [1, 2, 3, 4, 5]
let b = [3, 4, 5, 6]

let A = new Set(a)
let B = new Set(b)

let c = a.filter((num) => !B.has(num))
let C = new Set(c)

console.log(C)
```

```sh
Set(2) {1, 2}
```

## Map

### Criando um Map vazio

```js
const map = new Map()
console.log(map)
```

```sh
Map(0) {}
```

### Criando um Map a partir de um array

```js
countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo'],
]
const map = new Map(countries)
console.log(map)
console.log(map.size)
```

```sh
Map(3) {"Finland" => "Helsinki", "Sweden" => "Stockholm", "Norway" => "Oslo"}
3
```

### Adicionando valores ao Map

```js
const countriesMap = new Map()
console.log(countriesMap.size) // 0
countriesMap.set('Finland', 'Helsinki')
countriesMap.set('Sweden', 'Stockholm')
countriesMap.set('Norway', 'Oslo')
console.log(countriesMap)
console.log(countriesMap.size)
```

```sh
Map(3) {"Finland" => "Helsinki", "Sweden" => "Stockholm", "Norway" => "Oslo"}
3
```

### Obtendo um valor de um Map

```js
console.log(countriesMap.get('Finland'))
```

```sh
Helsinki
```

### Verificando uma chave em um Map

Verifique se uma chave existe em um map usando o método _has_. Ele retorna _true_ ou _false_.

```js
console.log(countriesMap.has('Finland'))
```

```sh
true
```

Obtendo todos os valores de um map usando loop

```js
for (const country of countriesMap) {
  console.log(country)
}
```

```sh
(2) ["Finland", "Helsinki"]
(2) ["Sweden", "Stockholm"]
(2) ["Norway", "Oslo"]
```

```js
for (const [country, city] of countriesMap){
 console.log(country, city)
}
```

```sh
Finland Helsinki
Sweden Stockholm
Norway Oslo
```

🌕 Você estabeleceu um grande marco, você é imparável. Continue! Você acabou de completar os desafios do dia 10 e está 10 passos à frente no seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercícios: Nível 1

```js
const a = [4, 5, 8, 9]
const b = [3, 4, 5, 7]
const countries = ['Finland', 'Sweden', 'Norway']
```

1. Crie um set vazio
2. Crie um set contendo de 0 a 10 usando loop
3. Remova um elemento de um set
4. Limpe um set
5. Crie um set de 5 elementos string a partir de um array
6. Crie um map de países e número de caracteres de um país

### Exercícios: Nível 2

1. Encontre a união de a e b
2. Encontre a interseção de a e b
3. Encontre a diferença de a e b

### Exercícios: Nível 3

1. Quantos idiomas existem no objeto countries.

1. \*\*\* Use os dados de países para encontrar os 10 idiomas mais falados:

```js
   // Sua saída deve ser assim
   console.log(mostSpokenLanguages(countries, 10))
   [
     { English: 91 },
     { French: 45 },
     { Arabic: 25 },
     { Spanish: 24 },
     { Russian: 9 },
     { Portuguese: 9 },
     { Dutch: 8 },
     { German: 7 },
     { Chinese: 5 },
     { Swahili: 4 },
     { Serbian: 4 }
   ]

  // Sua saída deve ser assim
  console.log(mostSpokenLanguages(countries, 3))
  [
  {English:91},
  {French:45},
  {Arabic:25}
  ]
```

🎉 PARABÉNS ! 🎉

[<< Dia 9](../Dia_09_Funcoes_Ordem_Superior/dia_09_funcoes_ordem_superior.md) | [Dia 11 >>](../Dia_11_Destructuring_e_Spreading/dia_11_destructuring_e_spreading.md)
