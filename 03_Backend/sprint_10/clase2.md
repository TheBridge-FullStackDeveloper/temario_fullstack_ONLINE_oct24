# Middlewares en Express.js

En Express.js, los middlewares son funciones que tienen acceso al objeto de solicitud (`req`), al objeto de respuesta (`res`), y a la siguiente función de middleware en el ciclo de solicitud-respuesta de la aplicación. Estos middlewares pueden realizar diversas tareas, como modificar la solicitud o respuesta, realizar validaciones, autenticar usuarios, y más.

## Uso Básico de Middlewares

En Express, puedes usar middlewares con la función `use`. Aquí hay un ejemplo básico:

```javascript
const express = require("express");
const app = express();

// Middleware de registro de tiempo
app.use((req, res, next) => {
  console.log(`Time: ${Date.now()}`);
  next(); // Llama a la siguiente función de middleware
});

// Ruta principal
app.get("/", (req, res) => {
  res.send("Hola, mundo!");
});

const puerto = 3000;
app.listen(puerto, () => {
  console.log(`Servidor escuchando en el puerto ${puerto}`);
});
```

En este ejemplo, el middleware de registro de tiempo se ejecutará antes de cada solicitud, mostrando la hora actual en la consola.

## Tipos Comunes de Middlewares

### Middleware de Análisis de Cuerpo (Body Parser)

El middleware de análisis de cuerpo permite procesar el cuerpo de la solicitud, especialmente útil para formularios y solicitudes POST. Puedes instalar el middleware `body-parser` para esto.

```javascript
const express = require("express");
const bodyParser = require("body-parser");
const app = express();

// Middleware de análisis de cuerpo
app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

// Ruta para manejar datos POST
app.post("/ejemplo", (req, res) => {
  const datos = req.body;
  res.json({ mensaje: "Datos recibidos correctamente", datos });
});

const puerto = 3000;
app.listen(puerto, () => {
  console.log(`Servidor escuchando en el puerto ${puerto}`);
});
```

### Middleware de Autenticación

Los middlewares de autenticación verifican si un usuario tiene permisos para acceder a ciertas rutas. Aquí hay un ejemplo simple:

```javascript
const express = require("express");
const app = express();

// Middleware de autenticación
const middlewareAutenticacion = (req, res, next) => {
  const usuarioAutenticado = false; // Lógica de autenticación

  if (usuarioAutenticado) {
    next(); // Usuario autenticado, permite el acceso
  } else {
    res.status(401).send("Acceso no autorizado");
  }
};

// Ruta protegida con el middleware de autenticación
app.get("/ruta-protegida", middlewareAutenticacion, (req, res) => {
  res.send("Bienvenido a la ruta protegida");
});

const puerto = 3000;
app.listen(puerto, () => {
  console.log(`Servidor escuchando en el puerto ${puerto}`);
});
```