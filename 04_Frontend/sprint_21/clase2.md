# Custom Hooks en React

Los Custom Hooks son una característica poderosa de React que nos permiten reutilizar lógica de estado y efectos entre componentes de manera fácil y eficiente.

## ¿Qué son los Custom Hooks?

Los Custom Hooks son funciones JavaScript que utilizan el prefijo "use" y pueden contener lógica de estado, efectos secundarios y cualquier otra lógica que necesitemos compartir entre componentes de manera reutilizable.

## Crear un Custom Hook

Crear un Custom Hook es tan simple como definir una función que utiliza Hooks de React. Por ejemplo, creemos un Custom Hook que maneje el estado de un contador:

```jsx
import { useState } from "react";

function useContador() {
  const [contador, setContador] = useState(0);

  const incrementar = () => {
    setContador((prevContador) => prevContador + 1);
  };

  const decrementar = () => {
    setContador((prevContador) => prevContador - 1);
  };

  return { contador, incrementar, decrementar };
}

export default useContador;
```

En este ejemplo, `useContador` es un Custom Hook que utiliza `useState` para manejar el estado del contador y devuelve funciones para incrementar y decrementar el contador, así como el valor actual del contador.

## Uso de un Custom Hook

Podemos usar nuestro Custom Hook `useContador` en cualquier componente funcional de la siguiente manera:

```jsx
import React from "react";
import useContador from "./useContador";

function App() {
  const { contador, incrementar, decrementar } = useContador();

  return (
    <div>
      <p>Contador: {contador}</p>
      <button onClick={incrementar}>Incrementar</button>
      <button onClick={decrementar}>Decrementar</button>
    </div>
  );
}

export default App;
```

En este ejemplo, `App` utiliza nuestro Custom Hook `useContador` para manejar el estado del contador y las funciones para incrementar y decrementar el valor.

## Beneficios de los Custom Hooks

1. **Reutilización de lógica**: Permite reutilizar la lógica de estado y efectos entre componentes.
2. **Separación de preocupaciones**: Ayuda a separar la lógica relacionada en Custom Hooks, lo que hace que nuestros componentes sean más simples y mantenibles.
3. **Abstracción de la complejidad**: Permite encapsular la complejidad de la lógica en un Custom Hook y utilizarlo fácilmente en múltiples componentes.

Los Custom Hooks son una herramienta poderosa en React que nos permite escribir código más limpio, modular y reutilizable. Al crear Custom Hooks específicos para nuestras necesidades, podemos mejorar la estructura y la organización de nuestras aplicaciones React.