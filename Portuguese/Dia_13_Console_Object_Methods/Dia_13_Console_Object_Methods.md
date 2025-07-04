<div align="center">
  <h1> 30 Dias De JavaScript: Métodos do Objeto Console</h1>
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

[<< Dia 12](../Dia_12_Expressoes_Regulares/Dia_12_Expressoes_Regulares.md) | [Dia 14 >>](../Dia_14_Tratamento_de_Erros/Dia_14_Tratamento_de_Erros.md)

![Trinta Dias De JavaScript](../images/banners/day_1_13.png)

- [Dia 13](#dia-13)
	- [Métodos do Objeto Console](#métodos-do-objeto-console)
		- [console.log()](#consolelog)
		- [console.warn()](#consolewarn)
		- [console.error()](#consoleerror)
		- [console.table()](#consoletable)
		- [console.time()](#consoletime)
		- [console.info()](#consoleinfo)
		- [console.assert()](#consoleassert)
		- [console.group()](#consolegroup)
		- [console.count()](#consolecount)
		- [console.clear()](#consoleclear)
	- [Exercícios](#exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 13

## Métodos do Objeto Console

Nesta seção, abordaremos os métodos do objeto console. Iniciantes absolutos geralmente não sabem qual usar: console.log(), document.write() ou document.getElementById.

Usamos os métodos do objeto console para mostrar a saída no console do navegador e usamos document.write para mostrar a saída no documento do navegador (janela de visualização). Ambos os métodos são usados apenas para fins de teste e depuração. O método console é a ferramenta de teste e depuração mais popular no navegador. Usamos document.getElementById() quando gostamos de interagir com o DOM usando JavaScript. Abordaremos o DOM em outra seção.

Além do famoso método console.log(), o console fornece outros métodos.

### console.log()

Usamos console.log() para mostrar a saída no console do navegador. Podemos substituir valores e também podemos estilizar a saída de log usando %c.

- Mostrando saída no console do navegador

```js
console.log('30 Dias de JavaScript')
```

```sh
30 Dias de JavaScript
```

- Substituição

```js
console.log('%d %s de JavaScript', 30, 'Dias')
```

```sh
30 Dias de JavaScript
```

- CSS

Podemos estilizar a mensagem de log usando css. Copie o seguinte código e cole-o no console do navegador para ver o resultado.

```js
console.log('%c30 Dias De JavaScript', 'color:green') // a saída do log é verde
console.log(
  '%c30 Dias%c %cDe%c %cJavaScript%c',
  'color:green',
  '',
  'color:red',
  '',
  'color:yellow'
) // a saída do log tem texto verde, vermelho e amarelo
```

### console.warn()

Usamos console.warn() para dar avisos no navegador. Por exemplo, para informar ou avisar sobre a descontinuação da versão de um pacote ou más práticas. Copie o seguinte código e cole-o no console do navegador para ver as mensagens de aviso.

```js
console.warn('Isto é um aviso')
console.warn(
  'Você está usando React. Não toque no DOM. O DOM Virtual cuidará do manuseio do DOM!'
)
console.warn('Aviso é diferente de erro')
```

### console.error()

O método console.error() mostra mensagens de erro.

```js
console.error('Esta é uma mensagem de erro')
console.error('Todos nós cometemos erros')
```

### console.table()

O método console.table() exibe dados como uma tabela no console. Exibe dados tabulares como uma tabela. O console.table() recebe um argumento obrigatório de dados, que deve ser um array ou um objeto, e um parâmetro opcional adicional de colunas.

Vamos começar com um array simples. O código abaixo exibe uma tabela com duas colunas. Uma coluna de índice para exibir o índice e uma coluna de valor para exibir os nomes.

```js
const names = ['Asabeneh', 'Brook', 'David', 'John']
console.table(names)
```

Vamos também verificar o resultado de um objeto. Isso cria uma tabela com duas colunas: uma coluna de índice contendo as chaves e uma coluna de valor contendo os valores do objeto.

```js
const user = {
  name: 'Asabeneh',
  title: 'Programador',
  country: 'Finlândia',
  city: 'Helsinki',
  age: 250
}
console.table(user)
```

Verifique o restante dos exemplos copiando e colando no console do navegador.

```js
const countries = [
  ['Finlândia', 'Helsinki'],
  ['Suécia', 'Estocolmo'],
  ['Noruega', 'Oslo']
]
console.table(countries)
```

```js
const users = [
  {
    name: 'Asabeneh',
    title: 'Programador',
    country: 'Finlândia',
    city: 'Helsinki',
    age: 250
  },
  {
    name: 'Eyob',
    title: 'Professor',
    country: 'Suécia',
    city: 'Londres',
    age: 25
  },
  {
    name: 'Asab',
    title: 'Instrutor',
    country: 'Noruega',
    city: 'Oslo',
    age: 22
  },
  {
    name: 'Matias',
    title: 'Desenvolvedor',
    country: 'Dinamarca',
    city: 'Copenhagen',
    age: 28
  }
]
console.table(users)
```

### console.time()

Inicia um cronômetro que você pode usar para rastrear quanto tempo uma operação leva. Você dá a cada cronômetro um nome exclusivo e pode ter até 10.000 cronômetros em execução em uma determinada página. Quando você chama console.timeEnd() com o mesmo nome, o navegador exibirá o tempo, em milissegundos, que decorreu desde o início do cronômetro.

```js
const countries = [
  ['Finlândia', 'Helsinki'],
  ['Suécia', 'Estocolmo'],
  ['Noruega', 'Oslo']
]

console.time('Loop for regular')
for (let i = 0; i < countries.length; i++) {
  console.log(countries[i][0], countries[i][1])
}
console.timeEnd('Loop for regular')

console.time('Loop for of')
for (const [name, city] of countries) {
  console.log(name, city)
}
console.timeEnd('Loop for of')

console.time('Loop forEach')
countries.forEach(([name, city]) => {
  console.log(name, city)
})
console.timeEnd('Loop forEach')
```

```sh
Finlândia Helsinki
Suécia Estocolmo
Noruega Oslo
Loop for regular: 0.34716796875ms
Finlândia Helsinki
Suécia Estocolmo
Noruega Oslo
Loop for of: 0.26806640625ms
Finlândia Helsinki
Suécia Estocolmo
Noruega Oslo
Loop forEach: 0.358154296875ms
```

De acordo com a saída acima, o loop for regular é mais lento que o loop for of ou forEach.

### console.info()

Ele exibe uma mensagem de informação no console do navegador.

```js
console.info('O desafio 30 Dias De JavaScript é tendência no Github')
console.info('O desafio 30 Dias De fullStack pode ser lançado')
console.info('O desafio 30 Dias De HTML e CSS pode ser lançado')
```

### console.assert()

Os métodos console.assert() gravam uma mensagem de erro no console se a asserção for falsa. Se a asserção for verdadeira, nada acontece. O primeiro parâmetro é uma expressão de asserção. Se esta expressão for falsa, uma mensagem de erro Falha na asserção será exibida.

```js
console.assert(4 > 3, '4 é maior que 3') // nenhum resultado
console.assert(3 > 4, '3 não é maior que 4') // Falha na asserção: 3 não é maior que 4

for (let i = 0; i <= 10; i += 1) {
  let errorMessage = `${i} não é par`
  console.log('o # é ' + i)
  console.assert(i % 2 === 0, { number: i, errorMessage: errorMessage })
}
```

### console.group()

O console.group() pode ajudar a agrupar diferentes grupos de log. Copie o seguinte código e cole-o no console do navegador para ver os grupos.

```js
const names = ['Asabeneh', 'Brook', 'David', 'John']
const countries = [
  ['Finlândia', 'Helsinki'],
  ['Suécia', 'Estocolmo'],
  ['Noruega', 'Oslo']
]
const user = {
  name: 'Asabeneh',
  title: 'Programador',
  country: 'Finlândia',
  city: 'Helsinki',
  age: 250
}
const users = [
  {
    name: 'Asabeneh',
    title: 'Programador',
    country: 'Finlândia',
    city: 'Helsinki',
    age: 250
  },
  {
    name: 'Eyob',
    title: 'Professor',
    country: 'Suécia',
    city: 'Londres',
    age: 25
  },
  {
    name: 'Asab',
    title: 'Instrutor',
    country: 'Noruega',
    city: 'Oslo',
    age: 22
  },
  {
    name: 'Matias',
    title: 'Desenvolvedor',
    country: 'Dinamarca',
    city: 'Copenhagen',
    age: 28
  }
]

console.group('Nomes')
console.log(names)
console.groupEnd()

console.group('Países')
console.log(countries)
console.groupEnd()

console.group('Usuários')
console.log(user)
console.log(users)
console.groupEnd()
```

### console.count()

Ele imprime o número de vezes que console.count() é chamado. Ele recebe um parâmetro de rótulo de string. É muito útil para contar o número de vezes que uma função é chamada. No exemplo a seguir, o método console.count() será executado três vezes.

```js
const func = () => {
  console.count('A função foi chamada')
}
func()
func()
func()
```

```sh
A função foi chamada: 1
A função foi chamada: 2
A função foi chamada: 3
```

### console.clear()

O console.clear() limpa o console do navegador.

🌕 Continue o bom trabalho. Continue se esforçando, o céu é o limite! Você acabou de completar os desafios do dia 13 e está 13 passos à frente em seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercícios: Nível 1

1.  Exiba o array de países como uma tabela
2.  Exiba o objeto de países como uma tabela
3.  Use console.group() para agrupar logs

### Exercícios: Nível 2

1. 10 > 2 \* 10 use console.assert()
2. Escreva uma mensagem de aviso usando console.warn()
3. Escreva uma mensagem de erro usando console.error()

### Exercícios: Nível 3

1. Verifique a diferença de velocidade entre os seguintes loops: while, for, for of, forEach

🎉 PARABÉNS ! 🎉

[<< Dia 12](../Dia_12_Expressoes_Regulares/Dia_12_Expressoes_Regulares.md) | [Dia 14 >>](../Dia_14_Tratamento_de_Erros/Dia_14_Tratamento_de_Erros.md)
