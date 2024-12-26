## Creación de Servidores HTTP en Node.js

Node.js facilita la creación de servidores HTTP gracias al módulo `http` que viene incorporado. Este módulo permite configurar y gestionar un servidor HTTP de manera sencilla.

### Ejemplo

```javascript
const http = require("http");

// Crear un servidor HTTP simple
const server = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("¡Hola, mundo!\n");
});

// Escuchar en el puerto 3000
const PORT = 3000;
server.listen(PORT, () => {
  console.log(`Servidor HTTP corriendo en http://localhost:${PORT}/`);
});
```

El código crea un servidor HTTP básico utilizando http.createServer. La función callback toma dos parámetros, req y res, que representan la solicitud del cliente y la respuesta del servidor, respectivamente.

## Manejo de Rutas y Métodos HTTP

El manejo de rutas y métodos HTTP es esencial para construir aplicaciones web robustas.

### Ejemplo

Vamos a explicar por partes el siguiente ejemplo:

```javascript
const http = require("http");

// Crear un servidor HTTP
const server = http.createServer((req, res) => {
  const url = req.url;
  const method = req.method;

  if (url === "/" && method === "GET") {
    res.writeHead(200, { "Content-Type": "text/plain" });
    res.end("¡Bienvenido a la página principal!");
  } else if (url === "/saludo" && method === "GET") {
    res.writeHead(200, { "Content-Type": "text/plain" });
    res.end("¡Hola, visitante!");
  } else {
    res.writeHead(404, { "Content-Type": "text/plain" });
    res.end("Ruta no encontrada");
  }
});

// Escuchar en el puerto 3000
const PORT = 3000;
server.listen(PORT, () => {
  console.log(`Servidor HTTP corriendo en http://localhost:${PORT}/`);
});
```

### 1.

```javascript
const url = req.url; // Obtener la URL de la solicitud
const method = req.method; // Obtener el método HTTP de la solicitud
```

Las líneas anteriores extraen la URL y el método de la solicitud, lo que permite al servidor tomar decisiones basadas en estos valores.

### 2.

```javascript
if (url === "/" && method === "GET") {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("¡Bienvenido a la página principal!");
} else if (url === "/saludo" && method === "GET") {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("¡Hola, visitante!");
} else {
  res.writeHead(404, { "Content-Type": "text/plain" });
  res.end("Ruta no encontrada");
}
```

En este bloque condicional, se evalúan diferentes rutas y métodos. Si la ruta es / y el método es GET, se envía una respuesta de bienvenida. Si la ruta es /saludo y el método es GET, se envía un saludo. De lo contrario, se responde con un código de estado 404 y un mensaje indicando que la ruta no fue encontrada.

### 3.

```javascript
res.writeHead(statusCode, { "Content-Type": "text/plain" });
res.end("Mensaje de respuesta");
```

El código utiliza res.writeHead para establecer el código de estado y los encabezados de la respuesta. Luego, res.end envía el contenido de la respuesta al cliente.