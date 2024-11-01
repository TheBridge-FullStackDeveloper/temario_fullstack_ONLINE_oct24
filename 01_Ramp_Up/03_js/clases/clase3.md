# Arrays en JavaScript

## Descripción

Un array en JavaScript es una estructura de datos que se utiliza para almacenar una colección de elementos. Estos elementos pueden ser de cualquier tipo de datos, como números, cadenas, objetos u otros arrays. Los elementos en un array están indexados numéricamente y el índice comienza desde 0.

## Métodos comunes de los Arrays

### `push()`

El método `push()` se utiliza para agregar uno o más elementos al final del array y devuelve la nueva longitud del array. Esto es útil para ampliar un array existente.

Ejemplo:

```javascript
let frutas = ["manzana", "pera"];
let nuevaLongitud = frutas.push("uva", "plátano");
// frutas ahora es ["manzana", "pera", "uva", "plátano"]
// nuevaLongitud es 4
```

### `pop()`

El método `pop()` elimina el último elemento del array y lo devuelve. Esto es útil cuando deseas quitar un elemento del final del array.

Ejemplo:

```javascript
let frutas = ["manzana", "pera", "uva"];
let ultimaFruta = frutas.pop();
// frutas ahora es ["manzana", "pera"]
// ultimaFruta es "uva"
```

### `shift()`

El método `shift()` elimina el primer elemento del array y lo devuelve. Además, ajusta el índice de los otros elementos en el array. Esto es útil para eliminar el primer elemento de un array.

Ejemplo:

```javascript
let frutas = ["manzana", "pera", "uva"];
let primeraFruta = frutas.shift();
// frutas ahora es ["pera", "uva"]
// primeraFruta es "manzana"
```

### `unshift()`

El método `unshift()` se utiliza para agregar uno o más elementos al inicio del array y devuelve la nueva longitud del array.

Ejemplo:

```javascript
let frutas = ["pera", "uva"];
let nuevaLongitud = frutas.unshift("manzana", "plátano");
// frutas ahora es ["manzana", "plátano", "pera", "uva"]
// nuevaLongitud es 4
```

### `concat()`

El método `concat()` combina dos o más arrays y devuelve un nuevo array que contiene los elementos de los arrays combinados. El array original no se modifica.

Ejemplo:

```javascript
let frutas = ["manzana", "pera"];
let verduras = ["zanahoria", "brócoli"];
let comida = frutas.concat(verduras);
// comida es ["manzana", "pera", "zanahoria", "brócoli"]
```

### `join()`

El método `join()` se utiliza para convertir los elementos de un array en una cadena de caracteres, unidos por el separador especificado. Esto es útil cuando deseas representar los elementos del array como una cadena.

Ejemplo:

```javascript
let frutas = ["manzana", "pera", "uva"];
let cadena = frutas.join(", ");
// cadena es "manzana, pera, uva"
```

### `slice()`

El método `slice()` devuelve una copia superficial de una porción del array en un nuevo array. El array original no se modifica. Puedes especificar el índice de inicio y el índice de final para obtener una porción específica del array.

Ejemplo:

```javascript
let frutas = ["manzana", "pera", "uva", "plátano", "kiwi"];
let porción = frutas.slice(1, 4);
// porción es ["pera", "uva", "plátano"]
```