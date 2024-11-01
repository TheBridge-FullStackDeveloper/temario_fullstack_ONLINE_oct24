# Conceptos Básicos de JavaScript

JavaScript es un lenguaje de programación ampliamente utilizado en el desarrollo web. En este texto, exploraremos a fondo los conceptos esenciales de JavaScript y cómo se aplican en la creación de sitios web dinámicos y funcionales.

JavaScript, a menudo abreviado como JS, es un lenguaje interpretado que se ejecuta en el navegador del cliente. Es versátil y permite a los desarrolladores web agregar interactividad, validar formularios, realizar solicitudes a servidores y mucho más. A lo largo de este texto, profundizaremos en temas clave, como variables, estructuras de control, funciones y manipulación del DOM, para ayudarte a comprender y utilizar JavaScript de manera efectiva en tus proyectos web.

## Variables en JavaScript

Una variable es un contenedor para almacenar datos que pueden cambiar durante la ejecución de un programa. Las variables se utilizan para almacenar valores como números, texto, objetos, etc..., y se pueden manipular y utilizar en diversas operaciones dentro de un programa.

En JavaScript, las variables se pueden declarar utilizando las palabras clave `var`, `let`, o `const`.

- `var`: Se utilizaba anteriormente para declarar variables, pero su uso ha sido reemplazado en gran medida por `let` y `const`.
- `let`: Se utiliza para declarar variables que pueden ser reasignadas.
- `const`: Se utiliza para declarar variables con un valor constante que no puede ser reasignado.

### Ejemplos

```javascript
// Declaración de variables
var edad = 30; // Variable declarada con var
let nombre = "Juan"; // Variable declarada con let
const PI = 3.1416; // Variable declarada con const

// Reasignación de variables
edad = 31; // Puedes reasignar una variable declarada con let
// PI = 3.15; // No puedes reasignar una variable declarada con const, esto generaría un error.
```

## Tipos de datos en JavaScript

JavaScript es un lenguaje de programación de tipado dinámico, lo que significa que no necesitas declarar explícitamente el tipo de datos que almacenará una variable. Los principales tipos de datos en JavaScript son:

- **Number**: Representa números, ya sean enteros o decimales.

  Ejemplo:

  ```javascript
  let edad = 30; // Número entero
  let precio = 19.99; // Número decimal
  ```

- **String**: Representa cadenas de caracteres, es decir, texto.

  Ejemplo:

  ```javascript
  let nombre = "Juan";
  let mensaje = "Hola, ¿cómo estás?";
  ```

- **Boolean**: Representa valores `true` o `false`.

  Ejemplo:

  ```javascript
  let esMayorDeEdad = true;
  let esCasado = false;
  ```

- **Object**: Representa un conjunto de propiedades clave-valor.

  Ejemplo:

  ```javascript
  let persona = {
    nombre: "Juan",
    edad: 30,
    casado: false,
  };
  ```

- **Array**: Representa una lista ordenada de valores.

  Ejemplo:

  ```javascript
  let colores = ["rojo", "verde", "azul"];
  let puntuaciones = [10, 8, 5, 9];
  ```

- **Null**: Representa la ausencia intencionada de cualquier valor o entidad de objeto.

  Ejemplo:

  ```javascript
  let valorNulo = null;
  ```

- **Undefined**: Representa una variable que se ha declarado pero aún no se ha asignado ningún valor.

  Ejemplo:

  ```javascript
  let variableSinValor;
  console.log(variableSinValor); // Imprimirá "undefined"
  ```

## Declaración y asignación de variables

Tenemos que tener en cuenta dos conceptos con las variables. Uno es la declaración de la variable y el otro es la asignación.

Las variables declaradas con let se pueden declarar sin asignar un valor de inicio y luego asignarles un valor más tarde. Las variables declaradas con const se deben declarar y asignar al inicializarlas, y no pueden ser reasignadas posteriormente.

Ejemplos:

```javascript
let edad; // Declaración de una variable sin asignar valor
edad = 30; // Asignación de un valor a la variable

const PI = 3.1416; // Declaración y asignación de una variable constante
```