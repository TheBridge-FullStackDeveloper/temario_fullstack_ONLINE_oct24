# Ejemplos Estructuras Express + JS + Mongoose

Vamos a construir un ejemplo práctico para ambas estructuras (básico + extendido) usando un caso sencillo: **obtener una lista de usuarios**.

---

1. Ejemplo con la estructura básica.
2. Ejemplo con la estructura extendida.
3. Estructura extendida - Añadimos validaciones y manejo de errores
4. Config vs Services


## **1. Ejemplo con la estructura básica**

### **Estructura del proyecto:**

```
📦src
 ┣ 📂config
 ┃ ┗ 📜dbConfig.js
 ┣ 📂controllers
 ┃ ┗ 📜userController.js
 ┣ 📂models
 ┃ ┗ 📜Users.js
 ┣ 📂routes
 ┃ ┗ 📜userRoutes.js
 ┗ 📜app.js
📜index.js
```

---

### **Archivos:**

1. **`src/config/dbConfig.js`**  
    Conexión a MongoDB usando Mongoose:
    
    ```javascript
    const mongoose = require("mongoose");
    
    const connectDB = async () => {
      try {
        await mongoose.connect(process.env.MONGO_URI, {
          useNewUrlParser: true,
          useUnifiedTopology: true,
        });
        console.log("Database connected successfully!");
      } catch (error) {
        console.error("Error connecting to database:", error.message);
        process.exit(1);
      }
    };
    
    module.exports = connectDB;
    ```
    
2. **`src/models/Users.js`**  
    Define el esquema del modelo de usuario:
    
    ```javascript
    const mongoose = require("mongoose");
    
    const userSchema = new mongoose.Schema({
      name: { type: String, required: true },
      email: { type: String, required: true, unique: true },
      password: { type: String, required: true },
    });
    
    module.exports = mongoose.model("User", userSchema);
    ```
    
3. **`src/controllers/userController.js`**  
    El controlador maneja la solicitud y responde al cliente:
    
    ```javascript
    const Users = require("../models/Users");
    
    const getUsers = async (req, res) => {
      try {
        const users = await Users.find(); // Obtiene todos los usuarios
        res.status(200).json(users);
      } catch (error) {
        res.status(500).json({ error: "Error fetching users" });
      }
    };
    
    module.exports = { getUsers };
    ```
    
4. **`src/routes/userRoutes.js`**  
    Define las rutas y las asocia al controlador:
    
    ```javascript
    const express = require("express");
    const router = express.Router();
    const { getUsers } = require("../controllers/userController");
    
    router.get("/users", getUsers); // Ruta para obtener usuarios
    
    module.exports = router;
    ```
    
5. **`src/app.js`**  
    Configura Express y registra las rutas:
    
    ```javascript
    const express = require("express");
    const connectDB = require("./config/dbConfig");
    const userRoutes = require("./routes/userRoutes");
    
    const app = express();
    
    app.use(express.json());
    app.use("/api", userRoutes);
    
    connectDB(); // Conexión a la base de datos
    
    module.exports = app;
    ```
    
6. **`index.js`**  
    Inicia el servidor:
    
    ```javascript
    const app = require("./src/app");
    
    const PORT = process.env.PORT || 8080;
    
    app.listen(PORT, () => {
      console.log(`Server running on port ${PORT}`);
    });
    ```
    

---

### **Flujo de trabajo con esta estructura:**

1. El cliente hace un `GET` a `/api/users`.
2. La ruta en `userRoutes.js` dirige la solicitud al controlador `getUsers` en `userController.js`.
3. El controlador consulta al modelo `Users` para obtener los datos.
4. El modelo consulta la base de datos MongoDB.
5. La respuesta se envía al cliente en formato JSON.

---

## **2. Ejemplo con la estructura extendida**

### **Estructura del proyecto:**

```
📦src
 ┣ 📂config
 ┃ ┗ 📜dbConfig.js
 ┣ 📂controllers
 ┃ ┗ 📜userController.js
 ┣ 📂models
 ┃ ┗ 📜Users.js
 ┣ 📂routes
 ┃ ┗ 📜userRoutes.js
 ┣ 📂services
 ┃ ┗ 📜userService.js
 ┣ 📂utils
 ┃ ┗ 📜dateUtils.js
 ┗ 📜app.js
📜index.js
```

---

### **Archivos (diferencias destacadas):**

1. **`src/services/userService.js`**  
    Centraliza la lógica de negocio:
    
    ```javascript
    const Users = require("../models/Users");
    
    const fetchAllUsers = async () => {
      // Aquí puedes agregar lógica adicional antes de consultar la base de datos
      const users = await Users.find();
      return users;
    };
    
    module.exports = { fetchAllUsers };
    ```
    
2. **`src/utils/dateUtils.js`**  
    Utilidad para formatear fechas (opcional):
    
    ```javascript
    const formatDate = (date) => {
      return new Date(date).toLocaleDateString("en-US");
    };
    
    module.exports = { formatDate };
    ```
    
3. **`src/controllers/userController.js`**  
    El controlador ahora delega la lógica al servicio:
    
    ```javascript
    const { fetchAllUsers } = require("../services/userService");
    
    const getUsers = async (req, res) => {
      try {
        const users = await fetchAllUsers(); // Llama al servicio
        res.status(200).json(users);
      } catch (error) {
        res.status(500).json({ error: "Error fetching users" });
      }
    };
    
    module.exports = { getUsers };
    ```
    
4. **Los demás archivos (`dbConfig`, `routes`, `app`, etc.) son idénticos al ejemplo básico.**
    

---

### **Flujo de trabajo con esta estructura:**

1. El cliente hace un `GET` a `/api/users`.
2. La ruta en `userRoutes.js` dirige la solicitud al controlador `getUsers` en `userController.js`.
3. El controlador llama al servicio `fetchAllUsers` en `userService.js`.
4. El servicio consulta al modelo `Users` para obtener los datos.
5. (Opcional) El servicio usa alguna utilidad (`utils`) para procesar los datos (como formatear fechas).
6. La respuesta procesada se envía al cliente en formato JSON.

---

### **Diferencias clave entre ambas estructuras:**

|**Estructura básica**|**Estructura extendida**|
|---|---|
|Controlador maneja toda la lógica.|Servicio maneja la lógica de negocio.|
|Menos archivos; más sencillo.|Más archivos; mejor organizado.|
|Puede volverse difícil de mantener.|Escalable y fácil de mantener.|
|Ideal para proyectos pequeños o MVPs.|Ideal para proyectos medianos o grandes.|

---

¡Vamos a mejorar los ejemplos! Agregaremos **validaciones** y un **manejo de errores más robusto**. Esto será útil para proyectos en crecimiento.

---

# 3. **Estructura extendida - Añadimos validaciones y manejo de errores**

### **Mejoras al ejemplo:**

1. **Validaciones** para verificar los datos que envía el cliente.
2. **Manejo de errores centralizado**, usando un middleware para evitar duplicar lógica de manejo de errores en cada controlador.

### **Estructura extendida actualizada:**

```
📦src
 ┣ 📂config
 ┃ ┗ 📜dbConfig.js
 ┣ 📂controllers
 ┃ ┗ 📜userController.js
 ┣ 📂middlewares
 ┃ ┗ 📜errorHandler.js
 ┣ 📂models
 ┃ ┗ 📜Users.js
 ┣ 📂routes
 ┃ ┗ 📜userRoutes.js
 ┣ 📂services
 ┃ ┗ 📜userService.js
 ┣ 📂utils
 ┃ ┗ 📜validationUtils.js
 ┗ 📜app.js
📜index.js
```

---

### **Archivos mejorados:**

#### **1. `src/utils/validationUtils.js`**

Aquí creamos funciones reutilizables para validar datos:

```javascript
const validateEmail = (email) => {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailRegex.test(email);
};

const validateUserInput = (userData) => {
  const { name, email, password } = userData;

  if (!name || name.length < 3) {
    throw new Error("Name must be at least 3 characters long.");
  }

  if (!email || !validateEmail(email)) {
    throw new Error("Invalid email format.");
  }

  if (!password || password.length < 6) {
    throw new Error("Password must be at least 6 characters long.");
  }

  return true;
};

module.exports = { validateUserInput };
```

---

#### **2. `src/middlewares/errorHandler.js`**

Middleware para manejar errores en un solo lugar:

```javascript
const errorHandler = (err, req, res, next) => {
  console.error(err.message); // Registra el error en la consola

  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
  });
};

module.exports = errorHandler;
```

---

#### **3. `src/controllers/userController.js`**

Validamos los datos antes de procesarlos y dejamos que el middleware maneje los errores:

```javascript
const { fetchAllUsers } = require("../services/userService");
const { validateUserInput } = require("../utils/validationUtils");

const getUsers = async (req, res, next) => {
  try {
    const users = await fetchAllUsers();
    res.status(200).json(users);
  } catch (error) {
    next(error); // Envía el error al middleware
  }
};

const createUser = async (req, res, next) => {
  try {
    validateUserInput(req.body); // Valida la entrada del cliente
    const newUser = await createUserService(req.body); // Llama al servicio para guardar el usuario
    res.status(201).json(newUser);
  } catch (error) {
    next(error); // Envía el error al middleware
  }
};

module.exports = { getUsers, createUser };
```

---

#### **4. `src/routes/userRoutes.js`**

Agregamos la ruta para crear usuarios:

```javascript
const express = require("express");
const router = express.Router();
const { getUsers, createUser } = require("../controllers/userController");

router.get("/users", getUsers); // Ruta para obtener todos los usuarios
router.post("/users", createUser); // Ruta para crear un nuevo usuario

module.exports = router;
```

---

#### **5. `src/app.js`**

Registramos el middleware de errores:

```javascript
const express = require("express");
const connectDB = require("./config/dbConfig");
const userRoutes = require("./routes/userRoutes");
const errorHandler = require("./middlewares/errorHandler");

const app = express();

app.use(express.json());
app.use("/api", userRoutes);
app.use(errorHandler); // Middleware de manejo de errores

connectDB();

module.exports = app;
```

---

#### **6. `src/services/userService.js`**

Agregamos un servicio para guardar un usuario:

```javascript
const Users = require("../models/Users");

const fetchAllUsers = async () => {
  const users = await Users.find();
  return users;
};

const createUserService = async (userData) => {
  const user = new Users(userData);
  await user.save();
  return user;
};

module.exports = { fetchAllUsers, createUserService };
```

---

### **Flujo de trabajo mejorado:**

#### **1. Obtener usuarios (`GET /api/users`):**

1. Cliente solicita todos los usuarios.
2. Ruta `GET /users` llama al controlador `getUsers`.
3. Controlador llama al servicio `fetchAllUsers`, que consulta el modelo `Users`.
4. Respuesta con los usuarios o error manejado por el middleware.

#### **2. Crear usuario (`POST /api/users`):**

1. Cliente envía datos (nombre, email, contraseña).
2. Ruta `POST /users` llama al controlador `createUser`.
3. Controlador valida los datos con `validateUserInput`.
4. Si la validación pasa, llama al servicio `createUserService` para guardar al usuario.
5. Respuesta con el nuevo usuario o error manejado por el middleware.

---

### **Ventajas de este enfoque:**

1. **Validaciones centralizadas**: Puedes agregar más reglas de validación en un solo archivo (`validationUtils.js`).
2. **Manejo de errores limpio**: En lugar de escribir `try-catch` en todos los controladores, el middleware se encarga.
3. **Reutilización de lógica**: Si necesitas validar o procesar datos, puedes reutilizar funciones y servicios.
4. **Escalabilidad**: Agregar nuevas rutas, validaciones o servicios no afecta otras partes del código.

---

## **4. Config vs Services**

Es común tener tanto la carpeta `config` como la carpeta `services` en un proyecto de programación, y cada una tiene una función diferente. Aquí te explico el propósito de cada una:

### Carpeta `config/`
La carpeta `config/` se utiliza para almacenar archivos de configuración que definen cómo debe comportarse la aplicación en diferentes entornos (desarrollo, producción, testing, etc.). Estos archivos suelen contener variables de configuración, como credenciales de bases de datos, claves de API, configuraciones de servidor, etc. Por ejemplo:

- **database.js**: Configuración de la conexión a la base de datos.
- **auth.js**: Configuración relacionada con la autenticación (JWT, OAuth, etc.).
- **server.js**: Configuración del servidor (puerto, host, etc.).

Ejemplo de un archivo de configuración:
```javascript
// config/database.js
module.exports = {
  development: {
    username: 'root',
    password: 'password',
    database: 'myapp_dev',
    host: 'localhost',
    dialect: 'mysql',
  },
  production: {
    username: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_NAME,
    host: process.env.DB_HOST,
    dialect: 'mysql',
  },
};
```

### Carpeta `services/`
La carpeta `services/` se utiliza para almacenar la lógica de negocio de la aplicación. Los servicios son responsables de manejar la lógica compleja, interactuar con los modelos, realizar cálculos, llamar a APIs externas, etc. Los servicios suelen ser utilizados por los controladores para separar la lógica de negocio de la lógica de manejo de solicitudes HTTP.

Por ejemplo:
- **userService.js**: Lógica relacionada con usuarios (creación, actualización, autenticación, etc.).
- **taskService.js**: Lógica relacionada con tareas (creación, asignación, cálculo de estadísticas, etc.).

Ejemplo de un archivo de servicio:
```javascript
// services/userService.js
const UserModel = require('../models/userModel');

class UserService {
  async createUser(userData) {
    const user = await UserModel.create(userData);
    return user;
  }

  async getUserById(userId) {
    const user = await UserModel.findById(userId);
    return user;
  }
}

module.exports = new UserService();
```

### Diferencias clave entre `config/` y `services/`
1. **Propósito**:
   - `config/`: Almacena configuraciones estáticas o dinámicas que afectan el comportamiento de la aplicación.
   - `services/`: Contiene la lógica de negocio y operaciones complejas que no pertenecen a los controladores o modelos.

2. **Contenido**:
   - `config/`: Archivos de configuración (JSON, JavaScript, YAML, etc.).
   - `services/`: Clases o funciones que implementan la lógica de negocio.

3. **Uso**:
   - `config/`: Se usa para inicializar la aplicación o para acceder a valores de configuración en cualquier parte del proyecto.
   - `services/`: Se usa en los controladores para delegar la lógica de negocio y mantener el código limpio y modular.

### ¿Es común tener ambas en el mismo proyecto?
Sí, es común y recomendable tener ambas carpetas en un proyecto bien estructurado. La separación de responsabilidades entre configuración (`config/`) y lógica de negocio (`services/`) ayuda a mantener el código organizado, escalable y fácil de mantener.

### Ejemplo de uso conjunto
Un controlador podría usar tanto la configuración como un servicio:
```javascript
// controllers/userController.js
const UserService = require('../services/userService');
const config = require('../config/auth');

class UserController {
  async register(req, res) {
    const userData = req.body;
    const user = await UserService.createUser(userData);
    res.status(201).json({ user });
  }

  async login(req, res) {
    const { email, password } = req.body;
    const user = await UserService.getUserByEmail(email);
    // Lógica de autenticación usando config.JWT_SECRET
    const token = generateToken(user, config.JWT_SECRET);
    res.json({ token });
  }
}

module.exports = new UserController();
```

En resumen, ambas carpetas son importantes y cumplen funciones distintas en un proyecto de programación bien organizado.
