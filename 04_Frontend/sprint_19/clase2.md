# Manejo de Formularios y Estilos en React

## Manejo de Formularios en React

En React, el manejo de formularios implica el uso de componentes controlados y no controlados. Los componentes controlados son aquellos cuyos valores de entrada son controlados por el estado de React, mientras que los componentes no controlados dejan que el DOM maneje el estado del formulario.

### Componentes Controlados

Los componentes controlados en React están vinculados al estado de React, lo que significa que su valor se sincroniza con el estado del componente.

```jsx
import React, { useState } from "react";

function FormularioControlado() {
  const [nombre, setNombre] = useState("");
  const [email, setEmail] = useState("");

  const handleChangeNombre = (event) => {
    setNombre(event.target.value);
  };

  const handleChangeEmail = (event) => {
    setEmail(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    // Realizar acciones con los datos del formulario
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Nombre:
        <input type="text" value={nombre} onChange={handleChangeNombre} />
      </label>
      <label>
        Email:
        <input type="email" value={email} onChange={handleChangeEmail} />
      </label>
      <button type="submit">Enviar</button>
    </form>
  );
}

export default FormularioControlado;
```

### Componentes No Controlados

En los componentes no controlados, el valor del formulario se maneja directamente por el DOM, en lugar de ser controlado por el estado de React.

```jsx
import React from "react";

function FormularioNoControlado() {
  const inputNombre = React.createRef();
  const inputEmail = React.createRef();

  const handleSubmit = (event) => {
    event.preventDefault();
    const nombre = inputNombre.current.value;
    const email = inputEmail.current.value;
    // Realizar acciones con los datos del formulario
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Nombre:
        <input type="text" ref={inputNombre} />
      </label>
      <label>
        Email:
        <input type="email" ref={inputEmail} />
      </label>
      <button type="submit">Enviar</button>
    </form>
  );
}

export default FormularioNoControlado;
```

## Estilos en React

En React, los estilos pueden aplicarse utilizando CSS tradicional, entre otras opciones.

### CSS tradicional

En el enfoque de CSS tradicional, cada componente tiene su propio archivo de estilos CSS, donde los estilos están encapsulados y solo se aplican al componente correspondiente.

Por ejemplo, supongamos que tienes un componente `Button`. Aquí tienes cómo podrías aplicar estilos CSS modular a estos componentes:

```jsx
import styles from "./Button.module.css";

function Button() {
  return <button className={styles.button}>Enviar</button>;
}

export default Button;
```

Es importante saber que aquí usamos `className`para las clases, porque la palabra `class` es una palabra reservada en React.