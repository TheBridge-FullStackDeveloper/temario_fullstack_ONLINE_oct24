# Funciones en JavaScript

## Descripción

En programación, una función es un bloque de código que realiza una tarea específica o calcula un valor. Las funciones permiten encapsular la lógica en un bloque reutilizable, lo que facilita la organización y el mantenimiento del código. En JavaScript, una función puede recibir parámetros y devolver un valor.

## Estructura de una Función

La estructura de una función en JavaScript es la siguiente:

```javascript
function miFuncion() {
  // Aquí va nuestro código
}
```

## Invocación de una Función

Puedes invocar una función de la siguiente manera:

```javascript
miFuncion();
```

## Ejemplo de una Función

```javascript
function sumar(a, b) {
  return a + b;
}

let resultado = sumar(5, 3);
console.log(resultado); // Esto imprimirá 8
```

En este ejemplo, la función sumar recibe dos parámetros, a y b, y devuelve la suma de los mismos.