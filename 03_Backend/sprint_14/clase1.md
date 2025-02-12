# JEST - Framework de Pruebas para JavaScript y TypeScript

[Jest](https://jestjs.io/) es un framework de pruebas desarrollado por Facebook. Es ampliamente utilizado para realizar pruebas unitarias, pruebas de integración y pruebas de extremo a extremo en proyectos de JavaScript y TypeScript. Jest se destaca por su simplicidad, velocidad y potentes capacidades de prueba.

## Características Principales

### 1. **Escribir Pruebas Sencillas**

Jest facilita la escritura de pruebas con una sintaxis clara y concisa. Puedes utilizar las funciones `test` o `it` para definir pruebas y la función `expect` para realizar afirmaciones.

Ejemplo de una prueba simple:

```javascript
test("suma 1 + 2 es igual a 3", () => {
  expect(1 + 2).toBe(3);
});
```

### 2. Matchers Poderosos

Jest incluye una variedad de "matchers" que permiten realizar afirmaciones en tus pruebas de manera intuitiva. Algunos ejemplos son `toBe`, `toEqual`, `toMatch`, `toContain`, entre otros.

Ejemplo de uso de matchers:

```javascript
test("verificar si un array contiene un elemento específico", () => {
  const miArray = ["manzana", "naranja", "banana"];
  expect(miArray).toContain("naranja");
});
```

**Matchers Comunes**:

- `toBe(valor)`: Comprueba si el valor es exactamente igual al valor esperado.
- `toEqual(valor)`: Compara estructuras de datos completas, como objetos o matrices.
- `toMatch(expresiónRegular)`: Comprueba si un string coincide con la expresión regular.
- `toContain(valor)`: Comprueba si una matriz o string contiene un elemento específico.
- `toBeNull()`, `toBeDefined()`, `toBeUndefined()`, `toBeTruthy()`, `toBeFalsy()`: Comprueban valores nulos, definidos, indefinidos, verdaderos o falsos respectivamente.

### 3. Mocks y Espías Integrados

Jest proporciona funciones integradas para crear mocks y espías. Los mocks son útiles para simular comportamientos de funciones y objetos, mientras que los espías te permiten realizar un seguimiento de las llamadas a funciones.

Ejemplo de uso de mocks y espías:

```javascript
const funcionMock = jest.fn();
funcionMock("argumento1");
expect(funcionMock).toHaveBeenCalledWith("argumento1");

const objetoEspia = jest.spyOn(objeto, "metodo");
objeto.metodo();
expect(objetoEspia).toHaveBeenCalled();
```

**Mocks**:

- Crear un Mock Funcional: `jest.fn()`
- Simular Valor de Retorno: `jest.fn().mockReturnValue(valor)`
- Contar Llamadas: `jest.fn().toHaveBeenCalledTimes(numero)`

**Espías**:

```javascript
const objeto = {
  metodoReal: () => "resultado real",
};

const espia = jest.spyOn(objeto, "metodoReal");
const resultado = objeto.metodoReal();

expect(espia).toHaveBeenCalled();
expect(resultado).toBe("resultado real");
```

### 4. Pruebas Asíncronas

Jest maneja fácilmente las pruebas asincrónicas utilizando callbacks, promesas o async/await. Puedes usar `done` con callbacks, devolver una promesa, o utilizar `async/await` para pruebas más legibles.

Ejemplo de prueba asíncrona con async/await:

```javascript
test("esperar que una promesa se resuelva correctamente", async () => {
  await expect(Promise.resolve("éxito")).resolves.toBe("éxito");
});
```

### 5. Snapshot Testing

Jest permite realizar pruebas de instantáneas que capturan el resultado actual y lo comparan con un resultado previo. Esto es útil para asegurarse de que no hayan cambios no deseados en la salida de tus componentes.

Ejemplo de snapshot testing:

```javascript
test("renderizar un componente correctamente", () => {
  const componente = renderizarComponente();
  expect(componente).toMatchSnapshot();
});
```