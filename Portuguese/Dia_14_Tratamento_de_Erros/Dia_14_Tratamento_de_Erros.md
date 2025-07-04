<div align="center">
  <h1> 30 Dias De JavaScript: Tratamento de Erros</h1>
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

[<< Dia 13](../Dia_13_Console_Object_Methods/Dia_13_Console_Object_Methods.md) | [Dia 15 >>](../Dia_15_Classes/Dia_15_Classes.md)

![Trinta Dias De JavaScript](../images/banners/day_1_14.png)

- [Dia 14](#dia-14)
	- [Tratamento de Erros](#tratamento-de-erros)
		- [Tipos de Erro](#tipos-de-erro)
	- [Exercícios](#exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 14

## Tratamento de Erros

JavaScript é uma linguagem de tipagem fraca. Algumas vezes você receberá um erro em tempo de execução quando tentar acessar uma variável não definida ou chamar uma função não definida etc.

JavaScript, semelhante ao Python ou Java, fornece um mecanismo de tratamento de erros para capturar erros em tempo de execução usando o bloco try-catch-finally.

```js
try {
  // código que pode lançar um erro
} catch (err) {
  // código a ser executado se ocorrer um erro
} finally {
  // código a ser executado independentemente de ocorrer ou não um erro
}
```

**try**: envolva o código suspeito que pode lançar um erro no bloco try. A instrução try nos permite definir um bloco de código a ser testado quanto a erros enquanto está sendo executado.

**catch**: escreva o código para fazer algo no bloco catch quando ocorrer um erro. O bloco catch pode ter parâmetros que fornecerão informações sobre o erro. O bloco catch é usado para registrar um erro ou exibir mensagens específicas para o usuário.

**finally**: o bloco finally sempre será executado independentemente da ocorrência de um erro. O bloco finally pode ser usado para concluir a tarefa restante ou redefinir variáveis que podem ter sido alteradas antes que o erro ocorresse no bloco try.

**Exemplo:**

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.log(err)
}
```

```sh
ReferenceError: fistName is not defined
    at <anonymous>:4:20
```

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.error(err) // podemos usar console.log() ou console.error()
} finally {
  console.log('De qualquer forma, serei executado')
}
```

```sh
ReferenceError: fistName is not defined
    at <anonymous>:4:20
De qualquer forma, serei executado
```
O bloco catch recebe um parâmetro. É comum passar e, err ou error como parâmetro para o bloco catch. Este parâmetro é um objeto e possui as chaves name e message. Vamos usar name e message.
```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.log('Nome do erro', err.name)
  console.log('Mensagem de erro', err.message)
} finally {
  console.log('De qualquer forma, serei executado')
}
```
```sh
Nome do erro ReferenceError
Mensagem de erro fistName is not defined
De qualquer forma, serei executado
```
throw: a instrução throw nos permite criar um erro personalizado. Podemos lançar uma string, número, booleano ou um objeto. Use a instrução throw para lançar uma exceção. Quando você lança uma exceção, a expressão especifica o valor da exceção. Cada um dos seguintes lança uma exceção:
```js
throw 'Error2' // gera uma exceção com um valor de string
throw 42 // gera uma exceção com o valor 42
throw true // gera uma exceção com o valor true
throw new Error('Required') // gera um objeto de erro com a mensagem de Required
```
```js
const throwErrorExampleFun = () => {
  let message
  let x = prompt('Digite um número: ')
  try {
    if (x == '') throw 'vazio'
    if (isNaN(x)) throw 'não é um número'
    x = Number(x)
    if (x < 5) throw 'muito baixo'
    if (x > 10) throw 'muito alto'
  } catch (err) {
    console.log(err)
  }
}
throwErrorExampleFun()
```
### Tipos de Erro
- ReferenceError: Ocorreu uma referência ilegal. Um ReferenceError é lançado se usarmos uma variável que não foi declarada.
```js
let firstName = 'Asabeneh'
let fullName = firstName + ' ' + lastName
console.log(fullName)
```
```sh
Uncaught ReferenceError: lastName is not defined
    at <anonymous>:2:35
```
- SyntaxError: Ocorreu um erro de sintaxe
```js
let square = 2 x 2
console.log(square)
console.log('Hello, world")
```
```sh
Uncaught SyntaxError: Unexpected identifier
```
- TypeError: Ocorreu um erro de tipo
```js
let num = 10
console.log(num.toLowerCase())
```
```sh
Uncaught TypeError: num.toLowerCase is not a function
    at <anonymous>:2:17
```
Estes são alguns dos erros comuns que você pode enfrentar ao escrever código. Entender os erros pode ajudá-lo a saber quais erros você cometeu e isso o ajudará a depurar seu código rapidamente.
🌕 Você é impecável. Agora, você sabe como lidar com erros e pode escrever aplicações robustas que lidam com entradas inesperadas do usuário. Você acabou de completar os desafios do dia 14 e está 14 passos à frente em seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.
## Exercícios
### Exercícios: Nível 1
Pratique
### Exercícios: Nível 2
Pratique
### Exercícios: Nível 3
Pratique
🎉 PARABÉNS ! 🎉
[<< Dia 13](../Dia_13_Console_Object_Methods/Dia_13_Console_Object_Methods.md) | [Dia 15 >>](../Dia_15_Classes/Dia_15_Classes.md)
