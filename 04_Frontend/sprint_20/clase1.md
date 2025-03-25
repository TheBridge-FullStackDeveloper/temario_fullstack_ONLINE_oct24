# Props en React

En React, las props (abreviatura de "propiedades") son utilizadas para pasar datos y configuraciones desde un componente padre a un componente hijo. Esto permite la reutilización de componentes y la creación de componentes dinámicos y flexibles.

## Pasar Props

Para pasar props de un componente padre a un componente hijo, simplemente se incluyen como atributos al renderizar el componente hijo. Las props son accesibles dentro del componente hijo a través del objeto `props`.

```jsx
// Componente Padre
import ComponenteHijo from "./ComponenteHijo";

function App() {
  return (
    <div>
      <ComponenteHijo nombre="Juan" edad={30} />
    </div>
  );
}

export default App;
```

En el ejemplo anterior, estamos pasando dos props (`nombre` y `edad`) al componente `ComponenteHijo`.

## Acceder a Props en Componentes Hijos

Dentro del componente hijo, podemos acceder a las props utilizando el objeto `props`. Las props son de solo lectura y no deben ser modificadas directamente dentro del componente hijo (a menos que se trate de componentes controlados).

```jsx
// Componente Hijo

function ComponenteHijo(props) {
  return (
    <div>
      <p>Nombre: {props.nombre}</p>
      <p>Edad: {props.edad}</p>
    </div>
  );
}

export default ComponenteHijo;
```

En este ejemplo, el componente `ComponenteHijo` recibe las props `nombre` y `edad` del componente padre y las muestra en su renderizado.

## Props por Defecto

Es posible definir valores por defecto para las props en caso de que no se pasen desde el componente padre. Esto se logra utilizando la propiedad `defaultProps` en el componente hijo.

```jsx
// Componente Hijo con Props por Defecto

function ComponenteHijo(props) {
  return (
    <div>
      <p>Nombre: {props.nombre}</p>
      <p>Edad: {props.edad}</p>
    </div>
  );
}

ComponenteHijo.defaultProps = {
  nombre: "Usuario",
  edad: 18,
};

export default ComponenteHijo;
```

En este ejemplo, si el componente padre no pasa las props `nombre` y `edad`, el componente `ComponenteHijo` utilizará los valores por defecto especificados en `defaultProps`.

## Prop Types

Para garantizar que las props recibidas sean del tipo esperado, es recomendable utilizar PropTypes. Esto ayuda a detectar errores durante el desarrollo y proporciona una documentación clara sobre las props aceptadas por un componente.

```jsx
// Componente Hijo con PropTypes
import PropTypes from "prop-types";

function ComponenteHijo(props) {
  return (
    <div>
      <p>Nombre: {props.nombre}</p>
      <p>Edad: {props.edad}</p>
    </div>
  );
}

ComponenteHijo.propTypes = {
  nombre: PropTypes.string.isRequired,
  edad: PropTypes.number.isRequired,
};

export default ComponenteHijo;
```

En este ejemplo, estamos utilizando PropTypes para especificar que `nombre` debe ser una cadena (string) y `edad` debe ser un número (number). La propiedad `isRequired` indica que es obligatorio pasar estas props al componente hijo.