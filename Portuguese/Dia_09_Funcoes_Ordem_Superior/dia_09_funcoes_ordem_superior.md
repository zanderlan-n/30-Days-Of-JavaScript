<div align="center">
  <h1> 30 Dias De JavaScript: Funções de Ordem Superior</h1>
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

[<< Dia 8](../Dia_08_Objetos/dia_08_objetos.md) | [Dia 10 >>](../Dia_10_Sets_e_Maps/dia_10_Sets_e_Maps.md)

![Dia 9](../../images/banners/day_1_9.png)

- [Dia 9](#dia-9)
	- [Funções de Ordem Superior (Higher Order Function)](#funções-de-ordem-superior-higher-order-function)
		- [Callback](#callback)
		- [Retornando função](#retornando-função)
		- [Configuração de tempo](#configuração-de-tempo)
			- [Definindo intervalo com uma função setInterval](#definindo-intervalo-com-uma-função-setinterval)
			- [Definindo tempo com setTimeout](#definindo-tempo-com-settimeout)
	- [Programação Funcional](#programação-funcional)
		- [forEach](#foreach)
		- [map](#map)
		- [filter](#filter)
		- [reduce](#reduce)
		- [every](#every)
		- [find](#find)
		- [findIndex](#findindex)
		- [some](#some)
		- [sort](#sort)
			- [Ordenando valores string](#ordenando-valores-string)
			- [Ordenando valores numéricos](#ordenando-valores-numéricos)
			- [Ordenando arrays de objetos](#ordenando-arrays-de-objetos)
	- [💻 Exercícios](#-exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 9

## Funções de Ordem Superior (Higher Order Function)

Funções de ordem superior (Higher Order Function) são funções que recebem outras funções como parâmetro ou retornam uma função como valor. A função passada como parâmetro é chamada de callback.

### Callback

Um callback é uma função que pode ser passada como parâmetro para outra função. Veja o exemplo abaixo.

```js
// uma função de callback, o nome da função pode ser qualquer nome
const callback = (n) => {
  return n ** 2
}
​
// função que recebe outra função como callback
function cube(callback, n) {
  return callback(n) * n
}
​
console.log(cube(callback, 3))
```

### Retornando função

Funções de ordem superior retornam função como um valor
​
```js
// Função de ordem superior retornando outra função
const higherOrder = n => {
  const doSomething = m => {
    const doWhatEver = t => {
      return 2 * n + 3 * m + t
    }
    return doWhatEver
  }
  return doSomething
}
console.log(higherOrder(2)(3)(10))
```

Vamos ver onde usamos funções de callback. Por exemplo, o método _forEach_ usa callback.

```js
const numbers = [1, 2, 3, 4, 5]
const sumArray = arr => {
  let sum = 0
  const callback = function(element) {
    sum += element
  }
  arr.forEach(callback)
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

O exemplo acima pode ser simplificado como a seguir:

```js
const numbers = [1, 2, 3, 4]

const sumArray = arr => {
  let sum = 0
  arr.forEach(function(element) {
    sum += element
  })
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

### Configuração de tempo

Em JavaScript, podemos executar algumas atividades em um determinado intervalo de tempo ou podemos agendar (esperar) algum tempo para executar algumas atividades.

- setInterval
- setTimeout

#### Definindo intervalo com uma função setInterval

Em JavaScript, usamos a função de ordem superior setInterval para realizar alguma atividade continuamente dentro de um intervalo de tempo. O método global setInterval recebe uma função de callback e uma duração como parâmetro. A duração é em milissegundos e o callback sempre será chamado nesse intervalo de tempo.

```js
// sintaxe
function callback() {
  // código aqui
}
setInterval(callback, duration)
```

```js
function sayHello() {
  console.log('Hello')
}
setInterval(sayHello, 1000) // imprime hello a cada segundo, 1000ms é 1s
```

#### Definindo tempo com setTimeout

Em JavaScript, usamos a função de ordem superior setTimeout para executar alguma ação em algum momento no futuro. O método global setTimeout recebe uma função de callback e uma duração como parâmetro. A duração é em milissegundos e o callback espera por essa quantidade de tempo.

```js
// sintaxe
function callback() {
  // código aqui
}
setTimeout(callback, duration) // duração em milissegundos
```

```js
function sayHello() {
  console.log('Hello')
}
setTimeout(sayHello, 2000) // imprime hello após esperar por 2 segundos.
```

## Programação Funcional

Em vez de escrever loops regulares, as versões mais recentes do JavaScript introduziram vários métodos integrados que podem nos ajudar a resolver problemas complicados. Todos os métodos integrados recebem função de callback. Nesta seção, veremos _forEach_, _map_, _filter_, _reduce_, _find_, _every_, _some_ e _sort_.

### forEach

_forEach_: Itera pelos elementos de um array. Usamos _forEach_ apenas com arrays. Ele recebe uma função de callback com elementos, parâmetro de índice e o próprio array. O índice e o array são opcionais.

```js
arr.forEach(function (element, index, arr) {
  console.log(index, element, arr)
})
// O código acima pode ser escrito usando arrow function
arr.forEach((element, index, arr) => {
  console.log(index, element, arr)
})
// O código acima pode ser escrito usando arrow function e retorno explícito
arr.forEach((element, index, arr) => console.log(index, element, arr))
```

```js
let sum = 0;
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => console.log(num))
console.log(sum)
```

```sh
1
2
3
4
5
0
```

```js
let sum = 0;
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => sum += num)
console.log(sum)
```

```sh
15
```

```js
const countries = ['Finland', 'Denmark', 'Sweden', 'Norway', 'Iceland']
countries.forEach((element) => console.log(element.toUpperCase()))
```

```sh
FINLAND
DENMARK
SWEDEN
NORWAY
ICELAND
```

### map

_map_: Itera pelos elementos de um array e modifica os elementos do array. Ele recebe uma função de callback com elementos, índice, parâmetro de array e retorna um novo array.

```js
const modifiedArray = arr.map(function (element, index, arr) {
  return element
})
```

```js
/*Arrow function e retorno explícito*/
const modifiedArray = arr.map((element,index) => element);
```

```js
//Exemplo
const numbers = [1, 2, 3, 4, 5]
const numbersSquare = numbers.map((num) => num * num)

console.log(numbersSquare)
```

```sh
[1, 4, 9, 16, 25]
```

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const namesToUpperCase = names.map((name) => name.toUpperCase())
console.log(namesToUpperCase)
```

```sh
['ASABENEH', 'MATHIAS', 'ELIAS', 'BROOK']
```

```js
const countries = [
  'Albania',
  'Bolivia',
  'Canada',
  'Denmark',
  'Ethiopia',
  'Finland',
  'Germany',
  'Hungary',
  'Ireland',
  'Japan',
  'Kenya',
]
const countriesToUpperCase = countries.map((country) => country.toUpperCase())
console.log(countriesToUpperCase)

/*
// Arrow function
const countriesToUpperCase = countries.map((country) => {
  return country.toUpperCase();
})
//Retorno explícito
const countriesToUpperCase = countries.map(country => country.toUpperCase());
*/
```

```sh
['ALBANIA', 'BOLIVIA', 'CANADA', 'DENMARK', 'ETHIOPIA', 'FINLAND', 'GERMANY', 'HUNGARY', 'IRELAND', 'JAPAN', 'KENYA']
```

```js
const countriesFirstThreeLetters = countries.map((country) =>
  country.toUpperCase().slice(0, 3)
)
```

```sh
['ALB', 'BOL', 'CAN', 'DEN', 'ETH', 'FIN', 'GER', 'HUN', 'IRE', 'JAP', 'KEN']
```

### filter

_filter_: Filtra itens que satisfazem as condições de filtragem e retorna um novo array.

```js
// Arrow function e retorno explícito
const countriesContainingLand = countries.filter((country) =>
  country.includes('land')
)
console.log(countriesContainingLand)
```

```sh
['Finland', 'Ireland']
```

```js
const countriesEndsByia = countries.filter((country) => country.endsWith('ia'))
console.log(countriesEndsByia)
```

```sh
['Albania', 'Bolivia','Ethiopia']
```

```js
const countriesHaveFiveLetters = countries.filter(
  (country) => country.length === 5
)
console.log(countriesHaveFiveLetters)
```

```sh
['Japan', 'Kenya']
```

```js
const scores = [
  { name: 'Asabeneh', score: 95 },
  { name: 'Lidiya', score: 98 },
  { name: 'Mathias', score: 80 },
  { name: 'Elias', score: 50 },
  { name: 'Martha', score: 85 },
  { name: 'John', score: 100 },
]

const scoresGreaterEighty = scores.filter((score) => score.score > 80)
console.log(scoresGreaterEighty)
```

```sh
[{name: 'Asabeneh', score: 95}, {name: 'Lidiya', score: 98}, {name: 'Martha', score: 85}, {name: 'John', score: 100}]
```

### reduce

_reduce_: Reduce recebe uma função de callback. A função de callback recebe o acumulador, o valor atual e um valor inicial opcional como parâmetros e retorna um único valor. É uma boa prática definir um valor inicial para o acumulador. Se não especificarmos este parâmetro, por padrão o acumulador receberá o `primeiro valor` do array. Se nosso array for um _array vazio_, o `Javascript` lançará um erro.

```js
arr.reduce((acc, cur) => {
  // algum código
}, valorInicial)
```

```js
const numbers = [1, 2, 3, 4, 5]
const sum = numbers.reduce((acc, cur) => acc + cur, 0)

console.log(sum)
```

```sh
15
```

### every

_every_: Verifica se todos os elementos são semelhantes em um aspecto. Retorna booleano

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const areAllStr = names.every((name) => typeof name === 'string') // Are all strings?

console.log(areAllStr)
```

```sh
true
```

```js
const bools = [true, true, true, true]
const areAllTrue = bools.every((b) => b === true) // Are all true? 

console.log(areAllTrue) // true
```

```sh
true
```

### find

_find_: Retorna o primeiro elemento que satisfaz a condição

```js
const ages = [24, 22, 25, 32, 35, 18]
const age = ages.find((age) => age < 20)

console.log(age)
```

```sh
18
```

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const result = names.find((name) => name.length > 7)
console.log(result)
```

```sh
Asabeneh
```

```js
const scores = [
  { name: 'Asabeneh', score: 95 },
  { name: 'Mathias', score: 80 },
  { name: 'Elias', score: 50 },
  { name: 'Martha', score: 85 },
  { name: 'John', score: 100 },
]

const score = scores.find((user) => user.score > 80)
console.log(score)
```

```sh
{ name: "Asabeneh", score: 95 }
```

### findIndex

_findIndex_: Retorna a posição do primeiro elemento que satisfaz a condição

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const ages = [24, 22, 25, 32, 35, 18]

const result = names.findIndex((name) => name.length > 7)
console.log(result) // 0

const age = ages.findIndex((age) => age < 20)
console.log(age) // 5
```

### some

_some_: Verifica se alguns dos elementos são semelhantes em um aspecto. Retorna booleano

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const bools = [true, true, true, true]

const areSomeTrue = bools.some((b) =>  b === true)

console.log(areSomeTrue) //true
```

```js
const areAllStr = names.some((name) => typeof name === 'number') // Are all strings ?
console.log(areAllStr) // false
```

### sort

_sort_: O método de ordenação organiza os elementos do array em ordem ascendente ou descendente. Por padrão, o método **_sort()_** classifica os valores como strings. Isso funciona bem para itens de array de strings, mas não para números. Se os valores numéricos forem classificados como strings, isso nos dará um resultado errado. O método sort modifica o array original. É recomendável copiar os dados originais antes de começar a usar o método _sort_.

#### Ordenando valores string

```js
const products = ['Milk', 'Coffee', 'Sugar', 'Honey', 'Apple', 'Carrot']
console.log(products.sort()) // ['Apple', 'Carrot', 'Coffee', 'Honey', 'Milk', 'Sugar']
// Agora os nomes de produtos estão ordenados em ordem alfabética.
```

#### Ordenando valores numéricos

Como você pode ver no exemplo abaixo, 100 veio primeiro após a ordenação em ordem crescente. O método sort converte os itens em strings, e como '100' e outros números foram comparados, 1 que é o início da string '100' tornou-se o menor. Para evitar isso, usamos uma função de retorno de chamada de comparação dentro do método sort, que retorna um valor negativo, zero ou positivo.

```js
const numbers = [9.81, 3.14, 100, 37]
// Using sort method to sort number items provide a wrong result. see below
console.log(numbers.sort()) //[100, 3.14, 37, 9.81]
numbers.sort(function (a, b) {
  return a - b
})

console.log(numbers) // [3.14, 9.81, 37, 100]

numbers.sort(function (a, b) {
  return b - a
})
console.log(numbers) //[100, 37, 9.81, 3.14]
```

#### Sorting Object Arrays

Sempre que classificamos objetos em um array, usamos a chave do objeto para comparar. Vamos ver o exemplo abaixo.

```js
objArr.sort(function (a, b) {
  if (a.key < b.key) return -1
  if (a.key > b.key) return 1
  return 0
})

// or

objArr.sort(function (a, b) {
  if (a['key'] < b['key']) return -1
  if (a['key'] > b['key']) return 1
  return 0
})

const users = [
  { name: 'Asabeneh', age: 150 },
  { name: 'Brook', age: 50 },
  { name: 'Eyob', age: 100 },
  { name: 'Elias', age: 22 },
]
users.sort((a, b) => {
  if (a.age < b.age) return -1
  if (a.age > b.age) return 1
  return 0
})
console.log(users) // sorted ascending
// [{…}, {…}, {…}, {…}]
```


🌕 Você está fazendo o que está fazendo. Não desista, porque as coisas grandes leva tempo. Você acabou de concluir os desafios do dia 9 e está 9 passos à frente em sua jornada para o grande. Agora faça alguns exercícios para sua mente e para seu músculo.


## 💻 Exercícios

### Exercícios: Nível 1

```js
const countries = ['Finland', 'Sweden', 'Denmark', 'Norway', 'Iceland']
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
const products = [
  { product: 'banana', price: 3 },
  { product: 'mango', price: 6 },
  { product: 'potato', price: ' ' },
  { product: 'avocado', price: 8 },
  { product: 'coffee', price: 10 },
  { product: 'tea', price: '' },
]
```

1. Explique a diferença entre **_forEach, map, filter, and reduce_**.
2. Defina uma função de callback antes de usá-la em forEach, map, filter ou reduce.
3. Use **_forEach_** para exibir no console cada país do array de países.
4. Use **_forEach_** para exibir no console cada nome do array de nomes.
5. Use **_forEach_** para exibir no console cada número do array de números.
6. Use **_map_** para criar um novo array alterando cada país para maiúsculas no array de países.
7. Use **_map_** para criar um array de comprimentos de países a partir do array de países.
8. Use **_map_** para criar um novo array alterando cada número para seu valor ao quadrado no array de números.
9. Use **_map_** para alterar para maiúsculas cada nome no array de nomes.
10. Use **_map_** para mapear os produtos pelo seu preço correspondente.
11. Use **_filter_** para filtrar países que contenham **_land_**.
12. Use **_filter_** para filtrar países com seis caracteres.
13. Use **_filter_** para filtrar países com seis caracteres ou mais a partir do array de países.
14. Use **_filter_** para filtrar países que comecem com 'E'
15. Use **_filter_** para filtrar apenas preços com valores.
16. Declare uma função chamada getStringLists que pega um array como parâmetro e então retorna apenas os itens de string.
17. Use **_reduce_** para somar todos os números no array de números.
18. Use **_reduce_** para concatenar todos os países e produzir esta frase: **_Estonia, Finland, Sweden, Denmark, Norway e Iceland são países do norte da Europa_**
19. Explique a diferença entre **_some_** e **_every_**
20. Use **_some_** para verificar se a comprimento de alguns nomes é maior que sete no array de nomes.
21. Use **_every_** para verificar se todos os países contém a palavra land.
22. Explique a diferença entre **_find_** e **_findIndex_**.
23. Use **_find_** para encontrar o primeiro país contendo apenas seis letras no array de países.
24. Use **_findIndex_** para encontrar a posição do primeiro país contendo apenas seis letras no array de países.
25. Use **_findIndex_** para encontrar a posição da **_Norway_** se ela existir no array de países. Se não existir, retorne -1.
26. Use **_findIndex_** para encontrar a posição da **_Russia_** se ela existir no array de países. Se não existir, retorne -1.

### Exercícios: Nível 2

1. Encontre o preço total dos produtos encadeando dois ou mais iteradores de array (ex. arr.map(callback).filter(callback).reduce(callback))
1. Encontre a soma dos preços dos produtos usando apenas reduce(callback))
1. Declare uma função chamada **_categorizeCountries_** que retorna um array de países que têm algum padrão comum (você encontra o array de países neste repositório como countries.js (ex. 'land', 'ia', 'island', 'stan')).
1. Crie uma função que retorna um array de objetos, que é a letra e o número de vezes que a letra é usada para começar o nome de um país.
1. Declare uma função **_getFirstTenCountries_** e retorne um array de dez países. Use diferentes técnicas de programação funcional para trabalhar no array countries.js
1. Declare uma função **_getLastTenCountries_** que retorna os últimos dez países no array de países.
1. Descubra qual _letra_ é usada muitas _vezes_ como inicial para um nome de país do array de países (ex. Finlândia, Fiji, França etc)

### Exercícios: Nível 3

1. Use as informações dos países na pasta de dados. Classifique os países por nome, capital, população.
1. \*\*\* Encontre os 10 idiomas mais falados:

   ````js
   // Your output should look like this
   console.log(mostSpokenLanguages(countries, 10))
   [
   {country: 'English',count:91},
   {country: 'French',count:45},
   {country: 'Arabic',count:25},
   {country: 'Spanish',count:24},
   {country:'Russian',count:9},
   {country:'Portuguese', count:9},
   {country:'Dutch',count:8},
   {country:'German',count:7},
   {country:'Chinese',count:5},
   {country:'Swahili',count:4}
   ]

   // Your output should look like this
   console.log(mostSpokenLanguages(countries, 3))
   [
   {country: 'English',count: 91},
   {country: 'French',count: 45},
   {country: 'Arabic',count: 25},
   ]```

   ````

2. \*\*\* Use o arquivo countries_data.js para criar uma função que crie os dez países mais populosos

   ````js
   console.log(mostPopulatedCountries(countries, 10))

   [
   {country: 'China', population: 1377422166},
   {country: 'India', population: 1295210000},
   {country: 'United States of America', population: 323947000},
   {country: 'Indonesia', population: 258705000},
   {country: 'Brazil', population: 206135893},
   {country: 'Pakistan', population: 194125062},
   {country: 'Nigeria', population: 186988000},
   {country: 'Bangladesh', population: 161006790},
   {country: 'Russian Federation', population: 146599183},
   {country: 'Japan', population: 126960000}
   ]

   console.log(mostPopulatedCountries(countries, 3))
   [
   {country: 'China', population: 1377422166},
   {country: 'India', population: 1295210000},
   {country: 'United States of America', population: 323947000}
   ]
   ```

   ````

3. \*\*\* Tente desenvolver um programa que calcule a medida de tendência central de uma amostra (média, mediana, moda) e medida de variabilidade (amplitude, variância, desvio padrão). Além dessas medidas, encontre o mínimo, máximo, contagem, percentil e distribuição de frequência da amostra. Você pode criar um objeto chamado estatísticas e criar todas as funções que realizam cálculos estatísticos como métodos para o objeto estatísticas. Verifique o resultado abaixo.

   ```js
   const ages = [31, 26, 34, 37, 27, 26, 32, 32, 26, 27, 27, 24, 32, 33, 27, 25, 26, 38, 37, 31, 34, 24, 33, 29, 26]

   console.log('Count:', statistics.count()) // 25
   console.log('Sum: ', statistics.sum()) // 744
   console.log('Min: ', statistics.min()) // 24
   console.log('Max: ', statistics.max()) // 38
   console.log('Range: ', statistics.range() // 14
   console.log('Mean: ', statistics.mean()) // 30
   console.log('Median: ',statistics.median()) // 29
   console.log('Mode: ', statistics.mode()) // {'mode': 26, 'count': 5}
   console.log('Variance: ',statistics.var()) // 17.5
   console.log('Standard Deviation: ', statistics.std()) // 4.2
   console.log('Variance: ',statistics.var()) // 17.5
   console.log('Frequency Distribution: ',statistics.freqDist()) # [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
   ```

   ```sh
   console.log(statistics.describe())
   Count: 25
   Sum:  744
   Min:  24
   Max:  38
   Range:  14
   Mean:  30
   Median:  29
   Mode:  (26, 5)
   Variance:  17.5
   Standard Deviation:  4.2
   Frequency Distribution: [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
   ```

🎉 CONGRATULATIONS ! 🎉

[<< Dia 8](../Dia_08_Objetos/dia_08_objetos.md) | [Dia 10 >>](../Dia_10_Sets_e_Maps/dia_10_Sets_e_Maps.md)
