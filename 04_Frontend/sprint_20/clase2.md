# Uso del Contexto en React

El contexto en React es una forma de pasar datos a través del árbol de componentes sin tener que pasar props manualmente en cada nivel. Esto es especialmente útil para datos que son necesarios por muchos componentes en la aplicación.

## createContext

`createContext` es una función que se utiliza para crear un contexto en React. Este contexto puede contener un valor que será accesible para todos los componentes hijos que lo consuman.

```jsx
// Contexto.js
import { createContext } from "react";

const MiContexto = createContext();

export default MiContexto;
```

En este ejemplo, estamos creando un contexto llamado `MiContexto` utilizando `createContext`.

## Proveedor de Contexto

Para proporcionar el valor del contexto a los componentes hijos, utilizamos el componente `Provider` que se proporciona con el contexto creado.

```jsx
// App.js
import MiContexto from "./Contexto";
import ComponenteHijo from "./ComponenteHijo";

function App() {
  const valorContexto = "Hola desde el contexto";

  return (
    <MiContexto.Provider value={valorContexto}>
      <ComponenteHijo />
    </MiContexto.Provider>
  );
}

export default App;
```

En este ejemplo, estamos envolviendo el componente `ComponenteHijo` dentro del `Provider` de `MiContexto` y pasando el valor del contexto mediante la prop `value`.

## useContext

Para acceder al valor del contexto dentro de un componente hijo, utilizamos el hook `useContext`. Este hook toma como argumento el contexto que queremos consumir y devuelve el valor proporcionado por el `Provider` más cercano en la jerarquía.

```jsx
// ComponenteHijo.js
import { useContext } from "react";
import MiContexto from "./Contexto";

function ComponenteHijo() {
  const valorContexto = useContext(MiContexto);

  return <p>{valorContexto}</p>;
}

export default ComponenteHijo;
```

En este ejemplo, estamos utilizando `useContext` dentro del componente `ComponenteHijo` para obtener el valor del contexto `MiContexto` que fue proporcionado por el `Provider` en el componente `App`.

## Valor por Defecto

Es posible proporcionar un valor por defecto al crear el contexto, para el caso en que no exista un `Provider` que provea un valor específico.

```jsx
// Contexto.js
import { createContext } from "react";

const MiContexto = createContext("Valor por defecto");

export default MiContexto;
```

En este caso, si no hay un `Provider` que envuelva al componente `ComponenteHijo`, `useContext` utilizará el valor por defecto proporcionado al crear el contexto.

El uso del contexto en React, junto con `useContext` y `createContext`, permite una forma eficiente de pasar datos a través de múltiples niveles de la jerarquía de componentes sin tener que pasar props manualmente en cada nivel.