# Eventos en JavaScript

## Descripción

En JavaScript, los eventos son acciones que ocurren en un documento HTML y a los cuales puedes responder programáticamente. Puedes registrar funciones que se ejecuten cuando un evento específico ocurra en un elemento del DOM. Los eventos son fundamentales para la interactividad en una página web.

## Registro de Eventos con `addEventListener`

Para registrar eventos en JavaScript, utilizamos el método `addEventListener`. La sintaxis general es la siguiente:

```javascript
elemento.addEventListener(evento, función);
```

Donde:

- `elemento` es el elemento del DOM al que deseas agregar el evento.
- `evento` es el nombre del evento que deseas capturar (por ejemplo, "click", "mouseover", "keydown").
- `función` es la función que se ejecutará cuando ocurra el evento.

## `click`

Se desencadena cuando se hace clic en un elemento. Puedes utilizar este evento para crear interactividad, como cambiar el color de un botón al hacer clic en él.

```javascript
elemento.addEventListener("click", function () {
  // Cambiar el color de fondo al hacer clic en el elemento
  elemento.style.backgroundColor = "blue";
});
```

## `mouseover`

Se desencadena cuando el puntero del ratón entra en un elemento. Es útil para mostrar información adicional cuando el usuario pasa el ratón sobre un elemento.

```javascript
elemento.addEventListener("mouseover", function () {
  // Mostrar un mensaje emergente cuando el ratón entra en el elemento
  alert("¡Pasa el ratón por encima!");
});
```

## `mouseout`

Se desencadena cuando el puntero del ratón sale de un elemento. Puedes utilizarlo para ocultar información adicional cuando el usuario se aleja de un elemento.

```javascript
elemento.addEventListener("mouseout", function () {
  // Ocultar el mensaje emergente cuando el ratón sale del elemento
  alert("Adiós, hasta la próxima");
});
```

## `mousemove`

Se desencadena cuando el puntero del ratón se mueve sobre un elemento. Este evento es útil para realizar un seguimiento de la posición del ratón en relación con un elemento.

```javascript
elemento.addEventListener("mousemove", function (event) {
  // Obtener las coordenadas del puntero del ratón en relación con el elemento
  const x = event.clientX - elemento.getBoundingClientRect().left;
  const y = event.clientY - elemento.getBoundingClientRect().top;

  console.log("Posición del ratón: x=" + x + ", y=" + y);
});
```

## `mousedown`

Se desencadena cuando se presiona un botón del ratón mientras está sobre un elemento. Puedes utilizarlo para iniciar acciones cuando se hace clic y se mantiene presionado el botón del ratón.

```javascript
elemento.addEventListener("mousedown", function () {
  // Iniciar una acción cuando se presiona el botón del ratón en el elemento
  iniciarArrastre(elemento);
});
```

## `mouseup`

Se desencadena cuando se libera un botón del ratón sobre un elemento. Es útil para finalizar acciones después de soltar un botón del ratón.

```javascript
elemento.addEventListener("mouseup", function () {
  // Finalizar una acción cuando se suelta el botón del ratón en el elemento
  finalizarArrastre(elemento);
});
```

## Ejemplos de Eventos de Teclado

## `keydown`

Se desencadena cuando se presiona una tecla.

```javascript
document.addEventListener("keydown", function (event) {
  // Código a ejecutar cuando se presiona una tecla
  console.log("Tecla presionada: " + event.key);
});
```

## `keyup`

Se desencadena cuando se suelta una tecla.

```javascript
document.addEventListener("keyup", function (event) {
  // Código a ejecutar cuando se suelta una tecla
  console.log("Tecla liberada: " + event.key);
});
```

## `keyup`

Se desencadena cuando se suelta una tecla.

```javascript
document.addEventListener("keyup", function (event) {
  // Código a ejecutar cuando se suelta una tecla
  console.log("Tecla liberada: " + event.key);
});
```