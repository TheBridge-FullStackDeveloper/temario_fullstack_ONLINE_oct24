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

---

# SUPERTEST 
### librería de JavaScript diseñada para facilitar la prueba de APIs HTTP


**Supertest** es una librería de JavaScript diseñada para facilitar la prueba de APIs HTTP, especialmente en aplicaciones construidas con **Node.js** y **Express**. 

Proporciona una interfaz sencilla y fluida para realizar solicitudes HTTP (como GET, POST, PUT, DELETE, etc.) y verificar las respuestas, incluyendo el código de estado, cabeceras y cuerpo de la respuesta.

### ¿Por qué usar Supertest?
- **Facilita las pruebas**: Permite escribir pruebas de integración de manera sencilla.
- **Integración con Mocha/Jest**: Funciona bien con frameworks de testing como Mocha o Jest.
- **Simula solicitudes HTTP**: No necesitas levantar un servidor real para probar tus endpoints.

### Instalación
Para usar Supertest, primero debes instalarlo junto con un framework de testing como Mocha o Jest:

```bash
npm install supertest mocha --save-dev
```

### Uso básico con Node.js, Express y Mocha

1. **Crear una aplicación Express**:
   Supongamos que tienes una aplicación Express simple:

   ```javascript
   // app.js
   const express = require('express');
   const app = express();

   app.get('/api/greet', (req, res) => {
     res.json({ message: 'Hola, mundo!' });
   });

   module.exports = app;
   ```

2. **Escribir una prueba con Supertest**:
   Crea un archivo de prueba (por ejemplo, `test/app.test.js`):

   ```javascript
   const request = require('supertest');
   const app = require('../app'); // Importa tu aplicación Express

   describe('GET /api/greet', () => {
     it('debe responder con un mensaje de saludo', (done) => {
       request(app)
         .get('/api/greet') // Realiza una solicitud GET al endpoint
         .expect(200) // Espera un código de estado 200
         .expect('Content-Type', /json/) // Espera un contenido tipo JSON
         .end((err, res) => {
           if (err) return done(err); // Si hay un error, termina la prueba
           // Verifica el cuerpo de la respuesta
           if (res.body.message !== 'Hola, mundo!') {
             return done(new Error('El mensaje no coincide'));
           }
           done(); // Finaliza la prueba
         });
     });
   });
   ```

3. **Ejecutar las pruebas**:
   Usa Mocha para ejecutar las pruebas:

   ```bash
   npx mocha test/app.test.js
   ```


### Ejemplo con Jest
Si prefieres usar Jest en lugar de Mocha, el proceso es similar:

1. Instala Jest:
   ```bash
   npm install jest --save-dev
   ```

2. Escribe la prueba con Jest:
   ```javascript
   const request = require('supertest');
   const app = require('../app');

   describe('GET /api/greet', () => {
     it('debe responder con un mensaje de saludo', async () => {
       const response = await request(app)
         .get('/api/greet')
         .expect(200)
         .expect('Content-Type', /json/);

       expect(response.body.message).toBe('Hola, mundo!');
     });
   });
   ```

3. Ejecuta las pruebas con Jest:
   ```bash
   npx jest
   ```

### Ventajas de Supertest
- **Fácil de usar**: La sintaxis es intuitiva y fluida.
- **No requiere un servidor en ejecución**: Simula las solicitudes HTTP sin necesidad de levantar un servidor real.
- **Integración con frameworks de testing**: Funciona bien con Mocha, Jest, y otros.

