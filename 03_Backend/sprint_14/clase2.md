# MongoDB y Mongoose

## 1. Introducción a MongoDB

MongoDB es una base de datos NoSQL que almacena datos en formato BSON (Binary JSON). Utiliza colecciones y documentos para organizar la información.

### Características Clave de MongoDB:

#### Documentos y Colecciones:

- Documento: Registro de datos en formato BSON.
- Colección: Grupo de documentos relacionados.

#### Esquema Dinámico:

- Documentos en una colección pueden tener esquemas diferentes.

#### ID Único:

- Cada documento tiene un campo `_id` único.

#### Consultas Flexibles:

- Admite consultas complejas y anidadas.

#### Escalabilidad Horizontal:

- Escalabilidad agregando más servidores.

## 2. Mongoose: Modelado de Datos para MongoDB en Node.js

Mongoose facilita la interacción con MongoDB en Node.js, proporcionando funciones para definir esquemas y modelos.

```javascript
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/mi_base_de_datos", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const conexion = mongoose.connection;

conexion.on("error", console.error.bind(console, "Error de conexión:"));
conexion.once("open", () => {
  console.log("Conexión exitosa a MongoDB");
});
```

- Se conecta a MongoDB usando `mongoose.connect`.
- El evento `open` se activa cuando la conexión es exitosa.

## 3. Definición de Esquemas y Modelos con Mongoose

```javascript
const mongoose = require("mongoose");

const esquemaUsuario = new mongoose.Schema({
  nombre: String,
  edad: Number,
  email: { type: String, unique: true },
});

const ModeloUsuario = mongoose.model("Usuario", esquemaUsuario);
```

- Define un esquema con campos `nombre`, `edad` y `email`.
- `ModeloUsuario` es el modelo basado en el esquema para interactuar con la colección 'usuarios'.

## 4. Operaciones CRUD Básicas con Mongoose

**Crear un nuevo documento**:

```javascript
const nuevoUsuario = new ModeloUsuario({
  nombre: "Juan",
  edad: 30,
  email: "juan@example.com",
});

nuevoUsuario.save((error, usuario) => {
  if (error) return console.error(error);
  console.log("Usuario guardado correctamente:", usuario);
});
```

- Se crea una nueva instancia de `ModeloUsuario` con los datos del usuario a agregar.
- `nuevoUsuario.save(callback)` guarda el nuevo usuario en la base de datos.
- Si hay un error, se maneja en el callback.

**Consulta de documentos**:

```javascript
ModeloUsuario.find({ edad: { $gte: 25 } }, (error, usuarios) => {
  if (error) return console.error(error);
  console.log("Usuarios mayores o iguales a 25 años:", usuarios);
});
```

- `ModeloUsuario.find(query, callback)` busca documentos que coincidan con el query.

**Actualización de un documento**:

```javascript
ModeloUsuario.updateOne(
  { nombre: "Juan" },
  { edad: 31 },
  (error, resultado) => {
    if (error) return console.error(error);
    console.log("Documento actualizado:", resultado);
  }
);
```

- `ModeloUsuario.updateOne(filter, update, callback)` actualiza un documento que coincide con el filtro.

**Eliminación de un documento:**:

```javascript
ModeloUsuario.deleteOne({ nombre: "Juan" }, (error) => {
  if (error) return console.error(error);
  console.log("Documento eliminado correctamente.");
});
```

- `ModeloUsuario.deleteOne(filter, callback)` elimina un documento que coincide con el filtro.

## Métodos Más Utilizados en MongoDB:

- `db.collection.find(query)`: Busca documentos en una colección que coincidan con el query.
- `db.collection.insertOne(document)`: Inserta un nuevo documento en la colección.
- `db.collection.updateOne(filter, update)`: Actualiza un documento que coincide con el filtro.
- `db.collection.deleteOne(filter)`: Elimina un documento que coincide con el filtro.
- `db.collection.aggregate(pipeline)`: Realiza operaciones de agregación en la colección.

## Operadores de Consulta en MongoDB:

Los operadores de consulta son herramientas poderosas para filtrar datos en MongoDB. Aquí hay algunos operadores importantes:

- `$eq`: Igual a.

```javascript
ModeloUsuario.find({ edad: { $eq: 30 } }, (error, usuarios) => {
  // Busca usuarios con edad igual a 30.
});
```

- `$ne`: No igual a.

```javascript
ModeloUsuario.find({ edad: { $ne: 30 } }, (error, usuarios) => {
  // Busca usuarios con edad diferente de 30.
});
```

- `$gt`: Mayor que.

```javascript
ModeloUsuario.find({ edad: { $gt: 30 } }, (error, usuarios) => {
  // Busca usuarios con edad mayor a 30.
});
```

- `$lt`: Menor que.

```javascript
ModeloUsuario.find({ edad: { $lt: 30 } }, (error, usuarios) => {
  // Busca usuarios con edad menor a 30.
});
```

- `$gte`: Mayor o igual que.

```javascript
ModeloUsuario.find({ edad: { $gte: 30 } }, (error, usuarios) => {
  // Busca usuarios con edad mayor o igual a 30.
});
```

- `$lte`: Menor o igual que.

```javascript
ModeloUsuario.find({ edad: { $lte: 30 } }, (error, usuarios) => {
  // Busca usuarios con edad menor o igual a 30.
});
```

- `$in`: Coincide con cualquiera de los valores en un array.

```javascript
ModeloUsuario.find({ edad: { $in: [25, 30, 35] } }, (error, usuarios) => {
  // Busca usuarios con edad 25, 30 o 35.
});
```

- `$nin`: No coincide con ninguno de los valores en un array.

```javascript
ModeloUsuario.find({ edad: { $nin: [25, 30, 35] } }, (error, usuarios) => {
  // Busca usuarios con edad diferente de 25, 30 y 35.
});
```

- `$and`: Combina varias condiciones con lógica AND.

```javascript
ModeloUsuario.find(
  { $and: [{ edad: { $gte: 25 } }, { nombre: "Juan" }] },
  (error, usuarios) => {
    // Busca usuarios con edad mayor o igual a 25 y nombre Juan.
  }
);
```

- `$or`: Combina varias condiciones con lógica OR.

```javascript
ModeloUsuario.find(
  { $or: [{ edad: { $gte: 30 } }, { nombre: "Maria" }] },
  (error, usuarios) => {
    // Busca usuarios con edad mayor o igual a 30 o nombre Maria.
  }
);
```

- `$not`: Niega la condición que lo precede.

```javascript
ModeloUsuario.find({ edad: { $not: { $eq: 30 } } }, (error, usuarios) => {
  // Busca usuarios con edad diferente de 30.
});
```