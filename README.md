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

## 1.1 Definición dunha función

```js
function add1(x) {
  return x + 1;
}
```

## 1.2 Invocación dunha función

```js
add1(9) // Devolve un 10
add1(4) // Devolve un 5
```

## 1.3 Anatomía dunha función (definición e invocación)

Vamos a poñerlle nome a cada unha das partes dunha función

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

É dicir só nos interesan as entradas (**IN**) e saidas (**OUT**). Por exemplo, `magic` ten

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

Esto é o que acontece:

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

```
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

Poderíamos dicir que  `efectosSecundariosAndNoReturn` ten

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

Se `map` recibe como argumento unha función con características diferentes non vai funcionar. Por exemplo se recibe unha función con 3 entradas falla.

### 1.8.2 `<array>.filter(function)`

![](./img/filter-example-1.png)

> ¿Qué tipo de función agarda `filter` como argumento?

Unha como `greaterThan15`. É dicir:

- 1 entrada (`x`)
- 1 saida (o resultado de facer `x > 15`).

Pero neste caso ademáis a saida debe ser ou `true` ou `false`. A este tipo de funcións chamamolas **predicados**.

Se `filter` recibe como argumento unha función con características diferentes non vai funcionar. Por exemplo se recibe unha función con 3 entradas falla ou se recibe unha función que non devolve `true` ou `false`.

### 1.8.3 `<array>.reduce(function)`

![](./img/reduce-example-1.png)

> ¿Qué tipo de función agarda `reduce` como argumento?

Unha como `minus`. É dicir:

- 2 entradas (`acc`, `x`)
- 1 saida (o resultado de facer `acc - x`).

Neste caso preferimos poñer un nome máis descritivo a os parámetros da función `minus`. En lugar de `x`e `y` poñemos `acc` (diminutivo de `accumulator`) e `x` porque cando lla pasamos a `reduce` fai o seguinte:

1. `acc` toma o valor do primeiro número do array (`acc = 10`) e `x` o do segundo (`x = 20`).
2. executamos o `return` (`acc - x`) obtendo o valor `-10` (`10 - 20 = -10`). Este `-10` vai se o valor do próximo `acc`.
3. `acc` toma o valor do último `return` (`acc = -10`) e `x`o do seguinte valor do array (`x = 30`).
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

As Arrow Functions teñen algunha inconsistencia ao respecto da notación.

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

As Arrow Functions levan un `return` implícito, é dicir as duas funcións que veñen a continuación son equivalente.

```js
(x, y, z) => x + y - z;
(x, y, z) => return x + y - z;
```