# Funcións

Ata o de agora estabamos acostumados a facer duas cousas coas funcións:

1. Definir unha función.
2. Usar (chamar, executar ou invocar, todas son sinónimos) unha función.

## Índice

- [Funcións](#funcións)
  - [Índice](#Índice)
  - [1.1 Definición dunha función](#11-definición-dunha-función)
  - [1.2 Invocación dunha función](#12-invocación-dunha-función)
  - [1.3 Anatomía dunha función (definición e invocación)](#13-anatomía-dunha-función-definición-e-invocación)
  - [1.4 Clasificación das funcións](#14-clasificación-das-funcións)
  - [1.5 `undefined` e `return`](#15-undefined-e-return)
  - [1.6 Efectos secundarios nas funcións](#16-efectos-secundarios-nas-funcións)
  - [1.7 Exemplo](#17-exemplo)
  - [1.8 `map`, `filter` e `reduce`](#18-map-filter-e-reduce)
    - [1.8.1 `<array>.map(function)`](#181-arraymapfunction)
    - [1.8.2 `<array>.filter(function)`](#182-arrayfilterfunction)
    - [1.8.3 `<array>.reduce(function)`](#183-arrayreducefunction)
  - [1.9 Funcións anónimas, Arrow Functions e Lambda Functions](#19-funcións-anónimas-arrow-functions-e-lambda-functions)
    - [1.9.1 Inconsistencias](#191-inconsistencias)
    - [1.9.2 `return` implícito](#192-return-implícito)
  - [INTERLUDIO: Interpolación de Strings](#interludio-interpolación-de-strings)
  - [INTERLUDIO: Emojis e Strings](#interludio-emojis-e-strings)
  - [1.10 ¿Por qué existen os parámetros?](#110-por-qué-existen-os-parámetros)
    - [1.10.1 O problema](#1101-o-problema)
    - [1.10.2 A solución](#1102-a-solución)
    - [1.10.3 Conclusión](#1103-conclusión)
  - [1.11 O caso de `"hello".toUpperCase()`](#111-o-caso-de-hellotouppercase)
    - [1.11.1 O primeiro problema](#1111-o-primeiro-problema)
    - [1.11.2 O segundo problema](#1112-o-segundo-problema)
    - [1.11.3 A solución](#1113-a-solución)
    - [1.11.4 Conclusion](#1114-conclusion)
    - [1.11.5 Exercicio](#1115-exercicio)
  - [1.12 `myMap`, `myFilter`, `myReduce`](#112-mymap-myfilter-myreduce)
    - [1.12.1 `<array>.map(function)`](#1121-arraymapfunction)
    - [1.12.2 `myMap(coleccion, funcion)`](#1122-mymapcoleccion-funcion)
    - [1.12.3 `<array>.filter(function)`](#1123-arrayfilterfunction)
    - [1.12.4 `myFilter(coleccion, predicado)`](#1124-myfiltercoleccion-predicado)
    - [1.12.5 `<array>.reduce(function)`](#1125-arrayreducefunction)
    - [1.12.6 `myReduce(coleccion, funcion)`](#1126-myreducecoleccion-funcion)
  - [1.13 Notación xeral sobre tipos e funcións](#113-notación-xeral-sobre-tipos-e-funcións)
    - [1.13.1 `add1`](#1131-add1)
    - [1.13.2 `add`](#1132-add)
    - [1.13.3 `<string>.toUpperCase` e `yell`](#1133-stringtouppercase-e-yell)
    - [1.13.4 `<string>.toLowerCase` e `chillTheFunkOut`](#1134-stringtolowercase-e-chillthefunkout)
    - [1.13.5 `<array>.map(function)` e `myMap`](#1135-arraymapfunction-e-mymap)
    - [1.13.6 `<array>.filter(predicate)` e `myFilter`](#1136-arrayfilterpredicate-e-myfilter)
    - [1.13.7 `<array>.reduce(function)` e `myReduce`](#1137-arrayreducefunction-e-myreduce)
    - [1.13.8 Consideracións extra](#1138-consideracións-extra)
    - [1.13.9 Derivando unha fórmula xenérica para `myMap`](#1139-derivando-unha-fórmula-xenérica-para-mymap)
    - [1.13.10 Cal é o tipo da función `Fn` que aparece en `myMap`?](#11310-cal-é-o-tipo-da-función-fn-que-aparece-en-mymap)
  - [1.14 Exemplo de clase `myMap` e `String`s](#114-exemplo-de-clase-mymap-e-strings)

## 1.1 Definición dunha función

```js
function add1(x) {
  return x + 1;
}
```

## 1.2 Invocación dunha función

```js
add1(9); // Devolve un 10
add1(4); // Devolve un 5
```

## 1.3 Anatomía dunha función (definición e invocación)

Imos poñerlle nome a cada unha das partes dunha función

```js
function magic(x, y, z) {
  return x + y - z;
}

magic(20, 12, 2); // Devolve 30
```

- `function` indica que estamos a definir unha función.
- `magic` é o nome que escollemos para a función.
- `x` é o primerio parámetro da función.
- `20` é o primeiro argumento da invocación da función (vai acabar substituindo a `x`).
- `y` é o segundo parámetro da función.
- `12` é o segundo argumento da invocación da función (vai acabar substituindo a `y`).
- `z` é o terceiro parámetro da función.
- `2` é o terceiro argumento da invocación da función (vai acabar substituindo a `z`).
- `(x, y, z)` é a lista de parámetros da función. A **orde** dos parámetros **importa**.
- `(20, 12, 2)`é a lista de argumentos da invocación da función.
- `{ return x + y - z; }` é o corpo (_body_) da función.
- `x + y - z` é o valor de retorno (está despois de `return`) da función.

## 1.4 Clasificación das funcións

Dende o punto de vista que estamos a defender na clase, podemos ver as funcións (unha vez definidas) coma caixas negras tal que

```
      -----------
      |         |
 IN → | FUNCIÓN | → OUT
      |         |
      -----------
```

É dicir, só nos interesan as entradas (**IN**) e saidas (**OUT**). Por exemplo, `magic` ten

- 3 entradas `(x, y, z)`
- 1 saida, o resultado de `x + y - z` que é un número e podemos chamarlle `q`

```
      -----------
  x → |         |
  y → | FUNCIÓN | → q (= x + y - z)
  z → |         |
      -----------
```

## 1.5 `undefined` e `return`

> ¿Que acontece cando facemos un `console.log('Ola')`?

![](./img/console-log-example.png)

> ¿Qué é iso de `undefined`?

Vexamos outro exemplo

![](./img/add1-example.png)

Cando tras a flecha cara a esquerda aparece `undefined`, significa que a función invocada non devolve nada...

![](./img/undefined-example.png)

É dicir:

- `console.log` non ten `return`.
- A definición dunha función con `function` non ten `return`.
- `add1` sí ten `return` (e devolve un `8`)

Podemos definir funcións que non devolven nada. Por exemplo (fixádevos como **non usamos `return`**)

```js
function noReturn(x) {
  x + 100;
}

noReturn(4);
```

Esto é o que acontece

![](./img/no-return-example.png)

> Pero entón, ¿cómo pode ser que `console.log` non devolva nada pero ainda así vexamos o resultado?

A resposta... os efectos secundarios

## 1.6 Efectos secundarios nas funcións

Consideremos a seguinte función con moitos efectos secundarios (3, en concreto)

```js
function efectosSecundarios(x) {
  console.log(x + 100);
  console.log('Ola!!!');
  console.log('Aquí');
  return x + 50;
}

efectosSecundarios(20);
```

Fixádevos qué acontece

![](./img/efectos-secundarios-example-1.png)

Debemos actualizar o concepto das caixas negras

```
      -----------
      |         |
 IN → | FUNCIÓN | → OUT
      |         |
      -----------
           ↓
        Efectos
      Secundarios

```

## 1.7 Exemplo

Podemos levar esta idea ainda máis alá. Considerade a seguinte función

```js
function efectosSecundariosAndNoReturn(x) {
  console.log(x + 100);
  console.log('Ola!!!');
  console.log('Aquí');
  x + 20;    // OLLO. NON HAI return
}

efectosSecundarios(50);
```

Fixémonos en qué acontece

![](./img/efectos-secundarios-example-2.png)

Efectivamente non hai return (mirade o `undefined` por riba do `150`) e temos 3 efectos secundarios.

Poderiamos dicir que `efectosSecundariosAndNoReturn` ten

- 1 entrada `x`
- 0 saidas (no `return`, daí o `undefined`)
- 3 efectos secundarios:
	- `150`
	- `Ola!!!`
	- `Aquí`

## 1.8 `map`, `filter` e `reduce`

Xa sabemos usar `map`, `filter` e máis `reduce`. Recordemos

```js
function add1(x) {
  return x + 1;
}

[10, 20, 30].map(add1);

function greaterThan15(x) {
  return x > 15;
}

[10, 20, 30].filter(greaterThan15);

function minus(acc, x) {
  return acc - x;
}

[10, 20, 30].reduce(minus);
```

### 1.8.1 `<array>.map(function)`

![](./img/map-example-1.png)

> ¿Qué tipo de función agarda `map` como argumento?

Unha como `add1`. É dicir:

- 1 entrada (`x`)
- 1 saida (o resultado de facer `x + 1`)

Se `map` recibe como argumento unha función con características diferentes non vai funcionar. Por exemplo se recibe unha función con 3 entradas, falla.

### 1.8.2 `<array>.filter(function)`

![](./img/filter-example-1.png)

> ¿Qué tipo de función agarda `filter` como argumento?

Unha como `greaterThan15`. É dicir:

- 1 entrada (`x`)
- 1 saida (o resultado de facer `x > 15`).

Pero neste caso ademais a saida debe ser ou `true` ou `false`. A este tipo de funcións chamámolas **predicados**.

Se `filter` recibe como argumento unha función con características diferentes non vai funcionar. Por exemplo se recibe unha función con 3 entradas falla ou se recibe unha función que non devolve `true` ou `false`.

### 1.8.3 `<array>.reduce(function)`

![](./img/reduce-example-1.png)

> ¿Qué tipo de función agarda `reduce` como argumento?

Unha como `minus`. É dicir:

- 2 entradas (`acc`, `x`)
- 1 saida (o resultado de facer `acc - x`).

Neste caso preferimos poñer un nome máis descritivo aos parámetros da función `minus`. En lugar de `x`e `y` poñemos `acc` (diminutivo de `accumulator`) e `x` porque cando lla pasamos a `reduce` fai o seguinte:

1. `acc` toma o valor do primeiro número do array (`acc = 10`) e `x` o do segundo (`x = 20`).
2. executamos o `return` (`acc - x`) obtendo o valor `-10` (`10 - 20 = -10`). Este `-10` vai ser o valor do próximo `acc`.
3. `acc` toma o valor do último `return` (`acc = -10`) e `x` o do seguinte valor do array (`x = 30`).
4. executamos o `return` (`acc - x`) obtendo o valor `-40` (`-10 - 30 = -40`). Este `-40` sería o valor do próximo `acc` pero como xa baleiramos o array pasa a ser o valor resultado final de `reduce`.

As funcións como `minus`, **as veces**, reciben o nome de **reducers** ou **reductores**.

Se `reduce` recibe como argumento unha función con características diferentes non vai funcionar. Por exemplo se recibe unha función con 3 entradas ou con 1 entrada falla en ámbolos casos.

## 1.9 Funcións anónimas, Arrow Functions e Lambda Functions

Podemos definir **funcións anónimas** usando outra notación. Consideremos os exemplos de `map`, `filter` e `reduce` anteriores como punto de partida. O que aparece a continuación sería equivalente

```js
[10, 20, 30].map(num => num + 1);
[10, 20, 30].filter(num => num > 15);
[10, 20, 30].reduce((acc, num) => acc - num);
```

A proba

![](./img/lambda-example-1.png)

Agora resulta moito menos tedioso encadear operacións

```js
[10, 20, 30, 40, 50, 60, 70, 80]
  .map(num => num + 1)
  .filter(num => num > 15)
  .reduce((acc, num) => acc - num);
```

O resultado

![](./img/lambda-example-2.png)

### 1.9.1 Inconsistencias

As Arrow Functions teñen algunha inconsistencia ao respecto da notación

```js
// 0 parámetro
() => 27;  // ✅
   => 27;  // ❌

// 1 parámetro
(x) => x + 10; // ✅
x   => x + 10; // ✅

// 2 ou máis parámetros
(x, y, z) => x + y - z;  // ✅
x, y, z   => x + y - z;  // ❌
```

### 1.9.2 `return` implícito

As Arrow Functions levan un `return` implícito, é dicir as duas funcións que veñen a continuación son equivalentes

```js
(x, y, z) => x + y - z;
(x, y, z) => return x + y - z;
```

## INTERLUDIO: Interpolación de Strings

> Cómo podemos facer para intercalar partes variables nun texto ou String?

Moi sinxelo.

1. Usamos `` para facer o String.
2. Usamos `${}` para encapsular o que queremos intercalar

```js
function useMe(text) {
  return `insert 👉 ${text} 👈`
}

useMe("one two three");
useMe("four five six");
```

A proba

![](./img/use-me.png)

## INTERLUDIO: Emojis e Strings

Os emojis son Strings (texto). A proba... Mirade 👆.

## 1.10 ¿Por qué existen os parámetros?

### 1.10.1 O problema

Supoñamos que queremos facer unha función que me diga ola. Poderiamos pensar en facer algo coma

```js
function sayHiToDavid() {
  return "Hello David 👽👾🤖";
}
```

de xeito que poidamos invocala tal que así

```js
sayHiToDavid();
```

Imos ver que acontece

![](./img/sayHiToDavid.png)

Funciona!!! 👽

O problema é que se queremos saudar a alguén que non sexa David temos que definir outra función diferente. Por exemplo

```js
function sayHiToYou() {
  return "Hello You 👽👾🤖";
}

sayHiToYou();
```

E poderiamos seguir así ata o infinito definindo e usando unha chea de funcións moi semellantes.

```js
function sayHiToInsertNameHere() {
  return "Hello insertNameHere 👽👾🤖";
}
```

A estas alturas xa vemos o problema. Somos moi concretos. Precisamos ser mais abstractos, que o nome da persoa que queremos saudar poida cambiar.... **ENTER PARAMETERS!** 🐉🐉🐉

### 1.10.2 A solución

En vez de facer unha chea de función chamadas `sayHiToDavid`, `sayHiToYou`, `sayHiToKim`, `sayHiToSetsuko` imos definir unha soa función xenérica que nos permita especificar o nome a través dun parámetro

```js
function sayHiTo(name) {
  return `Hello ${name} 👽👾🤖`;
}
```

e agora podemos invocala con moitos nomes diferentes sen facer funcións novas

```js
sayHiTo("David");
sayHiTo("You");
sayHiTo("Kim");
sayHiTo("Setsuko");
```

Comprobamos

![](./img/sayHiTo.png)

### 1.10.3 Conclusión

Os **parámetros** (`name`) / **argumentos** (`David`, `You`, `Kim`, `Setsuko`) permítennos _encapsular_ as cousas que mudan. Dalgún xeito poderiamos dicir que unha función só debe usar os datos que se lle pasan a través dos parámetros...

Pero entón... qué acontece con `"hello".toUpperCase()`?

## 1.11 O caso de `"hello".toUpperCase()`

### 1.11.1 O primeiro problema

A función `toUpperCase()` permite poñer en maiúsculas un texto (String)... pero funciona dun xeito raro, xa que o texto non vai como parámetro. Vexamos

![](./img/hello-toUpperCase.png)

Porén, `toUpperCase("hello")` non funciona...

![](./img/toUpperCase-hello.png)

Non imos explicar neste momento que está a acontecer... xa que obligaríanos a falar dos **obxectos** e xa o faremos máis adiante... Pero ten que ver con onde se almacenan as funcións que nos da JavaScript xa feitas.

### 1.11.2 O segundo problema

Imos tentar usar `toUpperCase()` cun `<array de textos>.map` a ver que acontece

```js
["hello", "hallo", "hola", "ola"].map(yell);
```

![](./img/map-toUpperCase.png)

🤔🤔🤔

Analicemos a forma de `<texto>.toUpperCase()`:

- 0 entradas... `()`
- 1 saida, o texto en maiúsculas

Recordemos que `map` quere funcións como `add1(x)`

- 1 entrada
- 1 saida

### 1.11.3 A solución

> Poderiamos crear unha función que grite (`yell`) que sexa compatible con `map` e use dentro `toUpperCase()`?

Claro que podemos

```js
function yell(text) {
  return text.toUpperCase()
}

yell("me");
```

Aquí temos a proba

![](./img/yell.png)

> Pero, funciona con `map`?

```js
["hello", "hallo", "hola", "ola"].map(yell);
```

Comprobemos

![](./img/map-yell.png)

🥳🎉🎊

### 1.11.4 Conclusion

Se queremos usar unha función con `map` do estilo a `<text>.doSomething()` xa sabemos como convertila a `doSomething(text)`  para que funcione.

### 1.11.5 Exercicio

Probade con `"HELLO".toLowerCase()`. Convertídea para que funcione con `map`.

`.toLowerCase` funciona así

```js
"I'M ANGRY!".toLowerCase();
```

Tal e como podemos comprobar 👇

![](./img/toLowerCase.png)

Entón podemos facer `chillTheFunkOut`

```js
function chillTheFunkOut(text) {
  return text.toLowerCase();
}

chillTheFunkOut("I'M ANGRY!");
```

Asegurámonos de que funcione 👇

![](./img/chillTheFunkOut.png)

Que efectivamente funciona con `map`

```js
["hello", "hallo", "hola", "ola"].map(chillTheFunkOut);
```

![](./img/map-chillTheFunkOut.png)

## 1.12 `myMap`, `myFilter`, `myReduce`

### 1.12.1 `<array>.map(function)`

Recordemos como funcionaba `map`

```js
[10, 20, 30, 40].map(x => x + 1);
```

É dicir

```
      -------
      |     |
 fn → | map | → colección
      |     |
      -------
```

Pero `map` fai trampas porque usa unha colección extra. No exemplo de arriba `[10, 20, 30, 40]`.

### 1.12.2 `myMap(coleccion, funcion)`

Queremos facer unha función `myMap` que siga a seguinte descripción

```
               ---------
  coleccion1 → |       |
               | myMap | → coleccion2
          fn → |       |
               ---------
```

e que internamente use `<array>.map(function)`.

```js
function myMap(coleccion, funcion) {
  return coleccion.map(funcion);
}

myMap(
  [10, 20, 30, 40],
  x => x + 1
);
```

Comprobamos

![](./img/myMap.png)

### 1.12.3 `<array>.filter(function)`

Recordemos como funcionaba `filter`

```js
[10, 20, 30, 40].filter(x => x > 15);
```

É dicir

```
      ----------
      |        |
 fn → | filter | → colección
      |        |
      ----------
```

Pero `filter` fai trampas (as mesmas trampas que `map`) porque usa unha colección extra. No exemplo de arriba `[10, 20, 30, 40]`.

### 1.12.4 `myFilter(coleccion, predicado)`

Queremos facer unha función `myFilter` que siga a seguinte descripción

```
               ------------
  coleccion1 → |          |
               | myFilter | → coleccion2
   predicado → |          |
               ------------
```

e que internamente use `<array>.filter(function)`.

```js
function myFilter(coleccion, predicado) {
  return coleccion.filter(predicado);
}

myFilter(
  [10, 20, 30, 40],
  x => x > 15
);
```

Comprobamos

![](./img/myFilter.png)

### 1.12.5 `<array>.reduce(function)`

Recordemos como funcionaba `reduce`

```js
[10, 20, 30, 40].reduce((x,y) => x + y);
```

É dicir

```
      ----------
      |        |
 fn → | reduce | → valor
      |        |
      ----------
```

Pero `reduce` fai trampas porque usa unha colección extra. No exemplo de arriba `[10, 20, 30, 40]`.

### 1.12.6 `myReduce(coleccion, funcion)`

Queremos facer unha función `myReduce` que siga a seguinte descripción

```
               ------------
  coleccion1 → |          |
               | myReduce | → valor
          fn → |          |
               ------------
```

e que internamente use `<array>.reduce(function)`.

```js
function myReduce(coleccion, funcion) {
  return coleccion.reduce(funcion);
}

myReduce(
  [10, 20, 30, 40],
  (x,y) => x + y
);
```

Comprobamos

![](./img/myReduce.png)

## 1.13 Notación xeral sobre tipos e funcións

Imos definir unha notación xeral para falar de tipos, funcións, parámetros e retorno.

### 1.13.1 `add1`

Consideremos a función `add1`

```js
function add1(x) {
  return x + 1;
}
```

Quedáramos en que `add1`:

- Recibe un só parámetro `x` i esperamos ademais que sexa un Número.
- Devolve un só valor `x + 1` que tamén esperamos que sexa un Número.

Poderiamos expresar toda esa información do seguinte xeito

```js
//       add1 :: Number → Number
function add1(x) {
  return x + 1;
}
```

### 1.13.2 `add`

Consideremos agora a función `add`

```js
function add(x, y) {
  return x + y;
}
```

Quedáramos en que `add`:

- Recibe 2 parámetros `x` e `y` i esperamos ambos sexan Números.
- Devolve un só valor `x + y` que tamén esperamos que sexa un Número.

Poderiamos expresar toda esa información do seguinte xeito

```js
//       add :: Number → Number → Number
function add(x, y) {
  return x + y;
}
```

### 1.13.3 `<string>.toUpperCase` e `yell`

Estas dúas funcións son mais interesantes xa que fan o mesmo pero veremos como a súa descrición non coincide. Comezamos por `<string>.toUpperCase`

```js
"Hello".toUpperCase();
```

`toUpperCase`:

- Recibe 0 parámetros `()`.
- Devolve un só valor que esperamos sexa un `String`.

Poderiamos expresar toda esa información do seguinte xeito

```js
//      toUpperCase :: () → String
"Hello".toUpperCase();
```

O mais complicado deste caso 👆 é percatarnos de que pese a que `toUpperCase` utiliza o `String` `"Hello"`, éste non é pasado como parámetro `()` polo que non computa na nosa descrición. Porén, arranxamos iso con `yell`

```js
function yell(text) {
  return text.toUpperCase()
}
```

`yell`:

- Recibe 1 parámetro `text` que esperamos sexa un `String`.
- Devolve un só valor que esperamos sexa outro `String`.

Polo tanto

```js
//       yell :: String → String
function yell(text) {
  return text.toUpperCase()
}
```

Comparemos a descripción de `<string>.toUpperCase` coa de `yell`

```js
toUpperCase :: ()     → String
       yell :: String → String
```

Pese a que fan o mesmo, a descrición é diferente.

### 1.13.4 `<string>.toLowerCase` e `chillTheFunkOut`

O mesmo caso de antes, 2 funcións que fan o mesmo e teñen descricións diferentes.

```js
//      toLowerCase :: () → String
"HELLO".toLowerCase();

//       chillTheFunkOut :: String → String
function chillTheFunkOut(text) {
  return text.toLowerCase();
}
```

Comparemos as descricións de `<string>.toUpperCase`, `yell`, `<string>.toLowerCase` e `chillTheFunkOut`

```js
    toUpperCase :: ()     → String
           yell :: String → String
    toLowerCase :: ()     → String
chillTheFunkOut :: String → String
```

### 1.13.5 `<array>.map(function)` e `myMap`

Algo parecido acontece tamén con `<array>.map(function)` e `myMap`. Fan o mesmo pero teñen descricións diferentes. Imos usar `Fn` para simbolizar `Function`.

```js
//               map :: Fn → Array Number
[10, 20, 30, 40].map(x => x + 1);

//       myMap :: Array Number → Fn → Array Number
function myMap(coleccion, funcion) {
  return coleccion.map(funcion);
}
```

Comparemos as descricións de ambas

```js
  map ::                Fn → Array Number
myMap :: Array Number → Fn → Array Number
```

### 1.13.6 `<array>.filter(predicate)` e `myFilter`

O mesmo caso que con `map` e `myMap`

```js
//               filter :: Fn → Array Number
[10, 20, 30, 40].filter(x => x > 15);

//       myFilter :: Array Number → Fn → Array Number
function myFilter(coleccion, predicado) {
  return coleccion.filter(predicado);
}
```

Recordade que un `predicate` (predicado) é unha función (o que acontece é que é unha función que retorna un booleano: `true` ou `false`).

```js
  filter ::                Fn → Array Number
myFilter :: Array Number → Fn → Array Number
```

### 1.13.7 `<array>.reduce(function)` e `myReduce`

O mesmo caso de `map` e `myMap` e de `filter` e `myFilter`

```js
//               reduce :: Fn → Number
[10, 20, 30, 40].reduce((x,y) => x + y);

//       myReduce :: Array Number → Fn → Number
function myReduce(coleccion, funcion) {
  return coleccion.reduce(funcion);
}
```

Agora as descricións comparadas

```js
  reduce ::                Fn → Number
myReduce :: Array Number → Fn → Number
```

Novamente, 2 funcións que fan o mesmo teñen descricións diferentes.

### 1.13.8 Consideracións extra

1. A descrición de funcións mediante os tipos **non consideran un efecto secundario como unha saída!**.
2. Cando usamos a notación `<algo>.funcion(...)`, `algo` non conta como entrada.

### 1.13.9 Derivando unha fórmula xenérica para `myMap`

Recordemos `myMap`

```js
function myMap(coleccion, funcion) {
  return coleccion.map(funcion);
}
```

`myMap` pode ter todas estas descricións (pode incluso ter máis)

```js
myMap :: Array Number → Fn → Array String
myMap :: Array Number → Fn → Array Number
myMap :: Array String → Fn → Array String
myMap :: Array String → Fn → Array Number
```

É certo que todavía no vimos exemplos de función coa seguinte forma ou descrición

```js
nonVista1 :: Number → String
nonVista2 :: String → Number
```

pero existen.

> Qué é o que cambia nas descricións de `myMap`?

`String` e `Number`

> Podemos facer ainda máis xenérica a descrición de `myMap`?

Sí que podemos. Do mesmo xeito que é costume usar `x` e `y` como nomes dos parametros das funcións que como `add` reciben 2 números. Recordemos 👇

```js
function add(x, y) {
  return x + y;
}
```

É costume usar `a` e `b` do mesmo xeito na descrición de funcións. É dicir 👇

```js
myMap :: Array a → Fn → Array b
```

E ao igual que `x` e `y` poden valer calquera número

```
add(3,5);
add(9,14);
```

`a` e `b` poden ser calquera tipo

```js
myMap :: Array a → Fn → Array b

// a: Number, b: Number
myMap :: Array Number → Fn → Array Number

// a: String, b: String
myMap :: Array String → Fn → Array String

// a: Number, b: String
myMap :: Array Number → Fn → Array String

// a: String, b: Number
myMap :: Array String → Fn → Array Number
```

Agora todas xuntas

```js
myMap :: Array a      → Fn → Array b
myMap :: Array Number → Fn → Array Number
myMap :: Array String → Fn → Array String
myMap :: Array Number → Fn → Array String
myMap :: Array String → Fn → Array Number
```

### 1.13.10 Cal é o tipo da función `Fn` que aparece en `myMap`?

Vexamos uns cantos exemplos de funcións que sabemos que funcionan con `map` e tamén con `myMap`

```js
//       add1 :: Number → Number
function add1(x) {
  return x + 1;
}

//       yell :: String → String
function yell(text) {
  return text.toUpperCase();
}
```

É dicir

```js
add1 :: Number → Number
yell :: String → String
```

Parece que teñen a forma

```js
xxxx :: a → a
```

Todas xuntas

```js
xxxx :: a      → a
add1 :: Number → Number
yell :: String → String
```

**NOTA**: Na clase do mércores 19 veremos polo menos un exemplo de funcións que teñan a seguinte forma

```js
xxx1 :: String → Number
xxx2 :: Number → String
```

A forma das funcións `Fn` que admite `map` e polo tanto `myMap` é

```js
mapeable :: a → b
```

## 1.14 Exemplo de clase `myMap` e `String`s

```js
//       myMap :: Array a → Fn → Array b
function myMap(coleccion, funcionMapeable) {
  return coleccion.map(funcionMapeable);
}

//       add100 :: Number → Number
function add100(number) {
  return x + 100;
}

myMap([1,2,3,4,5], number => number + 100);

const arrayDeStrings = ["ola", "hello", "hallo", "hola";

textos


//       yell :: String → String
function yell(texto) {
  return texto.upUpperCase();  // 👈👀 recordade o return
}

myMap(textos, yell);

textos.map(yell);
```

TODO: En breve subo o resultado de executalo na consola do Firefox.
