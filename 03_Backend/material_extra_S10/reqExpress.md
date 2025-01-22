# 02 req en Express

### **`req.params`**

- **Se utiliza para capturar parámetros definidos en la URL**.
- **Los valores se obtienen de las partes dinámicas de la ruta** (las que tienen `:` en el path).

**Ejemplo:** Ruta configurada en Express:

```javascript
app.get('/users/:id', (req, res) => {
  const userId = req.params.id; // Captura el valor de "id" en la URL
  res.send(`El ID del usuario es: ${userId}`);
});
```

Llamada a la ruta:

```
http://localhost:3000/users/42
```

Respuesta:

```
El ID del usuario es: 42
```

**Resumen:**

- `req.params` obtiene valores como `id` (en este caso, `42`) de la **estructura** de la URL.
- Muy útil para rutas dinámicas.

---

### **`req.query`**

- **Se utiliza para capturar los parámetros enviados en la URL como parte de una consulta**.
- **Los valores se obtienen después del signo `?` en la URL**.

**Ejemplo:** Ruta configurada en Express:

```javascript
app.get('/search', (req, res) => {
  const keyword = req.query.keyword; // Captura el valor de "keyword" en la query string
  res.send(`Buscando: ${keyword}`);
});
```

Llamada a la ruta:

```
http://localhost:3000/search?keyword=nutria
```

Respuesta:

```
Buscando: nutria
```

**Resumen:**

- `req.query` obtiene valores como `keyword` (en este caso, `nutria`) de la **cadena de consulta**.
- Muy útil para filtros o búsqueda.

---

### **Diferencias clave:**

|Aspecto|`req.params`|`req.query`|
|---|---|---|
|**Dónde aparece**|En la ruta (URL dinámica: `/ruta/:param`)|Después del `?` en la URL|
|**Propósito**|Identificar recursos únicos (IDs)|Enviar filtros o datos adicionales|
|**Forma de acceso**|`req.params.nombreParametro`|`req.query.nombreParametro`|

---

### **Ejemplo combinado:**

Supongamos esta ruta:

```javascript
app.get('/products/:id', (req, res) => {
  const productId = req.params.id; // ID dinámico de la URL
  const category = req.query.category; // Categoría como query string
  res.send(`Producto: ${productId}, Categoría: ${category}`);
});
```

Llamada:

```
http://localhost:3000/products/123?category=ropa
```

Respuesta:

```
Producto: 123, Categoría: ropa
```

---

**Regla para recordar:**

- Si la **estructura** de la ruta necesita valores únicos, usa `req.params`.
- Si solo necesitas **datos extra** (como filtros), usa `req.query`. 😊

---

## Otros tipos de `req` que puedes encontrar, junto con ejemplos básicos.

---

### **`req.body`**

- **Se utiliza para capturar datos enviados en el cuerpo de la solicitud**.
- Es comúnmente usado con métodos como `POST`, `PUT` o `PATCH`.
- Necesita un **middleware** como `express.json()` o `express.urlencoded()` para leer el cuerpo correctamente.

**Ejemplo:** Configuración en Express:

```javascript
const express = require('express');
const app = express();

app.use(express.json()); // Necesario para leer JSON en el cuerpo

app.post('/login', (req, res) => {
  const { username, password } = req.body; // Captura datos enviados en el cuerpo
  res.send(`Usuario: ${username}, Contraseña: ${password}`);
});
```

Solicitud enviada con el cuerpo:

```json
{
  "username": "usuario1",
  "password": "12345"
}
```

Respuesta:

```
Usuario: usuario1, Contraseña: 12345
```

---

### Comparativa: **`req.query`, `req.params`, `req.body`**

|**Uso**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`req.query`**|Parámetros después de `?` en la URL|`/search?keyword=nutria`|
|**`req.params`**|Parte dinámica de la ruta|`/users/:id` (`/users/42`)|
|**`req.body`**|Datos enviados en el cuerpo|`{ "username": "usuario1" }`|

---

### **Otros tipos comunes de `req` en Express**

#### 1. **`req.headers`**

- Contiene los encabezados de la solicitud HTTP.
    
- Ejemplo:
    
    ```javascript
    app.get('/headers', (req, res) => {
      res.send(req.headers); // Muestra todos los encabezados enviados
    });
    ```
    
    Llamada con un encabezado personalizado:
    
    ```
    curl -H "X-Custom-Header: valor" http://localhost:3000/headers
    ```
    
    Respuesta:
    
    ```json
    {
      "x-custom-header": "valor",
      "user-agent": "...",
      ...
    }
    ```
    

---

#### 2. **`req.cookies`**

- Contiene cookies enviadas por el cliente (requiere el middleware `cookie-parser`).
- Ejemplo:
    
    ```javascript
    const cookieParser = require('cookie-parser');
    app.use(cookieParser());
    
    app.get('/cookies', (req, res) => {
      res.send(req.cookies); // Devuelve las cookies enviadas
    });
    ```
    

---

#### 3. **`req.ip`**

- Devuelve la dirección IP del cliente.
- Ejemplo:
    
    ```javascript
    app.get('/ip', (req, res) => {
      res.send(`Tu IP es: ${req.ip}`);
    });
    ```
    

---

#### 4. **`req.method`**

- Devuelve el método HTTP utilizado (GET, POST, PUT, etc.).
- Ejemplo:
    
    ```javascript
    app.use((req, res) => {
      res.send(`Método utilizado: ${req.method}`);
    });
    ```
    

---

#### 5. **`req.url`**

- Devuelve la URL solicitada (sin el dominio).
- Ejemplo:
    
    ```javascript
    app.use((req, res) => {
      res.send(`URL solicitada: ${req.url}`);
    });
    ```
    

---

#### 6. **`req.protocol`**

- Devuelve el protocolo utilizado (`http` o `https`).
- Ejemplo:
    
    ```javascript
    app.get('/protocol', (req, res) => {
      res.send(`Protocolo: ${req.protocol}`);
    });
    ```
    

---

### **Resumen de los `req` más comunes**

|**Propiedad**|**Descripción**|**Ejemplo de uso**|
|---|---|---|
|`req.query`|Parámetros en la query string|`/search?keyword=nutria`|
|`req.params`|Valores dinámicos en la ruta|`/users/:id` (`/users/42`)|
|`req.body`|Datos enviados en el cuerpo de la solicitud|`{ "username": "usuario1" }`|
|`req.headers`|Encabezados enviados por el cliente|`Authorization: Bearer token`|
|`req.cookies`|Cookies enviadas por el cliente (requiere middleware)|`{ "sessionId": "abc123" }`|
|`req.ip`|Dirección IP del cliente|`192.168.0.1`|
|`req.method`|Método HTTP de la solicitud|`GET`, `POST`, etc.|
|`req.url`|URL solicitada|`/products/123?category=ropa`|
|`req.protocol`|Protocolo utilizado (`http` o `https`)|`http`|

Aquí tienes un ejemplo práctico donde combinamos varios tipos de `req` en una aplicación Express. Este ejemplo muestra cómo trabajar con **`req.query`**, **`req.params`**, **`req.body`**, **`req.headers`**, y más.
### **Ejemplo práctico**

Supongamos que tienes una API para manejar un catálogo de productos. Queremos implementar lo siguiente:

1. Buscar productos con filtros opcionales (`req.query`).
2. Obtener detalles de un producto específico (`req.params`).
3. Crear un producto nuevo (`req.body`).
4. Mostrar información adicional del cliente, como su IP y encabezados (`req.ip`, `req.headers`).

---

#### Código:

```javascript
const express = require('express');
const app = express();

// Middleware para leer JSON del cuerpo
app.use(express.json());

// 1. Buscar productos (usando req.query)
app.get('/products', (req, res) => {
  const { category, minPrice, maxPrice } = req.query;
  res.send({
    message: 'Buscando productos',
    filtros: {
      category: category || 'Ninguna categoría',
      minPrice: minPrice || 'Sin mínimo',
      maxPrice: maxPrice || 'Sin máximo',
    },
  });
});

// 2. Obtener detalles de un producto (usando req.params)
app.get('/products/:id', (req, res) => {
  const { id } = req.params;
  res.send({
    message: 'Detalles del producto',
    productId: id,
  });
});

// 3. Crear un producto nuevo (usando req.body)
app.post('/products', (req, res) => {
  const { name, price, category } = req.body;
  res.send({
    message: 'Producto creado exitosamente',
    producto: {
      name,
      price,
      category,
    },
  });
});

// 4. Mostrar información adicional del cliente
app.get('/info', (req, res) => {
  res.send({
    ip: req.ip,
    metodo: req.method,
    url: req.url,
    headers: req.headers,
  });
});

// Iniciar servidor
app.listen(3000, () => {
  console.log('Servidor corriendo en http://localhost:3000');
});
```

---

### **Pruebas:**

1. **Buscar productos con filtros:** URL: `http://localhost:3000/products?category=ropa&minPrice=50&maxPrice=200`  
    Respuesta:
    
    ```json
    {
      "message": "Buscando productos",
      "filtros": {
        "category": "ropa",
        "minPrice": "50",
        "maxPrice": "200"
      }
    }
    ```
    
2. **Obtener detalles de un producto específico:** URL: `http://localhost:3000/products/123`  
    Respuesta:
    
    ```json
    {
      "message": "Detalles del producto",
      "productId": "123"
    }
    ```
    
3. **Crear un producto nuevo:** Solicitud:
    
    ```
    POST http://localhost:3000/products
    Content-Type: application/json
    
    {
      "name": "Camiseta",
      "price": 100,
      "category": "ropa"
    }
    ```
    
    Respuesta:
    
    ```json
    {
      "message": "Producto creado exitosamente",
      "producto": {
        "name": "Camiseta",
        "price": 100,
        "category": "ropa"
      }
    }
    ```
    
4. **Información del cliente:** URL: `http://localhost:3000/info`  
    Respuesta:
    
    ```json
    {
      "ip": "::1",
      "metodo": "GET",
      "url": "/info",
      "headers": {
        "host": "localhost:3000",
        "user-agent": "...",
        "accept": "*/*",
        ...
      }
    }
    ```
    

---

### **Explicación:**

1. **`req.query`:** Extrae los filtros opcionales (categoría y rango de precio) para buscar productos.
2. **`req.params`:** Obtiene el `id` del producto directamente desde la URL.
3. **`req.body`:** Captura los datos del nuevo producto enviados en el cuerpo de la solicitud.
4. **`req.ip`, `req.headers`:** Proporcionan información del cliente que realiza la solicitud.

