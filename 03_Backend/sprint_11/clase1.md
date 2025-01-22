# API REST con Express.js

## Introducción a las API REST

Las API REST (Representational State Transfer) son un estilo arquitectónico para diseñar sistemas distribuidos y se han vuelto fundamentales en el desarrollo de aplicaciones web y servicios. Utilizan los métodos HTTP (GET, POST, PUT, DELETE) para realizar operaciones en recursos, generalmente representados en formato JSON o XML.

## Creación de una API REST con Express.js

Express.js es una excelente opción para construir API REST debido a su sencillez y flexibilidad. Aquí hay una guía paso a paso para crear una API REST básica con Express.js:

### 1. Instalación de Express

Primero, instala Express utilizando npm:

```bash
npm install express
```

### 2. Configuración Inicial

Crea un archivo app.js y configura tu aplicación Express:

```javascript
const express = require("express");
const app = express();
const puerto = 3000;

app.listen(puerto, () => {
  console.log(`Servidor escuchando en el puerto ${puerto}`);
});
```

### 3. Definición de Rutas y Métodos

Define las rutas de tu API y los métodos asociados:

```javascript
// Ruta principal
app.get("/", (req, res) => {
  res.send("Bienvenido a la API REST");
});

// Obtener todos los recursos
app.get("/api/recursos", (req, res) => {
  // Lógica para obtener y devolver todos los recursos
});

// Obtener un recurso por ID
app.get("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  // Lógica para obtener y devolver un recurso por ID
});

// Crear un nuevo recurso
app.post("/api/recursos", (req, res) => {
  // Lógica para crear un nuevo recurso
});

// Actualizar un recurso por ID
app.put("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  // Lógica para actualizar un recurso por ID
});

// Eliminar un recurso por ID
app.delete("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  // Lógica para eliminar un recurso por ID
});
```

### 4. Implementación de la Lógica de Negocio

Agrega la lógica necesaria para cada ruta y método. Puedes interactuar con una base de datos, procesar datos, y responder con resultados.

### 5. Pruebas de la API

Utiliza herramientas como Postman o cURL para realizar pruebas en tu API REST. Verifica que cada ruta y método funcionen correctamente.

## Principios Clave de una API REST

### 1. Recursos:

Las API REST se centran en los recursos, que son entidades o datos que pueden ser accedidos o manipulados mediante las rutas y métodos.

### 2. URI (Identificadores de Recursos Uniformes):

Cada recurso debe tener una URI única que lo identifica. Las rutas en Express representan estas URIs.

### 3. Métodos HTTP:

Las operaciones en los recursos se realizan a través de los métodos HTTP estándar: GET (obtener), POST (crear), PUT (actualizar) y DELETE (eliminar).

### 4. Estado (Stateless):

Las solicitudes deben contener toda la información necesaria para entender y procesar la solicitud. La API no debe depender del estado almacenado en el servidor.

### 5. Representación:

Los recursos se representan típicamente en formato JSON o XML. Los clientes pueden solicitar o enviar datos en estos formatos.

## CRUD: Crear, Leer, Actualizar y Eliminar

CRUD es un acrónimo que representa las cuatro operaciones básicas en la manipulación de datos. Estas operaciones son fundamentales en cualquier sistema que gestione información.

1. Crear (Create):

- Objetivo: Crear un nuevo registro o entidad en la base de datos.
- Método HTTP: `POST`
- Ejemplo en Express.js:

```javascript
app.post("/api/recursos", (req, res) => {
  // Lógica para crear un nuevo recurso
});
```

2. Leer (Read):

- Objetivo: Obtener información o datos de un registro o de varios registros.
- Método HTTP: `GET`
- Ejemplo en Express.js:

```javascript
// Obtener todos los recursos
app.get("/api/recursos", (req, res) => {
  // Lógica para obtener y devolver todos los recursos
});

// Obtener un recurso por ID
app.get("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  // Lógica para obtener y devolver un recurso por ID
});
```

3. Actualizar (Update):

- Objetivo: Modificar la información de un registro existente en la base de datos.
- Método HTTP: `PUT` o `PATCH`
- Ejemplo en Express.js:

```javascript
app.put("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  // Lógica para actualizar un recurso por ID
});
```

4. Eliminar (Delete):

- Objetivo: Eliminar un registro o entidad de la base de datos.
- Método HTTP: `DELETE`
- Ejemplo en Express.js:

```javascript
app.delete("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  // Lógica para eliminar un recurso por ID
});
```

## Ejemplo Completo de CRUD

```javascript
const express = require("express");
const app = express();
const puerto = 3000;

// Middleware para analizar el cuerpo de las solicitudes como JSON
app.use(express.json());

// Simulación de una base de datos (en la memoria)
let recursos = [];

// CREATE
app.post("/api/recursos", (req, res) => {
  const nuevoRecurso = req.body;
  recursos.push(nuevoRecurso);
  res.json({ mensaje: "Recurso creado con éxito", recurso: nuevoRecurso });
});

// READ
app.get("/api/recursos", (req, res) => {
  res.json(recursos);
});

app.get("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  const recurso = recursos.find((r) => r.id === resourceId);
  if (!recurso) {
    res.status(404).json({ mensaje: "Recurso no encontrado" });
  } else {
    res.json(recurso);
  }
});

// UPDATE
app.put("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  const indice = recursos.findIndex((r) => r.id === resourceId);
  if (indice === -1) {
    res.status(404).json({ mensaje: "Recurso no encontrado" });
  } else {
    recursos[indice] = req.body;
    res.json({
      mensaje: "Recurso actualizado con éxito",
      recurso: recursos[indice],
    });
  }
});

// DELETE
app.delete("/api/recursos/:id", (req, res) => {
  const resourceId = req.params.id;
  recursos = recursos.filter((r) => r.id !== resourceId);
  res.json({ mensaje: "Recurso eliminado con éxito" });
});

app.listen(puerto, () => {
  console.log(`Servidor escuchando en el puerto ${puerto}`);
});
```