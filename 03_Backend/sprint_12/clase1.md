# Auth0 JWT

Auth0 es una plataforma de gestión de identidad y acceso (IAM) que facilita la implementación de autenticación y autorización en aplicaciones web y móviles. Ofrece un conjunto de herramientas y servicios para manejar flujos de inicio de sesión, gestión de usuarios, y más, liberando a los desarrolladores de la complejidad de la autenticación.

## Principales Características y Ventajas

- **Soporte Multifuncional:** Auth0 es compatible con una amplia variedad de proveedores de identidad, como Google, Facebook, Microsoft, y otros.
- **Inicio de Sesión Único (SSO):** Permite a los usuarios iniciar sesión una vez y acceder a varias aplicaciones sin necesidad de autenticación repetida.
- **Gestión de Usuarios:** Proporciona una interfaz de usuario para gestionar usuarios, con funciones como creación, modificación y eliminación de cuentas.
- **Seguridad y Cumplimiento Normativo:** Implementa prácticas avanzadas de seguridad, como autenticación multifactor (MFA) y gestión de certificados, cumpliendo con normativas de seguridad como GDPR y HIPAA.
- **Escalabilidad y Fiabilidad:** Diseñado para escalar con el crecimiento de la aplicación, garantiza la fiabilidad y minimiza las caídas del servicio.

## JSON Web Tokens (JWT)

JSON Web Token (JWT) es un estándar abierto (RFC 7519) que define un formato compacto y autónomo para la representación de información entre dos partes. Los JWT son comúnmente utilizados para la transmisión segura de información entre servicios web y clientes.

## Bcrypt

Bcrypt es un algoritmo de hashing diseñado para almacenar contraseñas de manera segura. A diferencia de otros métodos de hashing, Bcrypt incorpora un "factor de trabajo" que ralentiza el proceso de hashing, dificultando los ataques de fuerza bruta.

## Configuración de Middleware para Sesiones, Bcrypt y JWT

Para implementar sesiones seguras, Bcrypt y JWT, es necesario configurar middleware en Express. A continuación, se explica qué hace cada parte:

### Configuración de Sesiones

```javascript
app.use(
  session({
    secret: process.env.SESSION_SECRET,
    resave: false,
    saveUninitialized: true,
    cookie: { secure: true },
  })
);
```

- **`session`**: Configura el middleware de sesiones en Express.
- **`secret`**: Clave secreta utilizada para firmar la cookie de sesión. Debe mantenerse segura.
- **`resave`**: Evita que las sesiones se vuelvan a guardar si no han sido modificadas.
- **`saveUninitialized`**: Almacena sesiones incluso si no se han inicializado.
- **`cookie`**: Configuración de la cookie de sesión.

### Generación y Verificación de Token JWT

1. Generación de `secret` y `hashedSecret` con Bcrypt:

```javascript
const crypto = require("crypto");
const bcrypt = require("bcrypt");

const secret = crypto.randomBytes(64).toString("hex");
const hashedSecret = bcrypt.hashSync(secret, 10);
```

- **`crypto.randomBytes(64).toString('hex')`**: Genera 64 bytes de datos aleatorios y los convierte en una cadena hexadecimal. Esta cadena se utiliza como un secreto único para firmar los tokens JWT.

- **`bcrypt.hashSync(secret, 10)`**: Utiliza el algoritmo de hash Bcrypt para aplicar una función hash al secret. El segundo argumento (10) representa el número de rondas de iteración, lo que aumenta la seguridad.

2. Generación de Token JWT con `generateToken`:

```javascript
function generateToken(user) {
  return jwt.sign({ user: user.id }, hashedSecret, {
    expiresIn: "1h",
  });
}
```

- `jwt.sign({ user: user.id }, hashedSecret, { expiresIn: '1h' })`: Toma el payload, lo firma utilizando el algoritmo especificado (o el predeterminado si no se proporciona), y devuelve un token JWT.

  - El primer argumento `{ user: user.id }` es el payload del token, que contiene la información que se desea almacenar.
  - El segundo argumento `hashedSecret` es el secreto utilizado para firmar el token.
  - El tercer argumento `{ expiresIn: '1h' }` indica que el token expirará después de una hora.

- El token generado se devuelve como resultado de la función.

3. Verificación del Token con `verifyToken`:

```javascript
function verifyToken(req, res, next) {
  const token = req.session.token;
  if (!token) {
    return res.status(401).json({ mensaje: "token no generado" });
  }

  jwt.verify(token, hashedSecret, (err, decoded) => {
    if (err) {
      return res.status(401).json({ mensaje: "token inválido" });
    }
    req.user = decoded.user;
    next();
  });
}
```

- `const token = req.session.token;`: Obtiene el token almacenado en la sesión del usuario.

- `jwt.verify(token, hashedSecret, (err, decoded) => {}`: Verifica la firma del token y, si la firma es válida y el token no ha expirado, devuelve el payload decodificado.

  - `token`: El token a verificar.
  - `hashedSecret`: El secreto utilizado para firmar el token.
  - `(err, decoded) => {}`: La función de devolución de llamada que maneja el resultado de la verificación.

- En caso de que el token sea inválido, se responde con un código de estado `401` y un mensaje indicando que el token no es válido.

- Si el token es válido, el payload decodificado se asigna a `req.user` y la ejecución se pasa al siguiente middleware con `next()`.