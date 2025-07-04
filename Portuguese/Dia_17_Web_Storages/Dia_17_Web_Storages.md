<div align="center">
  <h1> 30 Dias De JavaScript: Web Storages</h1>
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

[<< Dia 16](../Dia_16_JSON/Dia_16_JSON.md) | [Dia 18 >>](../Dia_18_Promises/Dia_18_Promises.md)

![Trinta Dias De JavaScript](../images/banners/day_1_17.png)

- [Dia 17](#dia-17)
	- [HTML5 Web Storage](#html5-web-storage)
		- [sessionStorage](#sessionstorage)
		- [localStorage](#localstorage)
		- [Caso de uso de Web Storages](#caso-de-uso-de-web-storages)
	- [Objetos HTML5 Web Storage](#objetos-html5-web-storage)
		- [Definindo item no localStorage](#definindo-item-no-localstorage)
		- [Obtendo item do localStorage](#obtendo-item-do-localstorage)
		- [Limpando o localStorage](#limpando-o-localstorage)
	- [Exercícios](#exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# Dia 17

## HTML5 Web Storage

Web Storage (sessionStorage e localStorage) é uma nova API HTML5 que oferece benefícios importantes sobre os cookies tradicionais. Antes do HTML5, os dados do aplicativo tinham que ser armazenados em cookies, incluídos em cada solicitação do servidor. O Web Storage é mais seguro e grandes quantidades de dados podem ser armazenadas localmente, sem afetar o desempenho do site. O limite de armazenamento de dados de cookies em muitos navegadores da web é de cerca de 4 KB por cookie. Os Web Storages podem armazenar dados muito maiores (pelo menos 5 MB) e nunca são transferidos para o servidor. Todos os sites da mesma origem podem armazenar e acessar os mesmos dados.

Os dados armazenados podem ser acessados usando JavaScript, o que lhe dá a capacidade de aproveitar o script do lado do cliente para fazer muitas coisas que tradicionalmente envolviam programação do lado do servidor e bancos de dados relacionais. Existem dois objetos Web Storage:

- sessionStorage
- localStorage

O localStorage é semelhante ao sessionStorage, exceto que, enquanto os dados armazenados no localStorage não têm tempo de expiração, os dados armazenados no sessionStorage são apagados quando a sessão da página termina - ou seja, quando a página é fechada.

Deve-se notar que os dados armazenados no localStorage ou sessionStorage são específicos do protocolo da página.

As chaves e os valores são sempre strings (observe que, como acontece com os objetos, as chaves inteiras serão convertidas automaticamente em strings).

![web_storage](../images/web_storage.png)

### sessionStorage

O sessionStorage está disponível apenas na guia do navegador ou na sessão da janela. Ele foi projetado para armazenar dados em uma única sessão de página da web. Isso significa que se a janela for fechada, os dados da sessão serão removidos. Como sessionStorage e localStorage têm métodos semelhantes, focaremos apenas no localStorage.

### localStorage

O localStorage do HTML5 é a parte da API de Web Storage usada para armazenar dados no navegador sem data de expiração. Os dados estarão disponíveis no navegador mesmo após o fechamento do navegador. O localStorage é mantido mesmo entre as sessões do navegador. Isso significa que os dados ainda estão disponíveis quando o navegador é fechado e reaberto, e também instantaneamente entre guias e janelas.

Os dados do Web Storage, em ambos os casos, não estão disponíveis entre navegadores diferentes. Por exemplo, objetos de armazenamento criados no Firefox não podem ser acessados no Internet Explorer, exatamente como os cookies. Existem cinco métodos para trabalhar no localStorage:
_setItem(), getItem(), removeItem(), clear(), key()_

### Caso de uso de Web Storages

Alguns casos de uso de Web Storages são

- armazenar dados temporariamente
- salvar produtos que o usuário coloca em seu carrinho de compras
- os dados podem ser disponibilizados entre solicitações de página, várias guias do navegador e também entre sessões do navegador usando localStorage
- pode ser usado offline completamente usando localStorage
- O Web Storage pode ser um grande ganho de desempenho quando alguns dados estáticos são armazenados no cliente para minimizar o número de solicitações subsequentes. Até mesmo imagens podem ser armazenadas em strings usando a codificação Base64.
- pode ser usado para o método de autenticação do usuário

Para os exemplos mencionados acima, faz sentido usar o localStorage. Você pode estar se perguntando, então, quando devemos usar o sessionStorage.

Nos casos em que queremos nos livrar dos dados assim que a janela for fechada. Ou, talvez, se não quisermos que o aplicativo interfira no mesmo aplicativo que está aberto em outra janela. Esses cenários são melhor atendidos com o sessionStorage.

Agora, vamos ver como usar essas APIs de Web Storage.

## Objetos HTML5 Web Storage

O Web Storage HTML fornece dois objetos para armazenar dados no cliente:

- window.localStorage - armazena dados sem data de expiração
- window.sessionStorage - armazena dados para uma sessão (os dados são perdidos quando a guia do navegador é fechada) A maioria dos navegadores modernos suporta Web Storage, no entanto, é bom verificar o suporte do navegador para localStorage e sessionStorage. Vejamos os métodos disponíveis para os objetos Web Storage.

Objetos Web Storage:

- _localStorage_ - para exibir o objeto localStorage
- _localStorage.clear()_ - para remover tudo no localStorage
- _localStorage.setItem()_ - para armazenar dados no localStorage. Ele recebe os parâmetros chave e valor.
- _localStorage.getItem()_ - para exibir dados armazenados no localStorage. Ele recebe uma chave como parâmetro.
- _localStorage.removeItem()_ - para remover o item armazenado de um localStorage. Ele recebe a chave como parâmetro.
- _localStorage.key()_ - para exibir dados armazenados em um localStorage. Ele recebe o índice como parâmetro.

![local_storage](../images/local_storage.png)

### Definindo item no localStorage

Quando definimos dados a serem armazenados em um localStorage, eles serão armazenados como uma string. Se estivermos armazenando um array ou um objeto, devemos primeiro convertê-lo em string para manter o formato, caso contrário, perderemos a estrutura do array ou a estrutura do objeto dos dados originais.

Armazenamos dados no localStorage usando o método _localStorage.setItem_.

```js
//sintaxe
localStorage.setItem('key', 'value')
```

- Armazenando string em um localStorage

```js
localStorage.setItem('firstName', 'Asabeneh') // como o valor é uma string, não o convertemos para string
console.log(localStorage)
```

```sh
Storage {firstName: 'Asabeneh', length: 1}
```

- Armazenando número em um localStorage

```js
localStorage.setItem('age', 200)
console.log(localStorage)
```

```sh
 Storage {age: '200', firstName: 'Asabeneh', length: 2}
```

- Armazenando um array em um localStorage. Se estivermos armazenando um array, um objeto ou um array de objetos, devemos primeiro converter o objeto em string. Veja o exemplo abaixo.

```js
const skills = ['HTML', 'CSS', 'JS', 'React']
//O array de skills precisa ser convertido em string primeiro para manter o formato.
const skillsJSON = JSON.stringify(skills, undefined, 4)
localStorage.setItem('skills', skillsJSON)
console.log(localStorage)
```

```sh
Storage {age: '200', firstName: 'Asabeneh', skills: 'HTML,CSS,JS,React', length: 3}
```

```js
let skills = [
  { tech: 'HTML', level: 10 },
  { tech: 'CSS', level: 9 },
  { tech: 'JS', level: 8 },
  { tech: 'React', level: 9 },
  { tech: 'Redux', level: 10 },
  { tech: 'Node', level: 8 },
  { tech: 'MongoDB', level: 8 }
]

let skillJSON = JSON.stringify(skills)
localStorage.setItem('skills', skillJSON)
```

- Armazenando um objeto em um localStorage. Antes de armazenarmos objetos em um localStorage, o objeto precisa ser convertido em string.

```js
const user = {
  firstName: 'Asabeneh',
  age: 250,
  skills: ['HTML', 'CSS', 'JS', 'React']
}

const userText = JSON.stringify(user, undefined, 4)
localStorage.setItem('user', userText)
```

### Obtendo item do localStorage

Obtemos dados do localStorage usando o método _localStorage.getItem()_.

```js
//sintaxe
localStorage.getItem('key')
```

```js
let firstName = localStorage.getItem('firstName')
let age = localStorage.getItem('age')
let skills = localStorage.getItem('skills')
console.log(firstName, age, skills)
```

```sh
 'Asabeneh', '200', '['HTML','CSS','JS','React']'
```

Como você pode ver, a skill está em formato de string. Vamos usar JSON.parse() para analisá-la para um array normal.

```js
let skills = localStorage.getItem('skills')
let skillsObj = JSON.parse(skills, undefined, 4)
console.log(skillsObj)
```

```sh
['HTML','CSS','JS','React']
```

### Limpando o localStorage

O método clear limpará tudo o que estiver armazenado no localStorage.

```js
localStorage.clear()
```

🌕 Você é determinado. Agora, você conhece Web Storages e sabe como armazenar pequenos dados nos navegadores dos clientes. Você está 17 passos à frente em seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercícios: Nível 1

1. Armazene seu nome, sobrenome, idade, país e cidade no localStorage do seu navegador.

### Exercícios: Nível 2

1. Crie um objeto student. O objeto student terá as chaves nome, sobrenome, idade, skills, país, matriculado e valores para as chaves. Armazene o objeto student no localStorage do seu navegador.

### Exercícios: Nível 3

1. Crie um objeto chamado personAccount. Ele tem as propriedades nome, sobrenome, rendas, despesas e os métodos rendaTotal, despesaTotal, infoConta, adicionarRenda, adicionarDespesa e saldoConta. Rendas é um conjunto de rendas e sua descrição e despesas é também um conjunto de despesas e sua descrição.

🎉 PARABÉNS ! 🎉

[<< Dia 16](../Dia_16_JSON/Dia_16_JSON.md) | [Dia 18 >>](../Dia_18_Promises/Dia_18_Promises.md)
