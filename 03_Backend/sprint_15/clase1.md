# DOCUMENTACIÓN y DEPLOY 

1. DOCUMENTAFCIÓN con Swagger y Swagger UI
2. DEPLOY con Render

# 1. DOCUMENTAFCIÓN con Swagger y Swagger UI

## Descripción

Swagger es una herramienta de código abierto utilizada para diseñar, construir y documentar servicios web RESTful. Proporciona soporte para la especificación de OpenAPI, un estándar de la industria para describir APIs RESTful. Swagger UI es una herramienta complementaria que genera una interfaz de usuario interactiva a partir de la descripción de tu API, permitiendo a los desarrolladores explorar y probar la API directamente desde su navegador.

## Uso de Swagger y Swagger UI

### Configuración de Swagger

Configura Swagger para que pueda leer la descripción de tu API. Crea un objeto de opciones con información como la definición de la API y la ubicación de los archivos que contienen la descripción de la API.

```javascript
const swaggerJSDoc = require("swagger-jsdoc");

const swaggerDefinition = {
  info: {
    title: "Mi API",
    version: "1.0.0",
    description: "Descripción de mi API",
  },
  host: "localhost:3000",
  basePath: "/",
};

const options = {
  swaggerDefinition,
  apis: ["./routes/*.js"], // Ruta a los archivos que contienen la documentación de la API
};

const swaggerSpec = swaggerJSDoc(options);
```

### Documentación de la API

Utiliza comentarios en el código para documentar la API. Estos comentarios deben seguir un formato específico para que Swagger pueda leerlos. Ejemplo:

```javascript
/**
 * @swagger
 * /users:
 *   get:
 *     tags:
 *       - Users
 *     description: Returns all users
 *     produces:
 *       - application/json
 *     responses:
 *       200:
 *         description: An array of users
 */
router.get("/users", (req, res) => {
  // ...
});
```

### Generación de la documentación

Una vez documentada la API, genera la documentación con Swagger utilizando la función `swaggerJSDoc` con el objeto de opciones creado anteriormente.

### Servir Swagger UI

Finalmente, sirve Swagger UI en tu aplicación utilizando el middleware `swagger-ui-express` y la documentación generada por Swagger. Por defecto, Swagger UI se sirve en la ruta `/api-docs`.

```javascript
const swaggerUi = require("swagger-ui-express");

app.use("/api-docs", swaggerUi.serve, swaggerUi.setup(swaggerSpec));
```
<br>


# 2. DEPLOY con Render

Resumen paso a paso para hacer un **deploy en Render** de un backend alojado en GitHu.

---

### **1. Preparar el repositorio en GitHub**
- Asegúrate de que tu proyecto de backend esté correctamente alojado en GitHub.
- Verifica que el archivo `.env` esté incluido en el `.gitignore` para que no se suba al repositorio.
- Asegúrate de que el proyecto tenga un archivo de configuración para el servidor (por ejemplo, `index.js` o `server.js`) y un `package.json` con los scripts necesarios (como `start` y `build` si es necesario).

---

### **2. Crear una cuenta en Render**
- Si no tienes una cuenta en Render, regístrate en [https://render.com/](https://render.com/).
- Render ofrece un plan gratuito con límites, pero suficiente para proyectos pequeños.

---

### **3. Crear un nuevo servicio en Render**
1. En el panel de Render, haz clic en **New** y selecciona **Web Service**.
2. Conecta tu cuenta de GitHub y selecciona el repositorio donde está alojado tu backend.
3. Render detectará automáticamente el proyecto y te pedirá configurar el servicio.

---

### **4. Configurar el servicio**
1. **Nombre del servicio**: Asigna un nombre descriptivo.
2. **Rama**: Selecciona la rama de GitHub que deseas usar para el deploy (por ejemplo, `main` o `master`).
3. **Comando de inicio**: Define el comando para iniciar tu servidor. Por ejemplo:
   - Si usas Node.js: `npm start` o `node index.js`.
   - Si usas un script personalizado, asegúrate de que esté definido en `package.json`.
4. **Puerto**: Define el puerto en el que tu aplicación escucha. Por ejemplo, `3000` o `8080`. Render usa la variable de entorno `PORT` para asignar un puerto dinámico, así que asegúrate de que tu servidor use `process.env.PORT`.

---

### **5. Añadir variables de entorno**
- Como el archivo `.env` no se sube a GitHub, debes agregar manualmente las variables de entorno en Render:
  1. En la configuración del servicio, ve a la sección **Environment Variables**.
  2. Añade cada variable que esté en tu `.env` (por ejemplo, `DATABASE_URL`, `JWT_SECRET`, etc.).
  3. Si usas `dotenv` en tu proyecto, Render lo manejará automáticamente siempre que las variables estén definidas en su panel.

---

### **6. Configurar la dirección IP**
- Si tu backend necesita conectarse a servicios externos (como una base de datos), asegúrate de que la dirección IP de Render esté permitida en las configuraciones de seguridad de esos servicios.
- Render no tiene una IP fija, pero puedes usar un **servicio de IP estática** o configurar reglas de firewall para permitir todas las IPs (no recomendado para producción).

---

### **7. Desplegar el servicio**
- Una vez configurado todo, haz clic en **Create Web Service**.
- Render comenzará a desplegar tu aplicación. Esto puede tardar unos minutos.
- Durante el despliegue, Render instalará las dependencias (`npm install`) y ejecutará el comando de inicio que definiste.

---

### **8. Verificar el despliegue**
- Una vez completado el despliegue, Render te proporcionará una URL pública para acceder a tu backend (por ejemplo, `https://tu-servicio.onrender.com`).
- Verifica que tu aplicación esté funcionando correctamente accediendo a la URL.
- Si hay errores, revisa los logs en el panel de Render para identificar el problema.

---

### **9. Configuraciones adicionales**
- **Dominio personalizado**: Si quieres usar un dominio propio, puedes configurarlo en la sección **Custom Domains**.
- **Escalado automático**: Render permite escalar automáticamente tu servicio si recibes mucho tráfico.
- **Monitoreo**: Usa la sección de logs y métricas de Render para monitorear el rendimiento de tu aplicación.

---

### **10. Actualizaciones futuras**
- Cada vez que hagas un cambio en tu repositorio de GitHub, Render detectará automáticamente los cambios y desplegará una nueva versión.
- Si necesitas cambiar las variables de entorno, puedes actualizarlas en el panel de Render y reiniciar el servicio.

---

### **Resumen de puntos clave**
1. **Variables de entorno**: Añádelas manualmente en el panel de Render.
2. **Puerto**: Usa `process.env.PORT` en tu código para que Render asigne el puerto correcto.
3. **Dirección IP**: Si es necesario, configura los servicios externos para permitir la IP de Render.
4. **Logs**: Revisa los logs en Render para depurar errores.
5. **Automatización**: Render se integra con GitHub para desplegar automáticamente los cambios.

¡Y eso es todo! Con estos pasos, tu backend estará desplegado en Render y listo para usarse. 😊