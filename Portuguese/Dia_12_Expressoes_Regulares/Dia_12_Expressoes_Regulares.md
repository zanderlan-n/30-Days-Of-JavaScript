<div align="center">
  <h1> 30 Dias De JavaScript: Expressões Regulares</h1>
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

[<< Dia 11](../Dia_11_Destructuring_e_Spreading/dia_11_destructuring_e_spreading.md) | [Dia 13 >>](../Dia_13_Console_Object_Methods/Dia_13_Console_Object_Methods.md)

![Trinta Dias De JavaScript](../images/banners/day_1_12.png)

- [📘 Dia 12](#-dia-12)
	- [Expressões Regulares](#expressões-regulares)
		- [Parâmetros RegExp](#parâmetros-regexp)
			- [Padrão](#padrão)
			- [Flags](#flags)
		- [Criando um padrão com o Construtor RegExp](#criando-um-padrão-com-o-construtor-regexp)
		- [Criando um padrão sem o Construtor RegExp](#criando-um-padrão-sem-o-construtor-regexp)
		- [Métodos do Objeto RegExpp](#métodos-do-objeto-regexpp)
			- [Testando por uma correspondência](#testando-por-uma-correspondência)
			- [Array contendo todas as correspondências](#array-contendo-todas-as-correspondências)
			- [Substituindo uma substring](#substituindo-uma-substring)
		- [Colchetes](#colchetes)
		- [Caractere de escape (\\) em RegExp](#caractere-de-escape--em-regexp)
		- [Uma ou mais vezes (+)](#uma-ou-mais-vezes-)
		- [Ponto (.)](#ponto-)
		- [Zero ou mais vezes (*)](#zero-ou-mais-vezes-)
		- [Zero ou uma vez (?)](#zero-ou-uma-vez-)
		- [Quantificador em RegExp](#quantificador-em-regexp)
		- [Acento circunflexo ^](#acento-circunflexo-)
		- [Correspondência exata](#correspondência-exata)
	- [💻 Exercícios](#-exercícios)
		- [Exercícios: Nível 1](#exercícios-nível-1)
		- [Exercícios: Nível 2](#exercícios-nível-2)
		- [Exercícios: Nível 3](#exercícios-nível-3)

# 📘 Dia 12

## Expressões Regulares

Uma expressão regular ou RegExp é uma pequena linguagem de programação que ajuda a encontrar padrões em dados. Uma RegExp pode ser usada para verificar se algum padrão existe em diferentes tipos de dados. Para usar RegExp em JavaScript, usamos o construtor RegExp ou podemos declarar um padrão RegExp usando duas barras normais seguidas por uma flag. Podemos criar um padrão de duas maneiras.

Para declarar uma string, usamos aspas simples, aspas duplas ou crase. Para declarar uma expressão regular, usamos duas barras normais e uma flag opcional. A flag pode ser g, i, m, s, u ou y.

### Parâmetros RegExp

Uma expressão regular recebe dois parâmetros. Um padrão de pesquisa obrigatório e uma flag opcional.

#### Padrão

Um padrão pode ser um texto ou qualquer forma de padrão que tenha algum tipo de similaridade. Por exemplo, a palavra spam em um e-mail pode ser um padrão que estamos interessados em procurar em um e-mail ou um formato de número de telefone pode ser nosso interesse em procurar.

#### Flags

Flags são parâmetros opcionais em uma expressão regular que determinam o tipo de pesquisa. Vejamos algumas das flags:

- g: uma flag global que significa procurar por um padrão em todo o texto
- i: flag insensível a maiúsculas e minúsculas (procura tanto em minúsculas quanto em maiúsculas)
- m: multilinhas

### Criando um padrão com o Construtor RegExp

Declarando expressão regular sem flag global e flag insensível a maiúsculas e minúsculas.

```js
// sem flag
let pattern = 'love'
let regEx = new RegExp(pattern)
```

Declarando expressão regular com flag global e flag insensível a maiúsculas e minúsculas.

```js
let pattern = 'love'
let flag = 'gi'
let regEx = new RegExp(pattern, flag)
```

Declarando um padrão regex usando o objeto RegExp. Escrevendo o padrão e a flag dentro do construtor RegExp

```js
let regEx = new RegExp('love','gi')
```

### Criando um padrão sem o Construtor RegExp

Declarando expressão regular com flag global e flag insensível a maiúsculas e minúsculas.

```js
let regEx= /love/gi
```

A expressão regular acima é a mesma que criamos com o construtor RegExp

```js
let regEx= new RegExp('love','gi')
```

### Métodos do Objeto RegExpp

Vejamos alguns métodos RegExp

#### Testando por uma correspondência

*test()*: Testa por uma correspondência em uma string. Retorna true ou false.

```js
const str = 'Eu amo JavaScript'
const pattern = /love/
const result = pattern.test(str)
console.log(result)
```

```sh
true
```

#### Array contendo todas as correspondências

*match()*: Retorna um array contendo todas as correspondências, incluindo grupos de captura, ou null se nenhuma correspondência for encontrada.
Se não usarmos uma flag global, match() retorna um array contendo o padrão, índice, entrada e grupo.

```js
const str = 'Eu amo JavaScript'
const pattern = /love/
const result = str.match(pattern)
console.log(result)
```

```sh
["love", index: 2, input: "Eu amo JavaScript", groups: undefined]
```

```js
const str = 'Eu amo JavaScript'
const pattern = /love/g
const result = str.match(pattern)
console.log(result)
```

```sh
["love"]
```

*search()*: Testa por uma correspondência em uma string. Retorna o índice da correspondência, ou -1 se a pesquisa falhar.

```js
const str = 'Eu amo JavaScript'
const pattern = /love/g
const result = str.search(pattern)
console.log(result)
```

```sh
2
```

#### Substituindo uma substring

*replace()*: Executa uma pesquisa por uma correspondência em uma string e substitui a substring correspondente por uma substring de substituição.

```js
const txt = 'Python é a linguagem mais bonita que um ser humano já criou.\
Eu recomendo python para uma primeira linguagem de programação'

matchReplaced = txt.replace(/Python|python/, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript é a linguagem mais bonita que um ser humano já criou.Eu recomendo python para uma primeira linguagem de programação
```

```js
const txt = 'Python é a linguagem mais bonita que um ser humano já criou.\
Eu recomendo python para uma primeira linguagem de programação'

matchReplaced = txt.replace(/Python|python/g, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript é a linguagem mais bonita que um ser humano já criou.Eu recomendo JavaScript para uma primeira linguagem de programação
```

```js
const txt = 'Python é a linguagem mais bonita que um ser humano já criou.\
Eu recomendo python para uma primeira linguagem de programação'

matchReplaced = txt.replace(/Python/gi, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript é a linguagem mais bonita que um ser humano já criou.Eu recomendo JavaScript para uma primeira linguagem de programação
```

```js

const txt = '%Eu s%ou profe%%ss%%or% e %% eu a%m%o ens%in%ar.\
N%ão% h%á na%da% t%ão gr%at%ifi%can%te qu%an%to ed%uc%ar e c%ap%ac%it%ar \
p%es%so%as.\
Ac%he%i o ens%in%o m%ais i%nt%er%%es%san%te d%o q%ue qu%alqu%er ou%tro tr%ab%alh%o.\
Is%so% m%ot%iv%a vo%c%ê a s%er um pr%of%es%s%or.'

matches = txt.replace(/%/g, '')
console.log(matches)
```

```sh
Eu sou professor e  eu amo ensinar.Não há nada tão gratificante quanto educar e capacitar pessoas.Achei o ensino mais interessante do que qualquer outro trabalho.Isso motiva você a ser um professor.
```

* []:  Um conjunto de caracteres
  * [a-c] significa, a ou b ou c
  * [a-z] significa, qualquer letra de a à z
  * [A-Z] significa, qualquer caractere de A à Z
  * [0-3] significa, 0 ou 1 ou 2 ou 3
  * [0-9] significa qualquer número de 0 à 9
  * [A-Za-z0-9] qualquer caractere que seja de a à z, A à Z, 0 à 9
* \\:  usado para escapar caracteres especiais
  * \d significa: corresponder onde a string contém dígitos (números de 0-9)
  * \D significa: corresponder onde a string não contém dígitos
* . : qualquer caractere exceto caractere de nova linha (\n)
* ^: começa com
  * r'^substring' ex: r'^love', uma frase que começa com a palavra love
  * r'[^abc] significa não a, não b, não c.
* $: termina com
  * r'substring$' ex: r'love$', frase termina com a palavra love
* *: zero ou mais vezes
  * r'[a]*' significa que 'a' é opcional ou pode ocorrer muitas vezes.
* +: uma ou mais vezes
  * r'[a]+' significa pelo menos uma ou mais vezes
* ?: zero ou uma vez
  *  r'[a]?' significa zero ou uma vez
* \b: delimitador de palavra, corresponde ao início ou fim de uma palavra
* {3}: Exatamente 3 caracteres
* {3,}: Pelo menos 3 caracteres
* {3,8}: De 3 a 8 caracteres
* |: Ou um ou outro
  * r'apple|banana' significa ou uma maçã ou uma banana
* (): Capturar e agrupar

![Folha de Dicas de Expressão Regular](../images/regex.png)

Vamos usar exemplos para esclarecer os metacaracteres acima

### Colchetes

Vamos usar colchetes para incluir letras minúsculas e maiúsculas

```js
const pattern = '[Aa]pple' // este colchete significa A ou a
const txt = 'Maçã e banana são frutas. Um velho clichê diz que uma maçã por dia mantém o médico longe, foi substituído por uma banana por dia mantém o médico muito muito longe. '
const matches = txt.match(pattern)

console.log(matches)
```

```sh
["Maçã", index: 0, input: "Maçã e banana são frutas. Um velho clichê diz que uma maçã por dia mantém o médico longe, foi substituído por uma banana por dia mantém o médico muito muito longe.", groups: undefined]

```

```js
const pattern = /[Aa]pple/g // este colchete significa A ou a
const txt = 'Maçã e banana são frutas. Um velho clichê diz que uma maçã por dia mantém o médico longe, foi substituído por uma banana por dia mantém o médico muito muito longe. '
const matches = txt.match(pattern)

console.log(matches)
```

```sh
["Maçã", "maçã"]
```

Se quisermos procurar por banana, escrevemos o padrão da seguinte forma:

```js
const pattern = /[Aa]pple|[Bb]anana/g // este colchete significa A ou a ou B ou b
const txt = 'Maçã e banana são frutas. Um velho clichê diz que uma maçã por dia mantém o médico longe, foi substituído por uma banana por dia mantém o médico muito muito longe. Banana é fácil de comer também.'
const matches = txt.match(pattern)

console.log(matches)
```

```sh
["Maçã", "banana", "maçã", "banana", "Banana"]
```

Usando colchetes e o operador `or` (|), conseguimos extrair Apple, apple, Banana e banana.

### Caractere de escape (\\) em RegExp

```js
const pattern = /\d/g  // d é um caractere especial que significa dígitos
const txt = 'Este exemplo de expressão regular foi feito em 12 de Janeiro de 2020.'
const matches = txt. match(pattern)

console.log(matches)  // ["1", "2", "2", "0", "2", "0"], não é o que queremos
```

```js
const pattern = /\d+/g  // d é um caractere especial que significa dígitos, + significa uma ou mais vezes
const txt = 'Este exemplo de expressão regular foi feito em 12 de Janeiro de 2020.'
const matches = txt. match(pattern)

console.log(matches)  // ["12", "2020"], é o que queremos
```

### Uma ou mais vezes (+)

```js
const pattern = /\d+/g  // d é um caractere especial que significa dígitos, + significa uma ou mais vezes
const txt = 'Este exemplo de expressão regular foi feito em 12 de Janeiro de 2020.'
const matches = txt. match(pattern)
console.log(matches)  // ["12", "2020"]
```

### Ponto (.)

```js
const pattern = /[a]./g  // este colchete significa 'a' e . significa qualquer caractere exceto nova linha
const txt = 'Maçã e banana são frutas'
const matches = txt.match(pattern)

console.log(matches)  // ["aç", "an", "an", "a ", "ão"]
```

```js
const pattern = /[a].+/g  // . qualquer caractere, + qualquer caractere uma ou mais vezes
const txt = 'Maçã e banana são frutas'
const matches = txt.match(pattern)

console.log(matches)  // ['açã e banana são frutas']
```

### Zero ou mais vezes (*)

Zero ou muitas vezes. O padrão pode não ocorrer ou pode ocorrer muitas vezes.

```js

const pattern = /[a].*/g  //. qualquer caractere, * zero ou mais vezes
const txt = 'Maçã e banana são frutas'
const matches = txt.match(pattern)

console.log(matches)  // ['açã e banana são frutas']

```

### Zero ou uma vez (?)

Zero ou uma vez. O padrão pode não ocorrer ou pode ocorrer uma vez.

```js
const txt = 'Não tenho certeza se existe uma convenção de como escrever a palavra e-mail.\
Algumas pessoas escrevem email, outras podem escrever Email ou E-mail.'
const pattern = /[Ee]-?mail/g  // ? significa opcional
matches = txt.match(pattern)

console.log(matches)  // ["e-mail", "email", "Email", "E-mail"]

```

### Quantificador em RegExp

Podemos especificar o comprimento da substring que procuramos em um texto, usando chaves. Vejamos como usar quantificadores RegExp. Imagine que estamos interessados em substrings com comprimento de 4 caracteres.

```js
const txt = 'Este exemplo de expressão regular foi feito em 6 de Dezembro de 2019.'
const pattern = /\b\w{4}\b/g  //  exatamente quatro caracteres de palavras
const matches = txt.match(pattern)
console.log(matches)  //['Este', 'feit', '2019']
```

```js
const txt = 'Este exemplo de expressão regular foi feito em 6 de Dezembro de 2019.'
const pattern = /\b[a-zA-Z]{4}\b/g  //  exatamente quatro caracteres de palavras sem números
const matches = txt.match(pattern)
console.log(matches)  //['Este', 'feit']
```

```js
const txt = 'Este exemplo de expressão regular foi feito em 6 de Dezembro de 2019.'
const pattern = /\d{4}/g  // um número e exatamente quatro dígitos
const matches = txt.match(pattern)
console.log(matches)  // ['2019']
```

```js
const txt = 'Este exemplo de expressão regular foi feito em 6 de Dezembro de 2019.'
const pattern = /\d{1,4}/g   // 1 a 4 dígitos
const matches = txt.match(pattern)
console.log(matches)  // ['6', '2019']
```

### Acento circunflexo ^

- Começa com

```js
const txt = 'Este exemplo de expressão regular foi feito em 6 de Dezembro de 2019.'
const pattern = /^Este/ // ^ significa começa com
const matches = txt.match(pattern)
console.log(matches)  // ['Este']
```

- Negação

```js
const txt = 'Este exemplo de expressão regular foi feito em 6 de Dezembro de 2019.'
const pattern = /[^A-Za-z,. ]+/g  // ^ em um conjunto de caracteres significa negação, não de A a Z, não de a a z, sem espaço, sem vírgula, sem ponto
const matches = txt.match(pattern)
console.log(matches)  // ["6", "2019"]
```

### Correspondência exata

Deve ter ^ no início e $ no final.

```js
let pattern = /^[A-Z][a-z]{3,12}$/;
let name = 'Asabeneh';
let result = pattern.test(name)

console.log(result) // true
```

🌕 Você está indo longe. Continue assim! Agora, você está super carregado com o poder da expressão regular. Você tem o poder de extrair e limpar qualquer tipo de texto e pode extrair significado de dados não estruturados. Você acabou de completar os desafios do dia 12 e está 12 passos à frente em seu caminho para a grandeza. Agora faça alguns exercícios para o seu cérebro e para os seus músculos.

## 💻 Exercícios

### Exercícios: Nível 1

1. Calcule a renda anual total da pessoa a partir do seguinte texto. ‘Ele ganha 4000 euros de salário por mês, 10000 euros de bônus anual, 5500 euros de cursos online por mês.’
2. A posição de algumas partículas no eixo x horizontal -12, -4, -3 e -1 na direção negativa, 0 na origem, 4 e 8 na direção positiva. Extraia esses números e encontre a distância entre as duas partículas mais distantes.

```js
points = ['-1', '2', '-4', '-3', '-1', '0', '4', '8']
sortedPoints =  [-4, -3, -1, -1, 0, 2, 4, 8]
distance = 12
```

3. Escreva um padrão que identifique se uma string é uma variável JavaScript válida.

    ```sh
    is_valid_variable('first_name') # True
    is_valid_variable('first-name') # False
    is_valid_variable('1first_name') # False
    is_valid_variable('firstname') # True
    ```

### Exercícios: Nível 2

1. Escreva uma função chamada *tenMostFrequentWords* que obtenha as dez palavras mais frequentes de uma string?

    ```js
        paragraph = `Eu amo ensinar. Se você não ama ensinar, o que mais você pode amar. Eu amo Python se você não ama algo que pode lhe dar todas as capacidades para desenvolver uma aplicação, o que mais você pode amar.`
        console.log(tenMostFrequentWords(paragraph))
    ```

    ```sh
        [
        {word:'amar', count:6},
        {word:'você', count:5},
        {word:'pode', count:3},
        {word:'que', count:2},
        {word:'ensinar', count:2},
        {word:'não', count:2},
        {word:'mais', count:2},
        {word:'Eu', count:2},
        {word:'algo', count:1},
        {word:'todas', count:1},
        {word:'para', count:1},
        {word:'Python', count:1},
        {word:'lhe', count:1},
        {word:'Se', count:1},
        {word:'se', count:1},
        {word:'o', count:1},
        {word:'uma', count:1},
        {word:'aplicação', count:1},
        {word:'desenvolver',count:1},
        {word:'dar',count:1},
        {word:'capacidades',count:1},
        {word:'Se',count:1}]
    ```

    ```js
    console.log(tenMostFrequentWords(paragraph, 10))
    ```

    ```sh
   [{word:'amar', count:6},
    {word:'você', count:5},
    {word:'pode', count:3},
    {word:'que', count:2},
    {word:'ensinar', count:2},
    {word:'não', count:2},
    {word:'mais', count:2},
    {word:'Eu', count:2},
    {word:'algo', count:1},
    {word:'todas', count:1}
    ]
    ```

### Exercícios: Nível 3

1. Escreva uma função que limpe o texto. Limpe o seguinte texto. Após a limpeza, conte as três palavras mais frequentes na string.

  ```js
    sentence = `%Eu $sou@% um %prof@essor%, &e& eu ad%#oro %ens@inar%;. Não $há nada; &tão& gr@atificante quanto educ@ar &e& @emp%o@derar pes@soas. ;Eu achei o ens@ino m%ais interessante que@ qualquer outro %tr@abalho. %Is@so mot%iva vo@cê a ser um prof@essor!?`
    console.log(cleanText(sentence))
   ```

   ```sh
    Eu sou um professor e eu adoro ensinar Não há nada tão gratificante quanto educar e empoderar pessoas Eu achei o ensino mais interessante que qualquer outro trabalho Isso motiva você a ser um professor
    ```
2. Escreva uma função que encontre as palavras mais frequentes. Após a limpeza, conte as três palavras mais frequentes na string.

  ```js
    console.log(mostFrequentWords(cleanedText))
    [{word:'Eu', count:3}, {word:'ensinar', count:2}, {word:'professor', count:2}]
  ```

🎉 PARABÉNS ! 🎉

[<< Dia 11](../Dia_11_Destructuring_e_Spreading/dia_11_destructuring_e_spreading.md) | [Dia 13 >>](../Dia_13_Console_Object_Methods/Dia_13_Console_Object_Methods.md)
