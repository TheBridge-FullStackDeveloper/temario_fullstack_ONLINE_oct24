# Nodos en el DOM

## Descripción

En el Document Object Model (DOM) de JavaScript, los nodos son elementos fundamentales que componen la estructura de un documento HTML. Los nodos representan diferentes partes de la página web, como elementos HTML, texto y atributos. La manipulación de nodos es esencial para cambiar dinámicamente el contenido y la estructura de una página web.

## Métodos para la Creación de Nodos

### `document.createElement(tagName)`

Este método permite crear un nuevo elemento con la etiqueta especificada. Puedes utilizarlo para generar dinámicamente elementos HTML y luego agregarlos al DOM.

Ejemplo:

```javascript
const nuevoParrafo = document.createElement("p");
```

### `document.createTextNode(text)`

El método `document.createTextNode(text)` crea un nuevo nodo de texto con el contenido especificado. Puedes utilizarlo para insertar texto dentro de un elemento HTML.

Ejemplo:

```javascript
const nuevoTexto = document.createTextNode(
  "Este es un nuevo párrafo de texto."
);
```

## Métodos para la Manipulación de Nodos

### `element.appendChild(childElement)`

El método `element.appendChild(childElement)` se utiliza para agregar un nuevo nodo como hijo de un elemento. Puedes construir estructuras jerárquicas en el DOM al añadir elementos secundarios a elementos principales.

Ejemplo:

```javascript
const contenedor = document.getElementById("miContenedor");
const nuevoParrafo = document.createElement("p");
contenedor.appendChild(nuevoParrafo);
```

### `element.removeChild(childElement)`

El método `element.removeChild(childElement)` elimina un nodo hijo de un elemento. Puedes usarlo para eliminar elementos del DOM de manera selectiva.

Ejemplo:

```javascript
const contenedor = document.getElementById("miContenedor");
const parrafoAEliminar = document.getElementById("parrafoAEliminar");
contenedor.removeChild(parrafoAEliminar);
```

### `element.replaceChild(newChild, oldChild)`

El método `element.replaceChild(newChild, oldChild)` reemplaza un nodo hijo con otro nodo. Esto es útil cuando deseas actualizar el contenido o la estructura de un elemento existente en el DOM.

Ejemplo:

```javascript
const contenedor = document.getElementById("miContenedor");
const nuevoParrafo = document.createElement("p");
const parrafoAntiguo = document.getElementById("parrafoAntiguo");
contenedor.replaceChild(nuevoParrafo, parrafoAntiguo);
```

## Otro Método para la Manipulación del DOM

### `element.insertAdjacentHTML(position, text)`

El método `element.insertAdjacentHTML(position, text)` permite insertar HTML en un punto específico en relación con el elemento actual. Puedes utilizarlo para inyectar fragmentos HTML en una página web.

Ejemplo:

```javascript
const elemento = document.getElementById("miElemento");
elemento.insertAdjacentHTML("beforeend", "<p>Texto a insertar</p>");
```