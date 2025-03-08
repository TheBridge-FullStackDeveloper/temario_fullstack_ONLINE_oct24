# React

React es una biblioteca de JavaScript utilizada para construir interfaces de usuario interactivas y eficientes para aplicaciones web. Una de las características fundamentales de React es el uso de componentes reutilizables que encapsulan la lógica y la interfaz de usuario de una parte específica de la aplicación.

## ¿Qué es React?

React es una biblioteca de JavaScript de código abierto desarrollada por Facebook. Se centra en la creación de interfaces de usuario (UI) declarativas y basadas en componentes. En lugar de trabajar con el DOM directamente, React introduce un modelo de programación basado en componentes, donde cada componente es una pieza aislada y reutilizable de la interfaz de usuario.

## JSX en React

Una de las características más distintivas de React es su uso de JSX (JavaScript XML), una extensión de JavaScript que permite escribir HTML dentro de archivos de JavaScript. JSX facilita la creación de componentes React al combinar la lógica JavaScript con la estructura del marcado HTML.

Por ejemplo, un componente simple en React utilizando JSX se vería así:

```jsx
import React from "react";

function Saludo(props) {
  return <h1>Hola, {props.nombre}!</h1>;
}

export default Saludo;
```

En este ejemplo, `Saludo` es un componente de función que toma un prop `nombre` y muestra un saludo personalizado utilizando JSX.

## Componentes en React

En React, los componentes son bloques de construcción fundamentales que representan partes independientes y reutilizables de la interfaz de usuario. Los componentes pueden ser simples o complejos, y se componen entre sí para formar la estructura de la aplicación. Esta arquitectura basada en componentes facilita la creación, mantenimiento y prueba de aplicaciones web escalables.

## El Hook useState

`useState` es un hook de React que permite a los componentes de función mantener y actualizar su propio estado interno. Antes de la introducción de los hooks en React 16.8, el estado solo podía ser utilizado en componentes de clase. Con el hook `useState`, los componentes de función pueden tener estado, lo que simplifica la gestión del estado en aplicaciones React y fomenta el uso de componentes funcionales sobre los componentes de clase.

### Uso Básico de useState

El hook `useState` se utiliza comúnmente dentro de un componente de función de la siguiente manera:

```jsx
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>El contador es: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>Incrementar</button>
    </div>
  );
}
```

En este ejemplo, `useState` inicializa una variable de estado llamada `contador` con un valor inicial de 0. También devuelve una función `setContador` que nos permite actualizar el valor de `contador`.

El hook `useState` es una herramienta poderosa que simplifica la gestión del estado en aplicaciones React. Al utilizar `useState`, los componentes de función pueden mantener su propio estado interno de manera eficiente y elegante.