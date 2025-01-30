# CORS (Cross-Origin Resource Sharing)

## Introducción

El Cross-Origin Resource Sharing (CORS) es un mecanismo de seguridad implementado en los navegadores web para restringir las solicitudes de recursos (como scripts, estilos y datos) que un dominio web puede realizar hacia otro dominio diferente al suyo. Esta política de seguridad es crucial para prevenir ataques de scripts entre sitios, conocidos como XSS (Cross-Site Scripting).

Cuando un cliente (navegador) realiza una solicitud HTTP a un servidor, el servidor puede responder con una política CORS que indica si la solicitud debería ser permitida o denegada. La implementación de CORS permite a los servidores controlar qué dominios tienen permiso para acceder a sus recursos y qué métodos HTTP están permitidos.

## Principales Conceptos

1. **Orígenes (Origins):**
   Un origen es una combinación de protocolo (http o https), dominio y puerto. Por ejemplo, https://www.ejemplo.com y http://api.ejemplo.com son orígenes diferentes. CORS se basa en la definición de orígenes para gestionar las solicitudes entre ellos.

2. **Política Same-Origin:**
   La política Same-Origin es la regla predeterminada que impide que un script en una página web realice solicitudes a un dominio diferente al de la propia página. CORS relaja esta política, permitiendo que los recursos se soliciten desde orígenes diferentes bajo ciertas condiciones.

3. **Cabeceras CORS:**
   Las cabeceras CORS son utilizadas tanto en la solicitud como en la respuesta HTTP para informar al navegador sobre las políticas de acceso. Algunas de las cabeceras más importantes incluyen:
   - **Origin:** En la solicitud, indica el origen del cual proviene la solicitud. En la respuesta, especifica el origen que tiene permiso para acceder a los recursos.
   - **Access-Control-Allow-Origin:** En la respuesta, indica qué orígenes tienen permiso para acceder a los recursos. Puede ser un origen específico, "\*", o una lista de orígenes permitidos.
   - **Access-Control-Allow-Methods:** Especifica los métodos HTTP permitidos cuando se accede al recurso. Por ejemplo, "GET", "POST", "PUT", etc.
   - **Access-Control-Allow-Headers:** Indica qué cabeceras HTTP personalizadas pueden ser usadas durante la solicitud actual.
   - **Access-Control-Allow-Credentials:** Indica si la solicitud puede incluir credenciales (como cookies o encabezados HTTP de autorización).

## Ejemplos Prácticos

1. **Configuración Básica en un Servidor Node.js con Express:**
   Supongamos que tienes un servidor Node.js con Express y deseas habilitar CORS. Puedes hacerlo instalando el paquete `cors` y usándolo como middleware:

```javascript
const express = require("express");
const cors = require("cors");

const app = express();

// Habilitar CORS para todos los orígenes
app.use(cors());

// ... Resto de la configuración del servidor
```

2. **Configurar CORS de manera personalizada en un servidor Node.js con Express:**

```javascript
const express = require("express");
const app = express();

// Middleware para habilitar CORS
app.use((req, res, next) => {
  // Configuración de cabeceras CORS
  res.header("Access-Control-Allow-Origin", "https://miotrodominio.com");
  res.header("Access-Control-Allow-Methods", "GET, POST, OPTIONS");
  res.header("Access-Control-Allow-Headers", "Content-Type");

  // Permite que el navegador envíe la solicitud con estos métodos
  res.header("Access-Control-Allow-Methods", "GET, POST, OPTIONS");

  // Permite que el navegador incluya las credenciales (cookies, tokens, etc.)
  res.header("Access-Control-Allow-Credentials", true);

  // Continúa con el siguiente middleware o enrutador
  next();
});

// Rutas y lógica de la aplicación aquí

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Servidor Express corriendo en http://localhost:${PORT}/`);
});
```