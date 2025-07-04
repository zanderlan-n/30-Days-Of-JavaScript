<div align="center">
  <h1> 30 Dias De JavaScript: Document Object Model(DOM)</h1>
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

[<< Dia 20](../Dia_20_Escrevendo_Codigo_Limpo/Dia_20_Escrevendo_Codigo_Limpo.md) | [Dia 22 >>](../Dia_22_Manipulando_DOM/Dia_22_Manipulando_DOM.md)

![Trinta Dias De JavaScript](../images/banners/day_1_21.png)

- [Dia 21](#dia-21)
	- [Document Object Model (DOM) - Dia 1](#document-object-model-dom---dia-1)
		- [Obtendo Elemento](#obtendo-elemento)
			- [Obtendo elementos pelo nome da tag](#obtendo-elementos-pelo-nome-da-tag)
			- [Obtendo elementos pelo nome da classe](#obtendo-elementos-pelo-nome-da-classe)
			- [Obtendo um elemento pelo id](#obtendo-um-elemento-pelo-id)
			- [Obtendo elementos usando métodos querySelector](#obtendo-elementos-usando-métodos-queryselector)
		- [Adicionando atributo](#adicionando-atributo)
			- [Adicionando atributo usando setAttribute](#adicionando-atributo-usando-setattribute)
			- [Adicionando atributo sem setAttribute](#adicionando-atributo-sem-setattribute)
			- [Adicionando classe usando classList](#adicionando-classe-usando-classlist)
			- [Removendo classe usando remove](#removendo-classe-usando-remove)
		- [Adicionando Texto ao elemento HTML](#adicionando-texto-ao-elemento-html)
			- [Adicionando conteúdo de texto usando textContent](#adicionando-conteúdo-de-texto-usando-textcontent)
			- [Adicionando Conteúdo de Texto usando innerHTML](#adicionando-conteúdo-de-texto-usando-innerhtml)
				- [Conteúdo de Texto](#conteúdo-de-texto)
				- [HTML Interno](#html-interno)
		- [Adicionando estilo](#adicionando-estilo)
			- [Adicionando Cor de Estilo](#adicionando-cor-de-estilo)
			- [Adicionando Cor de Fundo de Estilo](#adicionando-cor-de-fundo-de-estilo)
			- [Adicionando Tamanho da Fonte de Estilo](#adicionando-tamanho-da-fonte-de-estilo)
	- [Exercícios](#exercícios)
		- [Exercício: Nível 1](#exercício-nível-1)
		- [Exercício: Nível 2](#exercício-nível-2)
		- [Exercício: Nível 3](#exercício-nível-3)
			- [DOM: Mini projeto 1](#dom-mini-projeto-1)

# Dia 21

## Document Object Model (DOM) - Dia 1

O documento HTML é estruturado como um Objeto JavaScript. Todo elemento HTML possui propriedades diferentes que podem ajudar a manipulá-lo. É possível obter, criar, anexar ou remover elementos HTML usando JavaScript. Verifique os exemplos abaixo. Selecionar um elemento HTML usando JavaScript é semelhante a selecionar usando CSS. Para selecionar um elemento HTML, usamos nome da tag, id, nome da classe ou outros atributos.

### Obtendo Elemento

Podemos acessar elementos já criados usando JavaScript. Para acessar ou obter elementos, usamos métodos diferentes. O código abaixo possui quatro elementos _h1_. Vejamos os diferentes métodos para acessar os elementos _h1_.

```html
<!DOCTYPE html>
  <html lang="en">
    <head>
      <title>Document Object Model</title>
    </head>
    <body>

     <h1 class='title' id='first-title'>Primeiro Título</h1>
     <h1 class='title' id='second-title'>Segundo Título</h1>
     <h1 class='title' id='third-title'>Terceiro Título</h1>
     <h1></h1>

    </body>
  </html>
```

#### Obtendo elementos pelo nome da tag

**_getElementsByTagName()_**: recebe um nome de tag como parâmetro de string e este método retorna um objeto HTMLCollection. Um HTMLCollection é um objeto semelhante a um array de elementos HTML. A propriedade length fornece o tamanho da coleção. Sempre que usamos este método, acessamos os elementos individuais usando índice ou após percorrer cada item individual. Um HTMLCollection não suporta todos os métodos de array, portanto, devemos usar o loop for regular em vez de forEach.

```js
// sintaxe
document.getElementsByTagName('nomedatag')
```

```js
const allTitles = document.getElementsByTagName('h1')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // imprime cada elemento no HTMLCollection
}
```

#### Obtendo elementos pelo nome da classe

O método **_getElementsByClassName()_** retorna um objeto HTMLCollection. Um HTMLCollection é uma lista semelhante a um array de elementos HTML. A propriedade length fornece o tamanho da coleção. É possível percorrer todos os elementos HTMLCollection. Veja o exemplo abaixo.

```js
//sintaxe
document.getElementsByClassName('nomedaclasse')
```

```js
const allTitles = document.getElementsByClassName('title')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // imprime cada elemento no HTMLCollection
}
```

#### Obtendo um elemento pelo id

**_getElementById()_** (e não getElementsById) visa um único elemento HTML. Passamos o id sem # como argumento.

```js
//sintaxe
document.getElementById('id')
```

```js
let firstTitle = document.getElementById('first-title')
console.log(firstTitle) // <h1>Primeiro Título</h1>
```

#### Obtendo elementos usando métodos querySelector

O método _document.querySelector_ pode selecionar um elemento HTML ou elementos HTML pelo nome da tag, por id ou por nome de classe.

**_querySelector_**: pode ser usado para selecionar um elemento HTML por seu nome de tag, id ou classe. Se o nome da tag for usado, ele seleciona apenas o primeiro elemento.

```js
let firstTitle = document.querySelector('h1') // seleciona o primeiro elemento h1 disponível
let firstTitle = document.querySelector('#first-title') // seleciona o id com first-title
let firstTitle = document.querySelector('.title') // seleciona o primeiro elemento disponível com a classe title
```

**_querySelectorAll_**: pode ser usado para selecionar elementos html por seu nome de tag ou classe. Ele retorna um nodeList, que é um objeto semelhante a um array que suporta métodos de array. Podemos usar **_for loop_** ou **_forEach_** para percorrer cada elemento do nodeList.

```js
const allTitles = document.querySelectorAll('h1') // seleciona todos os elementos h1 disponíveis na página

console.log(allTitles.length) // 4
for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i])
}

allTitles.forEach(title => console.log(title))
const allTitles = document.querySelectorAll('.title') // o mesmo vale para selecionar usando classe
```

### Adicionando atributo

Um atributo é adicionado na tag de abertura do HTML, o que fornece informações adicionais sobre o elemento. Atributos HTML comuns: id, class, src, style, href, disabled, title, alt. Vamos adicionar id e classe para o quarto título.

```js
const titles = document.querySelectorAll('h1')
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

#### Adicionando atributo usando setAttribute

O método **_setAttribute()_** define qualquer atributo html. Ele recebe dois parâmetros: o tipo do atributo e o nome do atributo.
Vamos adicionar os atributos de classe e id para o quarto título.

```js
const titles = document.querySelectorAll('h1')
titles[3].setAttribute('class', 'title')
titles[3].setAttribute('id', 'fourth-title')
```

#### Adicionando atributo sem setAttribute

Podemos usar o método normal de configuração de objeto para definir um atributo, mas isso não funciona para todos os elementos. Alguns atributos são propriedades de objeto DOM e podem ser definidos diretamente. Por exemplo, id e class.

```js
//outra forma de definir um atributo
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

#### Adicionando classe usando classList

O método classList é um bom método para anexar classes adicionais. Ele não substitui a classe original se uma classe existir, mas adiciona classes adicionais ao elemento.

```js
//outra forma de definir um atributo: anexa a classe, não substitui
titles[3].classList.add('title', 'header-title')
```

#### Removendo classe usando remove

Semelhante à adição, também podemos remover classes de um elemento. Podemos remover uma classe específica de um elemento.

```js
//outra forma de definir um atributo: anexa a classe, não substitui
titles[3].classList.remove('title', 'header-title')
```

### Adicionando Texto ao elemento HTML

Um HTML é um bloco de construção de uma tag de abertura, uma tag de fechamento e um conteúdo de texto. Podemos adicionar um conteúdo de texto usando a propriedade _textContent_ ou \*innerHTML.

#### Adicionando conteúdo de texto usando textContent

A propriedade _textContent_ é usada para adicionar texto a um elemento HTML.

```js
const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Quarto Título'
```

#### Adicionando Conteúdo de Texto usando innerHTML

A maioria das pessoas se confunde entre _textContent_ e _innerHTML_. _textContent_ destina-se a adicionar texto a um elemento HTML, no entanto, innerHTML pode adicionar um texto ou elemento HTML ou elementos como filho.

##### Conteúdo de Texto

Atribuímos a propriedade de objeto HTML *textContent* a um texto.

```js
const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Quarto Título'
```

##### HTML Interno

Usamos a propriedade innerHTML quando queremos substituir ou adicionar um conteúdo filho completamente novo a um elemento pai.
O valor que atribuímos será uma string de elementos HTML.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript para Todos:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Desafios de Asabeneh Yetayeh em 2020</h1>
        <h2>Desafio 30DiasDeJavaScript</h2>
        <ul></ul>
    </div>
    <script>
    const lists = `
    <li>Desafio 30DiasDePython Concluído</li>
            <li>Desafio 30DiasDeJavaScript em Andamento</li>
            <li>Desafio 30DiasOfReact Próximo</li>
            <li>Desafio 30DiasDeFullStack Próximo</li>
            <li>Desafio 30DiasDeAnaliseDeDados Próximo</li>
            <li>Desafio 30DiasDeReactNative Próximo</li>
            <li>Desafio 30DiasDeMachineLearning Próximo</li>`
  const ul = document.querySelector('ul')
  ul.innerHTML = lists
    </script>
  </body>
</html>
```

A propriedade innerHTML também pode nos permitir remover todos os filhos de um elemento pai. Em vez de usar removeChild(), recomendo o seguinte método.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript para Todos:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Desafios de Asabeneh Yetayeh em 2020</h1>
        <h2>Desafio 30DiasDeJavaScript</h2>
        <ul>
            <li>Desafio 30DiasDePython Concluído</li>
            <li>Desafio 30DiasDeJavaScript em Andamento</li>
            <li>Desafio 30DiasOfReact Próximo</li>
            <li>Desafio 30DiasDeFullStack Próximo</li>
            <li>Desafio 30DiasDeAnaliseDeDados Próximo</li>
            <li>Desafio 30DiasDeReactNative Próximo</li>
            <li>Desafio 30DiasDeMachineLearning Próximo</li>
        </ul>
    </div>
    <script>
  const ul = document.querySelector('ul')
  ul.innerHTML = ''
    </script>
  </body>
</html>
```

### Adicionando estilo

#### Adicionando Cor de Estilo

Vamos adicionar algum estilo aos nossos títulos. Se o elemento tiver índice par, damos a cor verde, caso contrário, vermelho.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // todos os títulos terão tamanho de fonte de 24px
  if (i % 2 === 0) {
    title.style.color = 'green'
  } else {
    title.style.color = 'red'
  }
})
```

#### Adicionando Cor de Fundo de Estilo

Vamos adicionar algum estilo aos nossos títulos. Se o elemento tiver índice par, damos a cor verde, caso contrário, vermelho.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // todos os títulos terão tamanho de fonte de 24px
  if (i % 2 === 0) {
    title.style.backgroundColor = 'green'
  } else {
    title.style.backgroundColor = 'red'
  }
})
```

#### Adicionando Tamanho da Fonte de Estilo

Vamos adicionar algum estilo aos nossos títulos. Se o elemento tiver índice par, damos 20px, caso contrário, 30px.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // todos os títulos terão tamanho de fonte de 24px
  if (i % 2 === 0) {
    title.style.fontSize = '20px'
  } else {
    title.style.fontSize = '30px'
  }
})
```

Como você deve ter notado, as propriedades do CSS, quando as usamos em JavaScript, se tornam camelCase. As seguintes propriedades CSS mudam de background-color para backgroundColor, font-size para fontSize, font-family para fontFamily, margin-bottom para marginBottom.

---

🌕 Agora, você está totalmente carregado com um superpoder, você completou a parte mais importante e desafiadora do desafio e, em geral, do JavaScript. Você aprendeu DOM e agora tem a capacidade de construir e desenvolver aplicativos. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercício: Nível 1

1. Crie um arquivo index.html e coloque quatro elementos p como acima: Obtenha o primeiro parágrafo usando **_document.querySelector(tagname)_** e o nome da tag.
2. Obtenha cada um dos parágrafos usando **_document.querySelector('#id')_** e por seu id.
3. Obtenha todos os p como nodeList usando **_document.querySelectorAll(tagname)_** e por seu nome de tag.
4. Percorra o nodeList e obtenha o conteúdo de texto de cada parágrafo.
5. Defina um conteúdo de texto para o quarto parágrafo, **_Quarto Parágrafo_**.
6. Defina os atributos id e class para todos os parágrafos usando diferentes métodos de configuração de atributos.

### Exercício: Nível 2

1. Altere o estilo de cada parágrafo usando JavaScript (ex: cor, fundo, borda, tamanho da fonte, família da fonte).
2. Selecione todos os parágrafos e percorra cada elemento, dando ao primeiro e terceiro parágrafos a cor verde, e ao segundo e quarto parágrafos a cor vermelha.
3. Defina o conteúdo do texto, id e classe para cada parágrafo.

### Exercício: Nível 3

#### DOM: Mini projeto 1

1. Desenvolva o seguinte aplicativo, use os seguintes elementos HTML para começar. Você obterá o mesmo código na pasta inicial. Aplique todos os estilos e funcionalidades usando apenas JavaScript.

   - A cor do ano muda a cada 1 segundo
   - A cor de fundo da data e hora muda a cada segundo
   - O desafio concluído tem fundo verde
   - O desafio em andamento tem fundo amarelo
   - Os próximos desafios têm fundo vermelho

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript para Todos:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Desafios de Asabeneh Yetayeh em 2020</h1>
        <h2>Desafio 30DiasDeJavaScript</h2>
        <ul>
            <li>Desafio 30DiasDePython Concluído</li>
            <li>Desafio 30DiasDeJavaScript em Andamento</li>
            <li>Desafio 30DiasOfReact Próximo</li>
            <li>Desafio 30DiasDeFullStack Próximo</li>
            <li>Desafio 30DiasDeAnaliseDeDados Próximo</li>
            <li>Desafio 30DiasDeReactNative Próximo</li>
            <li>Desafio 30DiasDeMachineLearning Próximo</li>
        </ul>
    </div>
  </body>
</html>
```

![Projeto 1](../images/projects/dom_min_project_challenge_info_day_1.1.gif)

![Projeto 2](../images/projects/dom_min_project_challenge_info_day_1.1.png)

🎉 PARABÉNS ! 🎉

[<< Dia 20](../Dia_20_Escrevendo_Codigo_Limpo/Dia_20_Escrevendo_Codigo_Limpo.md) | [Dia 22 >>](../Dia_22_Manipulando_DOM/Dia_22_Manipulando_DOM.md)
