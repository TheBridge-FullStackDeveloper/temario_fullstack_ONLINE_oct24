# Bucles en JavaScript

## Descripción

Los bucles en programación permiten ejecutar un bloque de código repetidamente hasta que se cumple cierta condición. Los bucles son esenciales para realizar tareas repetitivas y procesar datos en una colección de elementos.

En JavaScript, hay varios tipos de bucles, pero los más comunes son:

### `for`

El bucle `for` se utiliza para ejecutar un bloque de código un número específico de veces, controlado por una variable de control. Es ideal cuando se conoce de antemano la cantidad de iteraciones necesarias.

Ejemplo:

```javascript
for (let i = 0; i < 5; i++) {
  console.log(`Iteración ${i}`);
}
```

### `while`

El bucle `while` se utiliza para ejecutar un bloque de código mientras una condición sea verdadera. Es útil cuando no se conoce de antemano cuántas iteraciones se necesitarán.

Ejemplo:

```javascript
let contador = 0;
while (contador < 5) {
  console.log(`Iteración ${contador}`);
  contador++;
}
```

### `do...while`

El bucle `do...while` es similar al `while`, pero garantiza que se ejecute al menos una vez antes de verificar la condición. Esto es útil cuando deseas asegurarte de que el bloque de código se ejecute al menos una vez.

Ejemplo:

```javascript
let x = 0;
do {
  console.log(`Iteración ${x}`);
  x++;
} while (x < 5);
```

### `for...of`

El bucle `for...of` se utiliza para iterar sobre elementos de cualquier objeto iterable. Es especialmente útil cuando necesitas recorrer los elementos de una colección.

Ejemplo:

```javascript
let frutas = ["manzana", "pera", "uva"];
for (let fruta of frutas) {
  console.log(fruta);
}
```

### `for...in`

El bucle `for...in` se utiliza para iterar sobre las propiedades enumerables de un objeto. Es útil para recorrer objetos y obtener las claves de sus propiedades.

Ejemplo:

```javascript
let persona = {
  nombre: "Juan",
  edad: 30,
  ciudad: "Madrid",
};

for (let propiedad in persona) {
  console.log(propiedad + ": " + persona[propiedad]);
}
```