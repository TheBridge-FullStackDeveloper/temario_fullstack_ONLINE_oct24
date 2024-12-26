# Node.js

Node.js es un entorno de ejecución de JavaScript del lado del servidor. A diferencia de otros entornos de ejecución, Node.js utiliza un modelo de E/S no bloqueante y orientado a eventos. Esto significa que puede manejar múltiples conexiones simultáneamente sin crear un hilo para cada conexión, lo que resulta en una alta eficiencia y escalabilidad.

## Características Principales

### 1. Asincronía y Eventos

La asincronía en Node.js se basa en el manejo de eventos. Las operaciones de entrada/salida no bloqueantes permiten que el servidor continúe procesando otras tareas mientras espera que una operación de E/S se complete. Esto es esencial para aplicaciones que requieren alta concurrencia, como aplicaciones web en tiempo real.

Ejemplo Asincronía:

```javascript
const fs = require("fs");

// Lectura de un archivo de manera asincrónica
fs.readFile("archivo.txt", "utf8", (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

### 2. Módulos

Node.js utiliza un sistema de módulos que permite la modularidad y la reutilización de código. Puedes organizar tu aplicación en pequeños módulos y usarlos según sea necesario. Además, Node.js tiene un conjunto de módulos internos, y puedes crear tus propios módulos para encapsular funcionalidades específicas.

Ejemplo de módulos:

```javascript
// Módulo greet.js
module.exports = function (name) {
  return `Hola, ${name}!`;
};

// Main.js
const greet = require("./greet");

console.log(greet("Usuario"));
```

### 3. NPM (Node Package Manager)

NPM es el sistema de gestión de paquetes de Node.js. Permite instalar, compartir y gestionar dependencias de proyectos de manera sencilla. Puedes utilizar NPM para instalar bibliotecas externas, herramientas y frameworks que facilitan el desarrollo.

Ejemplo de uso:

```bash
# Instalación de una dependencia
npm install nombre-del-paquete
```

### 4. Event Loop

El event loop es una parte fundamental de Node.js. Permite manejar múltiples operaciones de manera eficiente. Las operaciones que podrían bloquear, como la lectura de archivos o las consultas a bases de datos, se gestionan de manera no bloqueante, permitiendo que el servidor siga respondiendo a otras solicitudes.