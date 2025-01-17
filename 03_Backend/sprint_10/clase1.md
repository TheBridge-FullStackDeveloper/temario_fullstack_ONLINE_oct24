# Express.js

## ¿Qué es Express.js?

Express.js es un marco de aplicación web para Node.js, diseñado para simplificar el desarrollo de aplicaciones web y APIs. Es minimalista y flexible, proporcionando una serie de funciones y herramientas para construir aplicaciones web de manera rápida y sencilla.

## Características Principales

### 1. **Manejo de Rutas:**

Express facilita la definición de rutas para manejar diversas solicitudes HTTP. Puedes responder a solicitudes GET, POST, PUT, DELETE y más.

```javascript
const express = require("express");
const app = express();

// Ruta básica
app.get("/", (req, res) => {
  res.send("Hola, mundo!");
});

// Ruta con parámetros
app.get("/usuario/:id", (req, res) => {
  const userId = req.params.id;
  res.send(`Detalles del usuario ${userId}`);
});
```

### 2. Middlewares:

Express utiliza middlewares para procesar solicitudes antes de llegar a las rutas definidas. Pueden realizar tareas como el análisis de cuerpos de solicitud, autenticación, manejo de errores, etc.

```javascript
const express = require("express");
const app = express();

// Middleware de registro de tiempo
app.use((req, res, next) => {
  console.log(`Time: ${Date.now()}`);
  next();
});

// Middleware de análisis de cuerpo
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Middleware de autenticación
app.use((req, res, next) => {
  // Lógica de autenticación
  next();
});
```

### 3. Plantillas de Vistas:

Express es compatible con varios motores de plantillas (pug, ejs, handlebars, etc.), permitiendo la generación dinámica de HTML.

```javascript
app.set("view engine", "pug");

app.get("/vista", (req, res) => {
  res.render("mi_vista", { titulo: "Express.js" });
});
```

### 4. Enrutamiento Modular:

Express permite organizar el código de las rutas en módulos independientes, facilitando la gestión de rutas en aplicaciones grandes.

```javascript
// routes/usuarios.js
const express = require("express");
const router = express.Router();

router.get("/", (req, res) => {
  res.send("Lista de usuarios");
});

module.exports = router;

// index.js
const express = require("express");
const usuariosRouter = require("./routes/usuarios");

const app = express();
app.use("/usuarios", usuariosRouter);
```

### 5. Manejo de Archivos Estáticos:

Express puede servir archivos estáticos, como CSS, imágenes y JavaScript, de manera eficiente.

```javascript
app.use(express.static("public"));
```

## Instalación y Configuración

Para empezar con Express.js, primero debes instalarlo utilizando npm:

```bash
npm install express
```

Luego, puedes crear una aplicación básica de Express:

```javascript
const express = require("express");
const app = express();

const puerto = 3000;
app.listen(puerto, () => {
  console.log(`Servidor escuchando en el puerto ${puerto}`);
});
```