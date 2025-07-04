<div align="center">
  <h1> 30 Dias De JavaScript: Event Listeners</h1>
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

[<< Dia 22](../Dia_22_Manipulando_DOM/Dia_22_Manipulando_DOM.md) | [Dia 24 >>](../Dia_24_Mini_Projeto_Solar_System/Dia_24_Mini_Projeto_Solar_System.md)

![Trinta Dias De JavaScript](../images/banners/day_1_23.png)

- [Dia 23](#dia-23)
	- [DOM(Document Object Model)-Dia 3](#domdocument-object-model-dia-3)
		- [Event Listeners](#event-listeners)
			- [Click](#click)
			- [Double Click (Clique Duplo)](#double-click-clique-duplo)
			- [Mouse enter (Mouse Entra)](#mouse-enter-mouse-entra)
		- [Obtendo valor de um elemento de entrada](#obtendo-valor-de-um-elemento-de-entrada)
		- [Valor de entrada (input value)](#valor-de-entrada-input-value)
			- [Evento input e change](#evento-input-e-change)
			- [Evento blur](#evento-blur)
			- [keypress, keydown e keyup](#keypress-keydown-e-keyup)
	- [Exercícios](#exercícios)
		- [Exercício: Nível 1](#exercício-nível-1)

# Dia 23

## DOM(Document Object Model)-Dia 3

### Event Listeners

Eventos HTML comuns: onclick, onchange, onmouseover, onmouseout, onkeydown, onkeyup, onload.
Podemos adicionar o método event listener a qualquer objeto DOM. Usamos o método **_addEventListener()_** para ouvir diferentes tipos de eventos em elementos HTML. O método _addEventListener()_ recebe dois argumentos, um event listener e uma função de callback.

```js
selectedElement.addEventListener('eventlistner', function(e) {
  // a atividade que você deseja que ocorra após o evento estará aqui
})
// ou

selectedElement.addEventListener('eventlistner', e => {
  // a atividade que você deseja que ocorra após o evento estará aqui
})
```

#### Click

Para anexar um event listener a um elemento, primeiro selecionamos o elemento e depois anexamos o método addEventListener. O event listener recebe o tipo de evento e as funções de callback como argumento.

O seguinte é um exemplo de evento do tipo clique.

**Exemplo: click**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button>Clique em Mim</button>

    <script>
      const button = document.querySelector('button')
      button.addEventListener('click', e => {
        console.log('e fornece o objeto event listener:', e)
        console.log('e.target fornece o elemento selecionado: ', e.target)
        console.log(
          'e.target.textContent fornece o conteúdo do elemento selecionado: ',
          e.target.textContent
        )
      })
    </script>
  </body>
</html>
```

Um evento também pode ser anexado diretamente ao elemento HTML como script embutido.

**Exemplo: onclick**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button onclick="clickMe()">Clique em Mim</button>
    <script>
      const clickMe = () => {
        alert('Podemos anexar evento no elemento HTML')
      }
    </script>
  </body>
</html>
```

#### Double Click (Clique Duplo)

Para anexar um event listener a um elemento, primeiro selecionamos o elemento e depois anexamos o método addEventListener. O event listener recebe o tipo de evento e as funções de callback como argumento.

O seguinte é um exemplo de evento do tipo clique duplo.
**Exemplo: dblclick**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button>Clique em Mim</button>
    <script>
      const button = document.querySelector('button')
      button.addEventListener('dblclick', e => {
        console.log('e fornece o objeto event listener:', e)
        console.log('e.target fornece o elemento selecionado: ', e.target)
        console.log(
          'e.target.textContent fornece o conteúdo do elemento selecionado: ',
          e.target.textContent
        )
      })
    </script>
  </body>
</html>
```

#### Mouse enter (Mouse Entra)

Para anexar um event listener a um elemento, primeiro selecionamos o elemento e depois anexamos o método addEventListener. O event listener recebe o tipo de evento e as funções de callback como argumento.

O seguinte é um exemplo de evento do tipo mouse enter.

**Exemplo: mouseenter**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model</title>
  </head>

  <body>
    <button>Clique em Mim</button>
    <script>
      const button = document.querySelector('button')
      button.addEventListener('mouseenter', e => {
        console.log('e fornece o objeto event listener:', e)
        console.log('e.target fornece o elemento selecionado: ', e.target)
        console.log(
          'e.target.textContent fornece o conteúdo do elemento selecionado: ',
          e.target.textContent
        )
      })
    </script>
  </body>
</html>
```

Até agora você está familiarizado com o método addEventListener e como anexar event listeners. Existem muitos tipos de event listeners. Mas neste desafio, focaremos nos eventos mais comuns e importantes.
Lista de eventos:

- click - quando o elemento é clicado
- dblclick - quando o elemento é clicado duas vezes
- mouseenter - quando o ponteiro do mouse entra no elemento
- mouseleave - quando o ponteiro do mouse sai do elemento
- mousemove - quando o ponteiro do mouse se move sobre o elemento
- mouseover - quando o ponteiro do mouse se move sobre o elemento
- mouseout -quando o ponteiro do mouse sai do elemento
- input -quando um valor é inserido no campo de entrada
- change -quando o valor muda no campo de entrada
- blur -quando o elemento não está focado
- keydown - quando uma tecla é pressionada
- keyup - quando uma tecla é liberada
- keypress - quando pressionamos qualquer tecla
- onload - quando o navegador termina de carregar uma página

Teste os tipos de eventos acima substituindo o tipo de evento no trecho de código acima.

### Obtendo valor de um elemento de entrada

Geralmente preenchemos formulários e os formulários aceitam dados. Os campos de formulário são criados usando o elemento HTML input. Vamos construir uma pequena aplicação que nos permita calcular o índice de massa corporal de uma pessoa usando dois campos de entrada, um botão e uma tag p.

### Valor de entrada (input value)

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Dias De JavaScript</title>
  </head>

  <body>
    <h1>Calculadora de Índice de Massa Corporal</h1>

    <input type="text" id="mass" placeholder="Massa em Quilogramas" />
    <input type="text" id="height" placeholder="Altura em metros" />
    <button>Calcular IMC</button>

    <script>
      const mass = document.querySelector('#mass')
      const height = document.querySelector('#height')
      const button = document.querySelector('button')

      let bmi
      button.addEventListener('click', () => {
        bmi = mass.value / height.value ** 2
        alert(`Seu IMC é ${bmi.toFixed(2)}`)
        console.log(bmi)
      })
    </script>
  </body>
</html>
```

#### Evento input e change

No exemplo acima, conseguimos obter os valores de entrada de dois campos de entrada clicando no botão. E se quisermos obter o valor sem clicar no botão? Podemos usar o tipo de evento _change_ ou _input_ para obter dados imediatamente do campo de entrada quando o campo está em foco. Vejamos como lidaremos com isso.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Dias De JavaScript</title>
  </head>

  <body>
    <h1>Vinculação de Dados usando evento input ou change</h1>

    <input type="text" placeholder="diga algo" />
    <p></p>

    <script>
      const input = document.querySelector('input')
      const p = document.querySelector('p')

      input.addEventListener('input', e => {
        p.textContent = e.target.value
      })
    </script>
  </body>
</html>
```

#### Evento blur

Em contraste com _input_ ou _change_, o evento _blur_ ocorre quando o campo de entrada não está em foco.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Dias De JavaScript</title>
</head>

<body>
    <h1>Fornecendo feedback usando evento blur</h1>

    <input type="text" id="mass" placeholder="diga algo" />
    <p></p>

    <script>
        const input = document.querySelector('input')
        const p = document.querySelector('p')

        input.addEventListener('blur', (e) => {
            p.textContent = 'Campo obrigatório'
            p.style.color = 'red'

        })
    </script>
</body>

</html>
```

#### keypress, keydown e keyup

Podemos acessar todos os números de tecla do teclado usando diferentes tipos de event listeners. Vamos usar keypress e obter o keyCode de cada tecla do teclado.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Object Model:30 Dias De JavaScript</title>
  </head>

  <body>
    <h1>Eventos de tecla: Pressione qualquer tecla</h1>

    <script>
      document.body.addEventListener('keypress', e => {
        alert(e.keyCode)
      })
    </script>
  </body>
</html>
```

---

🌕 Você é tão especial, você está progredindo todos os dias. Agora, você sabe como lidar com qualquer tipo de evento DOM. Faltam apenas sete dias para o seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercício: Nível 1

1. Gerando números e marcando números pares, ímpares e primos com três cores diferentes. Veja a imagem abaixo.

![Gerador de Números](./../images/projects/dom_min_project_number_generator_day_3.1.gif)

2. Gerando o código da tecla do teclado usando event listener. A imagem abaixo.

![Tecla do Teclado](./../images/projects/dom_min_project_keycode_day_3.2.gif)

🎉 PARABÉNS ! 🎉

[<< Dia 22](../Dia_22_Manipulando_DOM/Dia_22_Manipulando_DOM.md) | [Dia 24 >>](../Dia_24_Mini_Projeto_Solar_System/Dia_24_Mini_Projeto_Solar_System.md)
