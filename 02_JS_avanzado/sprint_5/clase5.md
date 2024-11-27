# Métodos de Objeto en JavaScript

Los siguientes métodos son fundamentales para manipular y trabajar con objetos en JavaScript, proporcionando herramientas para acceder, modificar y crear estructuras de datos complejas.

## Object.keys(objeto)

Devuelve un array con las claves (propiedades) del objeto. Es útil para obtener una lista de las propiedades de un objeto.

```javascript
const objeto = { a: 1, b: 2, c: 3 };
const keys = Object.keys(objeto);
console.log(keys); // Resultado: ['a', 'b', 'c']
```

## Object.values(objeto)

Devuelve un array con los valores de las propiedades del objeto. Facilita la obtención de los valores asociados a las claves.

```javascript
const objeto = { a: 1, b: 2, c: 3 };
const values = Object.values(objeto);
console.log(values); // Resultado: [1, 2, 3]
```

## Object.entries(objeto)

Devuelve un array de arrays donde cada subarray contiene un par clave-valor. Esto es útil para iterar sobre las propiedades de un objeto.

```javascript
const objeto = { a: 1, b: 2, c: 3 };
const entries = Object.entries(objeto);
console.log(entries); // Resultado: [['a', 1], ['b', 2], ['c', 3]]
```

# Métodos de Número en JavaScript

Los siguientes métodos son esenciales para realizar operaciones matemáticas, validar y formatear números en JavaScript.

## Number.parseFloat(cadena)

Convierte una cadena en un número de punto flotante. Es útil cuando se desea convertir datos de entrada en formato string a valores numéricos.

```javascript
const cadena = "3.14";
const numero = Number.parseFloat(cadena);
console.log(numero); // Resultado: 3.14
```

## Number.isNaN(valor)

Verifica si el valor proporcionado es NaN (Not a Number). Útil para validar si un valor es numérico.

```javascript
const resultado = Number.isNaN("abc");
console.log(resultado); // Resultado: true
```

## Number.toFixed(decimales)

Devuelve una cadena que representa el número con un número fijo de decimales. Facilita el formateo de números para su presentación.

```javascript
const numero = 5.6789;
const numeroFormateado = numero.toFixed(2);
console.log(numeroFormateado); // Resultado: '5.68'
```

# Métodos de String en JavaScript

Los siguientes métodos son importantes para trabajar con strings en JavaScript.

- `length`: Propiedad que devuelve la longitud de el string.

- `toUpperCase()`: Convierte el string a mayúsculas.

- `toLowerCase()`: Convierte el string a minúsculas.

- `trim()`: Elimina los espacios en blanco al principio y al final del string.