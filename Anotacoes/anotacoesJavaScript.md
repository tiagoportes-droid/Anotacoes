## 📦 Variáveis e Tipos

- `let` → Cria uma variável que pode ter seu valor alterado.
- `const` → Cria uma variável que não pode ser reatribuída.
- `var` → Forma antiga de criar variáveis. Evite usar em código novo.
- `typeof` → Mostra o tipo de um valor.
- `Number()` → Converte para número.
- `String()` → Converte para texto.
- `parseInt()` → Converte para número inteiro.
- `parseFloat()` → Converte para número decimal.

### Exemplo

~~~javascript
let nome = "Tiago";
const idade = 16;

console.log(typeof nome);
console.log(typeof idade);
~~~

---

## 🔀 Condições

- `if` → Executa algo se uma condição for verdadeira.
- `else` → Executa algo caso a condição seja falsa.
- `else if` → Permite testar outra condição.
- `===` → Compara valor e tipo.
- `!==` → Verifica se valor ou tipo são diferentes.
- `>` → Maior que.
- `<` → Menor que.
- `>=` → Maior ou igual.
- `<=` → Menor ou igual.
- `&&` → **E**.
- `||` → **OU**.
- `!` → Inverte uma condição.

### Exemplo

~~~javascript
let idade = 16;

if (idade >= 18) {
    console.log("Maior de idade");
} else {
    console.log("Menor de idade");
}
~~~

---

## 📋 Arrays

Arrays são usados para guardar vários valores dentro de uma única variável.

~~~javascript
let frutas = ["Maçã", "Banana", "Uva"];
~~~

- `.push()` → Adiciona um item no final.
- `.pop()` → Remove o último item.
- `.shift()` → Remove o primeiro item.
- `.unshift()` → Adiciona um item no início.
- `.length` → Mostra a quantidade de itens.
- `.includes()` → Verifica se um item existe.

### Exemplo

~~~javascript
let frutas = ["Maçã", "Banana", "Uva"];

frutas.push("Laranja");

console.log(frutas);
console.log(frutas.length);
console.log(frutas.includes("Banana"));
~~~

---

## 🔁 Formas de Percorrer Arrays

### `for`

Forma tradicional de fazer repetições.

~~~javascript
for (let i = 0; i < frutas.length; i++) {
    console.log(frutas[i]);
}
~~~

### `for...of`

Percorre diretamente os valores do array.

~~~javascript
for (let fruta of frutas) {
    console.log(fruta);
}
~~~

### `forEach()`

Executa uma função para cada item do array.

~~~javascript
frutas.forEach((fruta) => {
    console.log(fruta);
});
~~~

> `forEach()` é útil quando queremos executar uma ação para cada elemento.

---

## 🛠️ Métodos de Array

### `map()`

Cria um **novo array**, modificando cada elemento.

~~~javascript
let numeros = [1, 2, 3, 4];

let dobro = numeros.map((numero) => {
    return numero * 2;
});

console.log(dobro);
~~~

Resultado:

~~~text
[2, 4, 6, 8]
~~~

### `filter()`

Cria um novo array somente com os elementos que atendem a uma condição.

~~~javascript
let numeros = [1, 2, 3, 4, 5, 6];

let pares = numeros.filter((numero) => {
    return numero % 2 === 0;
});

console.log(pares);
~~~

Resultado:

~~~text
[2, 4, 6]
~~~

### `find()`

Procura o **primeiro elemento** que atende a uma condição.

~~~javascript
let numeros = [10, 20, 30, 40];

let resultado = numeros.find((numero) => {
    return numero > 25;
});

console.log(resultado);
~~~

Resultado:

~~~text
30
~~~

### `findIndex()`

Parecido com `find()`, mas retorna a **posição** do elemento.

~~~javascript
let numeros = [10, 20, 30, 40];

let posicao = numeros.findIndex((numero) => {
    return numero > 25;
});

console.log(posicao);
~~~

Resultado:

~~~text
2
~~~

### `some()`

Verifica se **pelo menos um** elemento atende à condição.

~~~javascript
let numeros = [1, 3, 5, 8];

let temPar = numeros.some((numero) => {
    return numero % 2 === 0;
});

console.log(temPar);
~~~

Resultado:

~~~text
true
~~~

### `every()`

Verifica se **todos** os elementos atendem à condição.

~~~javascript
let numeros = [2, 4, 6, 8];

let todosPares = numeros.every((numero) => {
    return numero % 2 === 0;
});

console.log(todosPares);
~~~

Resultado:

~~~text
true
~~~

---

## 🧩 Funções

- `function` → Cria uma função.
- `return` → Retorna um valor.
- Parâmetros → Valores que a função recebe.

~~~javascript
function somar(a, b) {
    return a + b;
}

let resultado = somar(10, 5);

console.log(resultado);
~~~

---

## ➡️ Arrow Functions

Uma forma mais curta de escrever funções.

~~~javascript
const somar = (a, b) => {
    return a + b;
};
~~~

Se tiver apenas uma expressão, pode ser ainda menor:

~~~javascript
const somar = (a, b) => a + b;
~~~

São muito usadas com `map()`, `filter()` e `forEach()`.

~~~javascript
let numeros = [1, 2, 3];

let dobro = numeros.map(numero => numero * 2);
~~~

---

## 🧱 Objetos

Objetos armazenam informações através de **propriedades e valores**.

~~~javascript
const pessoa = {
    nome: "Tiago",
    idade: 16,
    cidade: "São Paulo"
};

console.log(pessoa.nome);
console.log(pessoa.idade);
~~~

### Acessando propriedades

~~~javascript
pessoa.nome
~~~

Ou:

~~~javascript
pessoa["nome"]
~~~

---

## 📤 Destructuring

Permite pegar valores de objetos ou arrays de uma forma mais rápida.

### Objeto

~~~javascript
const pessoa = {
    nome: "Tiago",
    idade: 16
};

const { nome, idade } = pessoa;

console.log(nome);
console.log(idade);
~~~

### Array

~~~javascript
const numeros = [10, 20];

const [primeiro, segundo] = numeros;

console.log(primeiro);
console.log(segundo);
~~~

---

## 📎 Spread Operator `...`

Usado principalmente para copiar ou juntar arrays e objetos.

~~~javascript
const numeros = [1, 2, 3];

const novosNumeros = [...numeros, 4, 5];

console.log(novosNumeros);
~~~

Resultado:

~~~text
[1, 2, 3, 4, 5]
~~~

Também pode juntar arrays:

~~~javascript
const a = [1, 2];
const b = [3, 4];

const resultado = [...a, ...b];

console.log(resultado);
~~~

---

## 🔤 Strings

Métodos úteis para trabalhar com textos:

- `.toUpperCase()` → Deixa tudo maiúsculo.
- `.toLowerCase()` → Deixa tudo minúsculo.
- `.includes()` → Verifica se contém determinado texto.
- `.trim()` → Remove espaços do começo e do final.
- `.replace()` → Substitui um trecho.
- `.split()` → Divide uma string e transforma em array.

### Exemplo

~~~javascript
let nome = "  Tiago  ";

console.log(nome.trim());
console.log(nome.toUpperCase());
~~~

---

## 🔄 Loops

### `while`

Repete enquanto uma condição for verdadeira.

~~~javascript
let numero = 0;

while (numero < 5) {
    console.log(numero);
    numero++;
}
~~~

### `do...while`

Executa pelo menos uma vez antes de verificar a condição.

~~~javascript
let numero = 0;

do {
    console.log(numero);
    numero++;
} while (numero < 5);
~~~

---

## 📝 Template Strings

Permitem colocar variáveis dentro de uma string usando `${}`.

~~~javascript
const nome = "Tiago";
const idade = 16;

console.log(`Meu nome é ${nome} e tenho ${idade} anos.`);
~~~

> Para usar Template Strings, utilize **crases**: `` ` ``.


#JavaScript #bancoDeDados #lógicaDeProgramacao #estudos  #backEnd 