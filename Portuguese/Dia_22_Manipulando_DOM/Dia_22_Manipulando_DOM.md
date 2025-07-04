<div align="center">
  <h1> 30 Dias De JavaScript: Manipulando Objeto DOM</h1>
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

[<< Dia 21](../Dia_21_Document_Object_Model/Dia_21_Document_Object_Model.md) | [Dia 23 >>](../Dia_23_Eventos/Dia_23_Eventos.md)

![Trinta Dias De JavaScript](../images/banners/day_1_22.png)
- [Dia 22](#dia-22)
  - [DOM(Document Object Model)-Dia 2](#domdocument-object-model-dia-2)
    - [Criando um Elemento](#criando-um-elemento)
    - [Criando elementos](#criando-elementos)
    - [Anexando filho a um elemento pai](#anexando-filho-a-um-elemento-pai)
    - [Removendo um elemento filho de um nó pai](#removendo-um-elemento-filho-de-um-nó-pai)
  - [Exercícios](#exercícios)
    - [Exercícios: Nível 1](#exercícios-nível-1)
    - [Exercícios: Nível 2](#exercícios-nível-2)
    - [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 22

## DOM(Document Object Model)-Dia 2

### Criando um Elemento

Para criar um elemento HTML usamos o nome da tag. Criar um elemento HTML usando JavaScript é muito simples e direto. Usamos o método _document.createElement()_. O método recebe o nome da tag de um elemento HTML como parâmetro de string.

```js
// sintaxe
document.createElement('nomedatag')
```

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Dias De JavaScript</title>
</head>

<body>

    <script>
        let title = document.createElement('h1')
        title.className = 'title'
        title.style.fontSize = '24px'
        title.textContent = 'Criando elemento HTML DOM Dia 2'

        console.log(title)
    </script>
</body>

</html>
```

### Criando elementos

Para criar múltiplos elementos devemos usar um loop. Usando um loop podemos criar quantos elementos HTML quisermos.
Depois de criarmos o elemento, podemos atribuir valor às diferentes propriedades do objeto HTML.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Dias De JavaScript</title>
</head>

<body>

    <script>
        let title
        for (let i = 0; i < 3; i++) {
            title = document.createElement('h1')
            title.className = 'title'
            title.style.fontSize = '24px'
            title.textContent = i
            console.log(title)
        }
    </script>
</body>

</html>
```

### Anexando filho a um elemento pai

Para ver um elemento criado no documento HTML, devemos anexá-lo ao pai como um elemento filho. Podemos acessar o corpo do documento HTML usando *document.body*. O *document.body* suporta o método *appendChild()*. Veja o exemplo abaixo.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Dias De JavaScript</title>
</head>

<body>

    <script>
        // criando múltiplos elementos e anexando ao elemento pai
        let title
        for (let i = 0; i < 3; i++) {
            title = document.createElement('h1')
            title.className = 'title'
            title.style.fontSize = '24px'
            title.textContent = i
            document.body.appendChild(title)
        }
    </script>
</body>
</html>
```

### Removendo um elemento filho de um nó pai

Após criar um HTML, podemos querer remover um ou mais elementos e podemos usar o método *removeChild()*.

**Exemplo:**

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Dias De JavaScript</title>
</head>

<body>
    <h1>Removendo nó filho</h1>
    <h2>Desafios de Asabeneh Yetayeh em 2020</h1>
    <ul>
        <li>Desafio 30DiasDePython Concluído</li>
        <li>Desafio 30DiasDeJavaScript Concluído</li>
        <li>Desafio 30DiasOfReact Próximo</li>
        <li>Desafio 30DiasDeFullStack Próximo</li>
        <li>Desafio 30DiasDeAnaliseDeDados Próximo</li>
        <li>Desafio 30DiasDeReactNative Próximo</li>
        <li>Desafio 30DiasDeMachineLearning Próximo</li>
    </ul>

    <script>
        const ul = document.querySelector('ul')
        const lists = document.querySelectorAll('li')
        for (const list of lists) {
            ul.removeChild(list)

        }
    </script>
</body>

</html>
```

Como vimos na seção anterior, existe uma maneira melhor de eliminar todos os elementos HTML internos ou os filhos de um elemento pai usando as propriedades do método *innerHTML*.

```html
<!DOCTYPE html>
<html>

<head>
    <title>Document Object Model:30 Dias De JavaScript</title>
</head>

<body>
    <h1>Removendo nó filho</h1>
    <h2>Desafios de Asabeneh Yetayeh em 2020</h1>
    <ul>
        <li>Desafio 30DiasDePython Concluído</li>
        <li>Desafio 30DiasDeJavaScript Concluído</li>
        <li>Desafio 30DiasOfReact Próximo</li>
        <li>Desafio 30DiasDeFullStack Próximo</li>
        <li>Desafio 30DiasDeAnaliseDeDados Próximo</li>
        <li>Desafio 30DiasDeReactNative Próximo</li>
        <li>Desafio 30DiasDeMachineLearning Próximo</li>
    </ul>

    <script>
        const ul = document.querySelector('ul')
        ul.innerHTML = ''
    </script>
</body>

</html>
```

O trecho de código acima limpou todos os elementos filhos.

---

🌕 Você é tão especial, você está progredindo todos os dias. Agora, você sabe como destruir um elemento DOM criado quando necessário. Você aprendeu DOM e agora tem a capacidade de construir e desenvolver aplicativos. Faltam apenas oito dias para o seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercícios: Nível 1

1. Crie um container div no documento HTML e crie de 100 a 100 números dinamicamente e anexe ao container div.
   - Números pares com fundo verde
   - Números ímpares com fundo amarelo
   - Números primos com fundo vermelho

![Gerador de Números](./../images/projects/dom_min_project_day_number_generators_2.1.png)

### Exercícios: Nível 2

1. Use o array de países para exibir todos os países. Veja o design.

![Lista de Países do Mundo](./../images/projects/dom_min_project_countries_aray_day_2.2.png)

### Exercícios: Nível 3

Verifique os requisitos deste projeto em ambas as imagens (jpg e gif). Todos os dados e CSS foram implementados usando apenas JavaScript. Os dados são encontrados no projeto_3 da pasta inicial. O botão suspenso foi criado usando o elemento HTML [*details*](https://www.w3schools.com/tags/tag_details.asp).

![Informações do Desafio](./../images/projects/dom_mini_project_challenge_info_day_2.3.gif)

![Informações do Desafio](./../images/projects/dom_mini_project_challenge_info_day_2.3.png)

🎉 PARABÉNS ! 🎉

[<< Dia 21](../Dia_21_Document_Object_Model/Dia_21_Document_Object_Model.md) | [Dia 23 >>](../Dia_23_Eventos/Dia_23_Eventos.md)
