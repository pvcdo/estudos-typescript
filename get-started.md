# TypeScript

## Tipos

Primitivos

- string
- number
- boolean
- Array
  - Possíveis representações
    - [1,2,3]
    - number[]
    - string[]
    - Array&lt;&gt;
  - any - desabilita checagens de erro do typescript. Cria como se fosse uma variável normal do javascript, onde você pode colocar qual quiser e também trocar seu tipo durante o código.
  - noImplicitAny - algumas vezes o desenvolvedor não especifica o tipo e o typescript não consegue inferir qual o tipo em função do contexto, quando isso acontece a variável é definida como any por padrão pelo compilador (há inferência de any). Usando noImplicitAny haverá um erro toda vez que for gerado um any por inferência.

## Anotação de tipo nas variáveis

A anotação do tipo da variável é colocado sempre depois do nome da variável, separada desse nome por um sinal ":". Na maioria dos casos não é necessário explicitar qual o tipo da variável, e para iniciantes é recomendável usar a tipagem o menos possível.

## Funções

### Parâmetros

O tipo do parâmetro vai também depois do nome do parâmetro, separado desse nome por ":", sendo que violações do tipo do parâmetro na chamada da função geram erro nessa chamada.

### Retorno da função

Aparece separado por ":" entre os parênteses que contêm os parâmetros da função e a chave de abertura dela. Também não é necessária essa anotação

## Objetos

Os tipos dos atributos são inferidos, mas em uma utilização, como por exemplo em uma função, podemos informar qual é o tipo esperado para cada um dos atributos.

Podemos também na função esperarmos trabalhar com um atributo opcional. Para marcar que um atributo de um objeto é opcional, devemos colocar no fim do nome o caracter "?", como se fosse parte do nome.

## União

União é uma técnica onde podemos atribuir a uma variável mais de um possível tipo membro da união. Em uma união só são válidos métodos que sejam válidos para TODOS os membros. É possível, porém, usar um método específico se trabalharmos com if.

## Apelido "type"

Podemos definir um apelido, ou nome comum para fazermos referência durante o código. Ex.:

```ts twoslash
type Point = {
  x: number;
  y: number;
};
 
// Exactly the same as the earlier example
function printCoord(pt: Point) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}
 
printCoord({ x: 100, y: 100 });
```

## Interface

É um outro jeito de declarar um objeto.

```ts twoslash
interface Point {
  x: number;
  y: number;
}
 
function printCoord(pt: Point) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}
 
printCoord({ x: 100, y: 100 });
```

## Diferença entre type e interface

A única diferença é que o type não permite inserções de atributos. Recomendado usar interface.

## Tipos de asserções

São utilizadas para especificar mais ou especificar menos o que é retornado.

```ts twolash
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
```

## Tipos literais

Podemos usar um valor para definirmos qual o tipo de uma variável terá, assim definido uma constante.

```ts twolash
let x: "hello" = "hello";
// OK
x = "hello";
// ...
x = "howdy";

// 

const constantString = "Hello World";
// Because `constantString` can only represent 1 possible string, it
// has a literal type representation
constantString;

// Esse tipo de anotação pode ser muito útil para valores definidos em funções

function printText(s: string, alignment: "left" | "right" | "center") {
  // ...
}
printText("Hello, world", "left");
printText("G'day, mate", "centre");

// Combinação

interface Options {
  width: number;
}
function configure(x: Options | "auto") {
  // ...
}
configure({ width: 100 });
configure("auto");
configure("automatic");
```
