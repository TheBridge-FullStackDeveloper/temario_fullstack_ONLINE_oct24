# CREAR MODELOS CON MONGOOSE

### 1. **Modelo básico con campos simples**

---

Modelo básico con diferentes tipos de datos simples: String, Number, Boolean y
Date. Añadimos el **timestamps** para generar fecha de creación y actualización
automáticas.

```js
const mongoose = require("mongoose");

const UsuarioSchema = new mongoose.Schema(
  {
    nombre: {
      type: String,
      required: true, // campo obligatorio
    },
    edad: {
      type: Number,
      min: 18, // validación: edad mínima de 18
      max: 100, // validación: edad máxima de 100
    },
    activo: {
      type: Boolean,
      default: true, // valor por defecto
    },
    fechaRegistro: {
      type: Date,
      default: Date.now, // fecha actual por defecto
    },
  },
  { timestamps: true }
); // creación y actualizaciones por defecto

const Usuario = mongoose.model("Usuario", UsuarioSchema);
module.exports = Usuario;
```

### 2. **Modelo con validaciones personalizadas**

---

Podemos agregar validaciones personalizadas y mensajes de error personalizados.

```js
const mongoose = require("mongoose");

const ProductoSchema = new mongoose.Schema({
  nombre: {
    type: String,
    required: [true, "el nombre del producto es obligatorio"], // mensaje de error personalizado
  },
  precio: {
    type: Number,
    required: true,
    min: [0, "el precio no puede ser negativo"], // validación personalizada
  },
  descripcion: {
    type: String,
    maxlength: [500, "la descripción tiene máximo 500 caracteres"],
  },
});

const Producto = mongoose.model("Producto", ProductoSchema);
module.exports = Producto;
```

### **3. Modelo con campos anidados**

---

Podemos definir esquemas anidados para crear estructuras más compleja

```js
const mongoose = require("mongoose");
const DireccionSchema = new mongoose.Schema({
  calle: String,
  ciudad: String,
  codigoPostal: String,
  pais: String,
});
const ClienteSchema = new mongoose.Schema({
  nombre: String,
  email: {
    type: String,
    unique: true, // campo único
  },
  direccion: DireccionSchema, // unimos con direccion, campo anidado
});

const Cliente = mongoose.model("Cliente", ClienteSchema);
module.exports = Cliente;
```

### **4. Modelo con referencias a otros modelos (relaciones)**

---

Podemos crear relaciones entre modelos usando referencias. En un modelo
referenciamos el modelo al que queremos unir. Hacemos estos modelos
relacionales. No hay necesidad de un tercer modelo como pasaba con las tablas
SQL.

```js
const mongoose = require("mongoose");

const PedidoSchema = new mongoose.Schema({
  producto: {
    type: mongoose.Schema.Types.ObjectId,
    ref: "Producto", // Referencia al modelo Producto
    required: true,
  },
  cantidad: {
    type: Number,
    required: true,
  },
  cliente: {
    type: mongoose.Schema.Types.ObjectId,
    ref: "Cliente", // Referencia al modelo Cliente
    required: true,
  },
});

const Pedido = mongoose.model("Pedido", PedidoSchema);
module.exports = Pedido;
```

### **5. Modelo con arrays y objetos**

---

Puedes definir campos que sean objetos de tipo array u objet

```JavaScript
const mongoose = require('mongoose');

const BlogSchema = new mongoose.Schema({
  titulo: String,
  contenido: String,
  etiquetas: [String], // Array de strings
  comentarios: [
    {
      autor: String,
      contenido: String,
      fecha:
      {
        type: Date,
        default: Date.now,
      },
    },
  ], // Array de objetos
});

const Blog = mongoose.model('Blog', BlogSchema);
module.exports = Blog;
```

### **6. Modelo con métodos personalizados**

---

Podemos añadir métodos a nuestros modelos y usarlos por ejemplo para verificar contraseña como en el ejemplo.

```js
const mongoose = require("mongoose");

const UsuarioSchema = new mongoose.Schema({
  nombre: String,
  email: String,
  contraseña: String,
});

// Método para verificar la contraseña
UsuarioSchema.methods.verificarContraseña = function (contraseña) {
  return this.contraseña === contraseña;
};

const Usuario = mongoose.model("Usuario", UsuarioSchema);
module.exports = Usuario;
```
