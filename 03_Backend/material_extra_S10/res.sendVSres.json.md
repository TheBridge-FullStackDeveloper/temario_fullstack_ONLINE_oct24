# res.send vs res.json en Express

La diferencia entre `.send` y `.json` en *Express.js* es sutil pero importante, y puede afectar cómo se envía la respuesta al cliente. 
- Tiene que ver en el tipo de dato que se envía y en cómo se envían los datos. 
- Además, también afecta en cómo se estable la configuración del **`Content-Type` en el encabezado**.

Vamos a desglosarlo:

### *.send()*
---
- ***Propósito:*** Envía una respuesta HTTP al cliente. Puede enviar diferentes tipos de datos, como cadenas de texto, objetos, buffers, etc.
- ***Comportamiento:***
	- Si le pasas un *objeto* o un *array*, Express automáticamente convierte el objeto a JSON y establece el **encabezado**  `Content-Type` como `application/json`.
	- Si le pasas una *cadena de texto*, Express establece el **encabezado** `Content-Type` como `text/html`.
	- Si le pasas un *buffer*,  Express establece el **encabezado** `Content-Type` como `application/octet-stream`.
- ***Flexibilidad:*** Es más genérico y puede manejar varios tipos de datos.

Ejemplo:

```js
res.send({ message: 'Hello, world!' }); // Envía JSON
res.send('Hello, world!'); // Envía texto plano
res.send(Buffer.from('Hello, world!')); // Envía un buffer
```


### *.json()*
---
- ***Propósito:*** Envía una respuesta HTTP en formato JSON al cliente.
- ***Comportamiento:***
	- Convierte automáticamente el objeto o array que le pases a una cadena JSON.
	- Siempre establece el **encabezado**  `Content-Type` como `application/json`.
- ***Especialización:*** Está diseñado específicamente para enviar respuestas JSON.

Ejemplo:

```js
res.json({ message: 'Hello, world!' }); // Envía JSON
```


### *¿Por qué en algunos casos funciona .json y no .send?*
---
Es posible que si usas `.send` con un **objeto**:
- algo en la forma en que envías los datos o en la configuración de tu servidor puede causar que el encabezado `Content-Type` no se establezca correctamente como `application/json`. Esto puede confundir al cliente (en este caso, Postman) sobre cómo interpretar la respuesta.

Al usar `.json` con un  **objeto**, te aseguras de que:
1. El encabezado `Content-Type` sea siempre `application/json`.
2. Los datos se serialicen correctamente como JSON.

### *Diferencias clave entre `.send` y `.json`*
---

| Característica            | `.send()`                                                                       | `.json()`                                     |
| ------------------------- | ------------------------------------------------------------------------------- | --------------------------------------------- |
| *Tipo de dato aceptado*   | Cualquier tipo (objetos, cadenas, buffers, etc.)                                | Solo objetos o arrays (se convierten a JSON). |
| *Encabezado Content-Type* | Depende del tipo de dato enviado (puede ser text/html, application/json, etc.). | Siempre application/json.                     |
| *Uso recomendado*         | Cuando quieres enviar cualquier tipo de dato.                                   | Cuando quieres enviar específicamente JSON.   |

### *¿Cuándo usar `.send` y cuándo usar `.json`?*
---
- Usa `.json` cuando estés seguro de que siempre enviarás una respuesta en formato JSON. Es más explícito y evita problemas con los encabezados.
- Usa `.send` cuando necesites enviar otros tipos de datos (como texto plano, HTML, o buffers) o cuando quieras más flexibilidad.


### *Ejemplo práctico*
---

#### Usando `.send`:

```javascript
app.get('/data', (req, res) => {
    const data = { message: 'Hello, world!' };
    res.send(data); // Express infiere que es JSON y establece el Content-Type automáticamente.
});
```

#### Usando `.json`:
```javascript
app.get('/data', (req, res) => {
    const data = { message: 'Hello, world!' };
    res.json(data); // Explícitamente envías JSON.
});
```

### Conclusión
---
Usa `.json` en vez de `.send` cuando envías objetos o arrays y quieres enviar específicamente un JSON. Esto asegura que la respuesta siempre sea interpretada como JSON y es especialmente útil cuando trabajas con *APIs RESTful*, donde las respuestas JSON son estándar.

---

## `Content-Type`

📌 ¿Qué es el `Content-Type` y por qué es importante configurarlo correctamente?

Esto tiene que ver con sobre cuándo utilizar `res.send` vs `res.json`.
En estos dos artículos explican conceptos importantes relacionados con `Content-Type` en `headers`:
- [Content-Type para JSON](https://www.freecodecamp.org/espanol/news/cual-es-el-content-type-correcto-para-json-explicacion-del-mime-type-del-encabezado-de-la-solicitud/)
- [Classification of Content Types](https://beeceptor.com/docs/concepts/content-type/)