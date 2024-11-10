# El DOM (Document Object Model)

## Descripción

El DOM, o Document Object Model, es una representación de la estructura de un documento HTML que proporciona una forma de interactuar y manipular los elementos de la página mediante programación. Esencialmente, el DOM convierte una página web en un árbol de objetos que puedes manipular con JavaScript para cambiar su contenido, estructura y estilo.

## Métodos del DOM

El DOM ofrece una amplia gama de métodos que permiten interactuar, manipular y acceder a los elementos y nodos de un documento HTML. Estos métodos facilitan la modificación de la estructura, el estilo y el contenido de la página web. A continuación, se muestran algunos de los métodos del DOM más comunes y útiles:

### `document.getElementById(id)`

Este método devuelve un elemento por su ID. Es útil para acceder a un elemento específico en la página.

Ejemplo:

```javascript
let elemento = document.getElementById("miElemento");
```

### `document.querySelector(selector)`

El método `document.querySelector(selector)` devuelve el primer elemento que coincide con un selector CSS. Permite seleccionar elementos de manera más precisa.

Ejemplo:

```javascript
let elemento = document.querySelector(".claseCSS");
```

### `document.querySelectorAll(selector)`

El método `document.querySelectorAll(selector)` devuelve todos los elementos que coinciden con un selector CSS. Puedes obtener una lista de elementos que cumplan ciertas condiciones.

Ejemplo:

```javascript
let elementos = document.querySelectorAll("p");
```

## Propiedades del DOM

Además de los métodos, el DOM también ofrece propiedades que te permiten acceder y manipular el contenido y los atributos de los elementos. Aquí tienes algunas propiedades comunes:

### `innerHTML`

La propiedad `innerHTML` se utiliza para obtener o establecer el contenido HTML de un elemento. Puedes modificar el contenido de un elemento de manera dinámica.

Ejemplo:

```javascript
let elemento = document.getElementById("miElemento");
elemento.innerHTML = "<p>Nuevo contenido</p>";
```

### `textContent`

La propiedad `textContent` se utiliza para obtener o establecer el contenido de texto de un elemento. Es útil para trabajar con texto sin formato dentro de elementos.

Ejemplo:

```javascript
let elemento = document.getElementById("miElemento");
elemento.textContent = "Nuevo texto";
```

### `setAttribute(name, value)`

El método `setAttribute(name, value)` se utiliza para establecer un atributo en un elemento. Puedes cambiar o agregar atributos a elementos HTML.

Ejemplo:

```javascript
let elemento = document.getElementById("miElemento");
elemento.setAttribute("class", "nuevaClase");
```