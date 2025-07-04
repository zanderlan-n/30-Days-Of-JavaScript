<div align="center">
  <h1> 30 Dias De JavaScript: Classes</h1>
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

[<< Dia 14](../Dia_14_Tratamento_de_Erros/Dia_14_Tratamento_de_Erros.md) | [Dia 16 >>](../Dia_16_JSON/Dia_16_JSON.md)

![Trinta Dias De JavaScript](../images/banners/day_1_15.png)

- [Dia 15](#dia-15)
	- [Classes](#classes)
		- [Definindo classes](#definindo-classes)
		- [Instanciação de Classe](#instanciação-de-classe)
		- [Construtor de Classe](#construtor-de-classe)
		- [Valores padrão com construtor](#valores-padrão-com-construtor)
		- [Métodos de classe](#métodos-de-classe)
		- [Propriedades com valor inicial](#propriedades-com-valor-inicial)
		- [getter](#getter)
		- [setter](#setter)
		- [Método estático](#método-estático)
	- [Herança](#herança)
		- [Sobrescrevendo métodos](#sobrescrevendo-métodos)
	- [Exercícios](#exercícios)
		- [Exercícios Nível 1](#exercícios-nível-1)
		- [Exercícios Nível 2](#exercícios-nível-2)
		- [Exercícios Nível 3](#exercícios-nível-3)

# Dia 15

## Classes

JavaScript é uma linguagem de programação orientada a objetos. Tudo em JavaScript é um objeto, com suas propriedades e métodos. Criamos classes para criar um objeto. Uma Classe é como um construtor de objetos, ou um "modelo" para criar objetos. Instanciamos uma classe para criar um objeto. A classe define atributos e o comportamento do objeto, enquanto o objeto, por outro lado, representa a classe.

Depois de criarmos uma classe, podemos criar objetos a partir dela sempre que quisermos. Criar um objeto a partir de uma classe é chamado de instanciação de classe.

Na seção de objetos, vimos como criar um objeto literal. O objeto literal é um singleton. Se quisermos obter um objeto semelhante, temos que escrevê-lo. No entanto, a classe permite criar muitos objetos. Isso ajuda a reduzir a quantidade de código e a repetição de código.

### Definindo classes

Para definir uma classe em JavaScript, precisamos da palavra-chave _class_, o nome de uma classe em **CamelCase** e um bloco de código (duas chaves). Vamos criar uma classe chamada Pessoa.

```sh
// sintaxe
class NomeDaClasse {
    //  código vai aqui
}

```

**Exemplo:**

```js
class Pessoa {
  // código vai aqui
}
```

Criamos uma classe Pessoa, mas ela não tem nada dentro.

### Instanciação de Classe

Instanciar uma classe significa criar um objeto a partir de uma classe. Precisamos da palavra-chave _new_ e chamamos o nome da classe após a palavra new.

Vamos criar um objeto pessoa a partir da nossa classe Pessoa.

```js
class Pessoa {
  // código vai aqui
}
const pessoa = new Pessoa()
console.log(pessoa)
```

```sh
Pessoa {}
```

Como você pode ver, criamos um objeto pessoa. Como a classe ainda não tinha nenhuma propriedade, o objeto também está vazio.

Vamos usar o construtor da classe para passar diferentes propriedades para a classe.

### Construtor de Classe

O construtor é uma função embutida que nos permite criar um modelo para nosso objeto. A função construtora começa com a palavra-chave constructor seguida por parênteses. Dentro dos parênteses, passamos as propriedades do objeto como parâmetro. Usamos a palavra-chave _this_ para anexar os parâmetros do construtor à classe.

O construtor da classe Pessoa a seguir tem as propriedades firstName e lastName. Essas propriedades são anexadas à classe Pessoa usando a palavra-chave _this_. _This_ se refere à própria classe.

```js
class Pessoa {
  constructor(firstName, lastName) {
    console.log(this) // Verifique a saída daqui
    this.firstName = firstName
    this.lastName = lastName
  }
}

const pessoa = new Pessoa()

console.log(pessoa)
```

```sh
Pessoa {firstName: undefined, lastName:undefined}
```

Todas as chaves do objeto são indefinidas. Sempre que instanciamos, devemos passar o valor das propriedades. Vamos passar o valor desta vez quando instanciarmos a classe.

```js
class Pessoa {
  constructor(firstName, lastName) {
    this.firstName = firstName
    this.lastName = lastName
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh')

console.log(pessoa1)
```

```sh
Pessoa {firstName: "Asabeneh", lastName: "Yetayeh"}
```

Como afirmamos no início, uma vez que criamos uma classe, podemos criar muitos objetos usando a classe. Agora, vamos criar muitos objetos pessoa usando a classe Pessoa.

```js
class Pessoa {
  constructor(firstName, lastName) {
    console.log(this) // Verifique a saída daqui
    this.firstName = firstName
    this.lastName = lastName
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh')
const pessoa2 = new Pessoa('Lidiya', 'Tekle')
const pessoa3 = new Pessoa('Abraham', 'Yetayeh')

console.log(pessoa1)
console.log(pessoa2)
console.log(pessoa3)
```

```sh
Pessoa {firstName: "Asabeneh", lastName: "Yetayeh"}
Pessoa {firstName: "Lidiya", lastName: "Tekle"}
Pessoa {firstName: "Abraham", lastName: "Yetayeh"}
```

Usando a classe Pessoa, criamos três objetos pessoa. Como você pode ver, nossa classe não tinha muitas propriedades, vamos adicionar mais propriedades à classe.

```js
class Pessoa {
  constructor(firstName, lastName, age, country, city) {
    console.log(this) // Verifique a saída daqui
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh', 250, 'Finlândia', 'Helsinki')

console.log(pessoa1)
```

```sh
Pessoa {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finlândia", city: "Helsinki"}
```

### Valores padrão com construtor

As propriedades da função construtora podem ter um valor padrão como outras funções regulares.

```js
class Pessoa {
  constructor(
    firstName = 'Asabeneh',
    lastName = 'Yetayeh',
    age = 250,
    country = 'Finlândia',
    city = 'Helsinki'
  ) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
  }
}

const pessoa1 = new Pessoa() // pegará os valores padrão
const pessoa2 = new Pessoa('Lidiya', 'Tekle', 28, 'Finlândia', 'Espoo')

console.log(pessoa1)
console.log(pessoa2)
```

```sh
Pessoa {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finlândia", city: "Helsinki"}
Pessoa {firstName: "Lidiya", lastName: "Tekle", age: 28, country: "Finlândia", city: "Espoo"}
```

### Métodos de classe

O construtor dentro de uma classe é uma função embutida que nos permite criar um modelo para o objeto. Em uma classe, podemos criar métodos de classe. Métodos são funções JavaScript dentro da classe. Vamos criar alguns métodos de classe.

```js
class Pessoa {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh', 250, 'Finlândia', 'Helsinki')
const pessoa2 = new Pessoa('Lidiya', 'Tekle', 28, 'Finlândia', 'Espoo')

console.log(pessoa1.getFullName())
console.log(pessoa2.getFullName())
```

```sh
Asabeneh Yetayeh
Lidiya Tekle
```

### Propriedades com valor inicial

Quando criamos uma classe, para algumas propriedades podemos ter um valor inicial. Por exemplo, se você está jogando um jogo, sua pontuação inicial será zero. Então, podemos ter uma pontuação inicial ou pontuação que é zero. De outra forma, podemos ter uma habilidade inicial e adquiriremos alguma habilidade depois de algum tempo.

```js
class Pessoa {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh', 250, 'Finlândia', 'Helsinki')
const pessoa2 = new Pessoa('Lidiya', 'Tekle', 28, 'Finlândia', 'Espoo')

console.log(pessoa1.score)
console.log(pessoa2.score)

console.log(pessoa1.skills)
console.log(pessoa2.skills)
```

```sh
0
0
[]
[]
```

Um método pode ser um método regular ou um getter ou um setter. Vejamos getter e setter.

### getter

O método get nos permite acessar o valor do objeto. Escrevemos um método get usando a palavra-chave _get_ seguida por uma função. Em vez de acessar propriedades diretamente do objeto, usamos getter para obter o valor. Veja o exemplo abaixo.

```js
class Pessoa {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh', 250, 'Finlândia', 'Helsinki')
const pessoa2 = new Pessoa('Lidiya', 'Tekle', 28, 'Finlândia', 'Espoo')

console.log(pessoa1.getScore) // Não precisamos de parênteses para chamar um método getter
console.log(pessoa2.getScore)

console.log(pessoa1.getSkills)
console.log(pessoa2.getSkills)
```

```sh
0
0
[]
[]
```

### setter

O método setter nos permite modificar o valor de certas propriedades. Escrevemos um método setter usando a palavra-chave _set_ seguida por uma função. Veja o exemplo abaixo.

```js
class Pessoa {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
  set setScore(score) {
    this.score += score
  }
  set setSkill(skill) {
    this.skills.push(skill)
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh', 250, 'Finlândia', 'Helsinki')
const pessoa2 = new Pessoa('Lidiya', 'Tekle', 28, 'Finlândia', 'Espoo')

pessoa1.setScore = 1
pessoa1.setSkill = 'HTML'
pessoa1.setSkill = 'CSS'
pessoa1.setSkill = 'JavaScript'

pessoa2.setScore = 1
pessoa2.setSkill = 'Planejamento'
pessoa2.setSkill = 'Gerenciamento'
pessoa2.setSkill = 'Organização'

console.log(pessoa1.score)
console.log(pessoa2.score)

console.log(pessoa1.skills)
console.log(pessoa2.skills)
```

```sh
1
1
["HTML", "CSS", "JavaScript"]
["Planejamento", "Gerenciamento", "Organização"]
```

Não se confunda com a diferença entre método regular e getter. Se você sabe como fazer um método regular, está tudo bem. Vamos adicionar um método regular chamado getPersonInfo na classe Pessoa.

```js
class Pessoa {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
  set setScore(score) {
    this.score += score
  }
  set setSkill(skill) {
    this.skills.push(skill)
  }
  getPersonInfo() {
    let fullName = this.getFullName()
    let skills =
      this.skills.length > 0 &&
      this.skills.slice(0, this.skills.length - 1).join(', ') +
        ` e ${this.skills[this.skills.length - 1]}`
    let formattedSkills = skills ? `Ele conhece ${skills}` : ''

    let info = `${fullName} tem ${this.age} anos. Ele mora em ${this.city}, ${this.country}. ${formattedSkills}`
    return info
  }
}

const pessoa1 = new Pessoa('Asabeneh', 'Yetayeh', 250, 'Finlândia', 'Helsinki')
const pessoa2 = new Pessoa('Lidiya', 'Tekle', 28, 'Finlândia', 'Espoo')
const pessoa3 = new Pessoa('John', 'Doe', 50, 'Marte', 'Cidade de Marte')

pessoa1.setScore = 1
pessoa1.setSkill = 'HTML'
pessoa1.setSkill = 'CSS'
pessoa1.setSkill = 'JavaScript'

pessoa2.setScore = 1
pessoa2.setSkill = 'Planejamento'
pessoa2.setSkill = 'Gerenciamento'
pessoa2.setSkill = 'Organização'

console.log(pessoa1.getScore)
console.log(pessoa2.getScore)

console.log(pessoa1.getSkills)
console.log(pessoa2.getSkills)
console.log(pessoa3.getSkills)

console.log(pessoa1.getPersonInfo())
console.log(pessoa2.getPersonInfo())
console.log(pessoa3.getPersonInfo())
```

```sh
1
1
["HTML", "CSS", "JavaScript"]
["Planejamento", "Gerenciamento", "Organização"]
[]
Asabeneh Yetayeh tem 250 anos. Ele mora em Helsinki, Finlândia. Ele conhece HTML, CSS e JavaScript
Lidiya Tekle tem 28 anos. Ele mora em Espoo, Finlândia. Ele conhece Planejamento, Gerenciamento e Organização
John Doe tem 50 anos. Ele mora em Cidade de Marte, Marte.
```

### Método estático

A palavra-chave static define um método estático para uma classe. Métodos estáticos não são chamados em instâncias da classe. Em vez disso, eles são chamados na própria classe. Frequentemente, são funções utilitárias, como funções para criar ou clonar objetos. Um exemplo de método estático é _Date.now()_. O método _now_ é chamado diretamente da classe.

```js
class Pessoa {
  constructor(firstName, lastName, age, country, city) {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
    this.country = country
    this.city = city
    this.score = 0
    this.skills = []
  }
  getFullName() {
    const fullName = this.firstName + ' ' + this.lastName
    return fullName
  }
  get getScore() {
    return this.score
  }
  get getSkills() {
    return this.skills
  }
  set setScore(score) {
    this.score += score
  }
  set setSkill(skill) {
    this.skills.push(skill)
  }
  getPersonInfo() {
    let fullName = this.getFullName()
    let skills =
      this.skills.length > 0 &&
      this.skills.slice(0, this.skills.length - 1).join(', ') +
        ` e ${this.skills[this.skills.length - 1]}`

    let formattedSkills = skills ? `Ele conhece ${skills}` : ''

    let info = `${fullName} tem ${this.age} anos. Ele mora em ${this.city}, ${this.country}. ${formattedSkills}`
    return info
  }
  static favoriteSkill() {
    const skills = ['HTML', 'CSS', 'JS', 'React', 'Python', 'Node']
    const index = Math.floor(Math.random() * skills.length)
    return skills[index]
  }
  static showDateTime() {
    let now = new Date()
    let year = now.getFullYear()
    let month = now.getMonth() + 1
    let date = now.getDate()
    let hours = now.getHours()
    let minutes = now.getMinutes()
    if (hours < 10) {
      hours = '0' + hours
    }
    if (minutes < 10) {
      minutes = '0' + minutes
    }

    let dateMonthYear = date + '.' + month + '.' + year
    let time = hours + ':' + minutes
    let fullTime = dateMonthYear + ' ' + time
    return fullTime
  }
}

console.log(Pessoa.favoriteSkill())
console.log(Pessoa.showDateTime())
```

```sh
Node
15.1.2020 23:56
```

Os métodos estáticos são métodos que podem ser usados como funções utilitárias.

## Herança

Usando herança, podemos acessar todas as propriedades e métodos da classe pai. Isso reduz a repetição de código. Se você se lembra, temos uma classe pai Pessoa e criaremos filhos a partir dela. Nossas classes filhas podem ser estudante, professor etc.

```js
// sintaxe
class NomeClasseFilha extends NomeClassePai {
 // código vai aqui
}
```

Vamos criar uma classe filha Estudante a partir da classe pai Pessoa.

```js
class Estudante extends Pessoa {
  saySomething() {
    console.log('Eu sou um filho da classe pessoa')
  }
}

const s1 = new Estudante('Asabeneh', 'Yetayeh', 250, 'Finlândia', 'Helsinki')
console.log(s1)
console.log(s1.saySomething())
console.log(s1.getFullName())
console.log(s1.getPersonInfo())
```

```sh
Estudante {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finlândia", city: "Helsinki", …}
Eu sou um filho da classe pessoa
Asabeneh Yetayeh
Estudante {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finlândia", city: "Helsinki", …}
Asabeneh Yetayeh tem 250 anos. Ele mora em Helsinki, Finlândia.
```

### Sobrescrevendo métodos

Como você pode ver, conseguimos acessar todos os métodos da Classe Pessoa e os usamos na classe filha Estudante. Podemos personalizar os métodos pais, podemos adicionar propriedades adicionais a uma classe filha. Se quisermos personalizar os métodos e se quisermos adicionar propriedades extras, precisamos usar a função construtora da classe filha também. Dentro da função construtora, chamamos a função super() para acessar todas as propriedades da classe pai. A classe Pessoa não tinha gênero, mas agora vamos dar a propriedade gênero para a classe filha, Estudante. Se o mesmo nome de método for usado na classe filha, o método pai será sobrescrito.

```js
class Estudante extends Pessoa {
  constructor(firstName, lastName, age, country, city, gender) {
    super(firstName, lastName, age, country, city)
    this.gender = gender
  }

  saySomething() {
    console.log('Eu sou um filho da classe pessoa')
  }
  getPersonInfo() {
    let fullName = this.getFullName()
    let skills =
      this.skills.length > 0 &&
      this.skills.slice(0, this.skills.length - 1).join(', ') +
        ` e ${this.skills[this.skills.length - 1]}`

    let formattedSkills = skills ? `Ele conhece ${skills}` : ''
    let pronoun = this.gender == 'Masculino' ? 'Ele' : 'Ela'

    let info = `${fullName} tem ${this.age} anos. ${pronoun} mora em ${this.city}, ${this.country}. ${formattedSkills}`
    return info
  }
}

const s1 = new Estudante(
  'Asabeneh',
  'Yetayeh',
  250,
  'Finlândia',
  'Helsinki',
  'Masculino'
)
const s2 = new Estudante('Lidiya', 'Tekle', 28, 'Finlândia', 'Helsinki', 'Feminino')
s1.setScore = 1
s1.setSkill = 'HTML'
s1.setSkill = 'CSS'
s1.setSkill = 'JavaScript'

s2.setScore = 1
s2.setSkill = 'Planejamento'
s2.setSkill = 'Gerenciamento'
s2.setSkill = 'Organização'

console.log(s1)

console.log(s1.saySomething())
console.log(s1.getFullName())
console.log(s1.getPersonInfo())

console.log(s2.saySomething())
console.log(s2.getFullName())
console.log(s2.getPersonInfo())
```

```sh
Estudante {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finlândia", city: "Helsinki", …}
Estudante {firstName: "Lidiya", lastName: "Tekle", age: 28, country: "Finlândia", city: "Helsinki", …}
Eu sou um filho da classe pessoa
Asabeneh Yetayeh
Estudante {firstName: "Asabeneh", lastName: "Yetayeh", age: 250, country: "Finlândia", city: "Helsinki", …}
Asabeneh Yetayeh tem 250 anos. Ele mora em Helsinki, Finlândia. Ele conhece HTML, CSS e JavaScript
Eu sou um filho da classe pessoa
Lidiya Tekle
Estudante {firstName: "Lidiya", lastName: "Tekle", age: 28, country: "Finlândia", city: "Helsinki", …}
Lidiya Tekle tem 28 anos. Ela mora em Helsinki, Finlândia. Ela conhece Planejamento, Gerenciamento e Organização
```

Agora, o método getPersonInfo foi sobrescrito e identifica se a pessoa é do sexo masculino ou feminino.

🌕 Você está se destacando. Agora, você conhece classes e tem o poder de transformar tudo em um objeto. Você chegou na metade do caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## Exercícios

### Exercícios Nível 1

1. Crie uma classe Animal. A classe terá propriedades nome, idade, cor, pernas e crie diferentes métodos.
2. Crie classes filhas Cachorro e Gato a partir da Classe Animal.

### Exercícios Nível 2

1. Sobrescreva o método que você criou na classe Animal.

### Exercícios Nível 3

1. Vamos tentar desenvolver um programa que calcule a medida de tendência central de uma amostra (média, mediana, moda) e medida de variabilidade (amplitude, variância, desvio padrão). Além dessas medidas, encontre o mínimo, máximo, contagem, percentil e distribuição de frequência da amostra. Você pode criar uma classe chamada Estatisticas e criar todas as funções que fazem cálculos estatísticos como métodos para a classe Estatisticas. Verifique a saída abaixo.

```JS
idades = [31, 26, 34, 37, 27, 26, 32, 32, 26, 27, 27, 24, 32, 33, 27, 25, 26, 38, 37, 31, 34, 24, 33, 29, 26]

console.log('Contagem:', estatisticas.count()) // 25
console.log('Soma: ', estatisticas.sum()) // 744
console.log('Mínimo: ', estatisticas.min()) // 24
console.log('Máximo: ', estatisticas.max()) // 38
console.log('Amplitude: ', estatisticas.range()) // 14
console.log('Média: ', estatisticas.mean()) // 30
console.log('Mediana: ',estatisticas.median()) // 29
console.log('Moda: ', estatisticas.mode()) // {'moda': 26, 'contagem': 5}
console.log('Variância: ',estatisticas.var()) // 17.5
console.log('Desvio Padrão: ', estatisticas.std()) // 4.2
console.log('Variância: ',estatisticas.var()) // 17.5
console.log('Distribuição de Frequência: ',estatisticas.freqDist()) // [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

```sh
// sua saída deve se parecer com isto
console.log(estatisticas.describe())
Contagem: 25
Soma:  744
Mínimo:  24
Máximo:  38
Amplitude:  14
Média:  30
Mediana:  29
Moda:  (26, 5)
Variância:  17.5
Desvio Padrão:  4.2
Distribuição de Frequência: [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

2. Crie uma classe chamada PessoaConta. Ela tem as propriedades nome, sobrenome, rendas, despesas e os métodos rendaTotal, despesaTotal, infoConta, adicionarRenda, adicionarDespesa e saldoConta. Rendas é um conjunto de rendas e sua descrição e despesas é também um conjunto de despesas e sua descrição.

🎉 PARABÉNS ! 🎉

[<< Dia 14](../Dia_14_Tratamento_de_Erros/Dia_14_Tratamento_de_Erros.md) | [Dia 16 >>](../Dia_16_JSON/Dia_16_JSON.md)
