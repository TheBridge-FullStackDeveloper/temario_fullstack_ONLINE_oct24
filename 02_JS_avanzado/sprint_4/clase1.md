# Funciones Puras, Arrow Functions y Métodos de Array en JavaScript

## Funciones Puras

En JavaScript, una función pura es una función que produce un resultado basado únicamente en sus entradas (argumentos) y no tiene efectos secundarios en el entorno. Esto significa que:

- El resultado de una función pura es predecible y siempre es el mismo para las mismas entradas.
- No modifica ni depende de variables externas o globales.
- No realiza acciones que afecten al entorno global, como cambiar el DOM.

Las funciones puras son esenciales en programación funcional y son útiles para escribir código más predecible y fácil de mantener.

### Ejemplos de funciones puras

```javascript
// Función pura que suma dos números
function suma(a, b) {
  return a + b;
}

// Función pura que multiplica un número por sí mismo
function cuadrado(x) {
  return x * x;
}

// Función pura que concatena dos cadenas
function concatenarCadenas(cadena1, cadena2) {
  return cadena1 + " " + cadena2;
}

// Función pura que verifica si un número es par
function esNumeroPar(numero) {
  return numero % 2 === 0;
}

// Función pura que calcula el área de un rectángulo
function calcularAreaRectangulo(ancho, alto) {
  return ancho * alto;
}
```

## Arrow Functions (Funciones Flecha)

Las Arrow Functions son una característica introducida en ECMAScript 6 (también conocido como ES6) para definir funciones de manera más concisa en JavaScript. Las ventajas de las Arrow Functions incluyen:

- Sintaxis más breve, especialmente útil para funciones pequeñas y simples.
- Utilizan un "this" léxico, lo que significa que heredan el valor "this" del contexto en el que se definen.

### Ejemplos de Arrow Function:

```javascript
// Arrow Function que suma dos números
const suma = (a, b) => a + b;

// Arrow Function que calcula el cuadrado de un número
const cuadrado = (x) => x * x;

// Arrow Function que concatena dos cadenas
const concatenarCadenas = (cadena1, cadena2) => cadena1 + " " + cadena2;

// Arrow Function que verifica si un número es par
const esNumeroPar = (numero) => numero % 2 === 0;

// Arrow Function que calcula el área de un triángulo
const calcularAreaTriangulo = (base, altura) => (base * altura) / 2;
```

Las Arrow Functions pueden tener llaves `{}` si el cuerpo de la función contiene múltiples declaraciones o necesita realizar más de una operación. En ese caso, se utiliza la sintaxis de llaves y se debe incluir la palabra clave `return` explícitamente si se desea devolver un valor.

```javascript
const suma = (a, b) => {
  // Realiza múltiples operaciones
  const resultado = a + b;
  console.log("La suma es: " + resultado);
  return resultado;
};
```

## Métodos de Array

Los métodos de Array son funciones incorporadas en JavaScript para realizar diversas operaciones en los elementos de un array. Estos métodos proporcionan una amplia gama de funcionalidades para manipular, filtrar, ordenar y transformar arrays. Algunos de los métodos más comunes incluyen:

- `push`: Agrega elementos al final del array.

- `pop`: Elimina el último elemento del array.

- `unshift`: Agrega elementos al principio del array.

- `shift`: Elimina el primer elemento del array.

- `join`: Convierte los elementos del array en una cadena separada por un delimitador.

- `slice`: Crea un nuevo array copiando una porción del array original.

- `splice`: Modifica el contenido del array al eliminar, reemplazar o agregar elementos.

- `map`: Crea un nuevo array aplicando una función a cada elemento del array original.

- `filter`: Crea un nuevo array con elementos que cumplan ciertos criterios.

- `reduce`: Reduce el array a un solo valor aplicando una función acumuladora.

### Ejemplos

```javascript
const numeros = [1, 2, 3, 4, 5];

// Usar map para duplicar cada número
const duplicados = numeros.map((num) => num * 2);

// Usar filter para encontrar números pares
const pares = numeros.filter((num) => num % 2 === 0);

// Usar reduce para sumar todos los números
const suma = numeros.reduce((acumulador, num) => acumulador + num, 0);
```