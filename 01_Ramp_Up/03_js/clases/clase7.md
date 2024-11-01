# Objetos y Métodos en JavaScript

## Descripción

En JavaScript, un objeto es una estructura de datos que puede contener propiedades y métodos. Una propiedad es una asociación entre un nombre (una clave) y un valor, mientras que un método es una función asociada al objeto. Los objetos permiten organizar y manipular datos de manera estructurada y eficiente.

## Creación de Objetos

Puedes crear objetos en JavaScript de diversas maneras. Una forma común es utilizando la notación de objeto literal:

```javascript
let persona = {
  nombre: "Juan",
  edad: 30,
  saludar: function () {
    console.log(
      "Hola, soy " + this.nombre + " y tengo " + this.edad + " años."
    );
  },
};
```

## Acceso a Propiedades y Métodos

Puedes acceder a las propiedades y métodos de un objeto utilizando la notación de punto:

```javascript
console.log(persona.nombre); // Acceso a la propiedad nombre
persona.saludar(); // Llamada al método saludar
```

## Ejemplo

Aquí tienes un ejemplo de cómo se puede usar un objeto para representar una persona:

```javascript
let persona = {
  nombre: "María",
  edad: 25,
  saludar: function () {
    console.log(
      "Hola, soy " + this.nombre + " y tengo " + this.edad + " años."
    );
  },
};

persona.saludar();
```