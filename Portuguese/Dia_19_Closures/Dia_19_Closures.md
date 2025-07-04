<div align="center">
  <h1> 30 Dias De JavaScript: Closures</h1>
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

[<< Dia 18](../Dia_18_Promises/Dia_18_Promises.md) | [Dia 20 >>](../Dia_20_Escrevendo_Codigo_Limpo/Dia_20_Escrevendo_Codigo_Limpo.md)

![Trinta Dias De JavaScript](../images/banners/day_1_19.png)
- [Dia 19](#dia-19)
	- [Closure](#closure)
	- [Exercícios](#exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 19

## Closure

JavaScript permite escrever uma função dentro de uma função externa. Podemos escrever quantas funções internas quisermos. Se a função interna acessar as variáveis da função externa, isso é chamado de closure.

```js
function outerFunction() {
    let count = 0;
    function innerFunction() {
        count++
        return count
    }

    return innerFunction
}
const innerFunc = outerFunction()

console.log(innerFunc())
console.log(innerFunc())
console.log(innerFunc())
```

```sh
1
2
3
```

Vejamos mais exemplos de funções internas

```js
function outerFunction() {
    let count = 0;
    function plusOne() {
        count++
        return count
    }
    function minusOne() {
        count--
        return count
    }

    return {
        plusOne:plusOne(),
        minusOne:minusOne()
    }
}
const innerFuncs = outerFunction()

console.log(innerFuncs.plusOne)
console.log(innerFuncs.minusOne)
```

```sh
1
0
```

🌕 Você está progredindo. Mantenha seu ritmo, continue o bom trabalho. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercícios: Nível 1

1. Crie uma closure que tenha uma função interna.

### Exercícios: Nível 2

1. Crie uma closure que tenha três funções internas.

### Exercícios: Nível 3

1. Crie uma função externa personAccount. Ela possui variáveis internas firstname, lastname, incomes, expenses. Ela possui funções internas totalIncome, totalExpense, accountInfo,addIncome, addExpense e accountBalance. Incomes é um conjunto de rendas e sua descrição e expenses é também um conjunto de despesas e sua descrição.

🎉 PARABÉNS ! 🎉

[<< Dia 18](../Dia_18_Promises/Dia_18_Promises.md) | [Dia 20 >>](../Dia_20_Escrevendo_Codigo_Limpo/Dia_20_Escrevendo_Codigo_Limpo.md)
