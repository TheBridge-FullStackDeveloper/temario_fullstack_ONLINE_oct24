# Condicionales en JavaScript

## Descripción

Las estructuras condicionales en JavaScript permiten controlar el flujo de ejecución del programa basándose en ciertas condiciones. Los condicionales se utilizan para ejecutar un bloque de código si una condición es verdadera (`true`) o para ejecutar un bloque de código alternativo si la condición es falsa (`false`).

## Tipos de Condicionales

### `if` declaración

La declaración `if` permite ejecutar un bloque de código si la condición es verdadera.

Ejemplo:

```javascript
let edad = 18;
if (edad >= 18) {
  console.log("Eres mayor de edad");
}
```

### `if...else` declaración

La declaración `if...else` ejecuta un bloque de código si la condición es verdadera y otro bloque si es falsa.

Ejemplo:

```javascript
let hora = 15;
if (hora < 12) {
  console.log("Buenos días");
} else {
  console.log("Buenas tardes");
}
```

### `else if` declaración

La declaración `else if` permite encadenar múltiples condiciones a comprobar.

Ejemplo:

```javascript
let puntaje = 75;
if (puntaje >= 90) {
  console.log("Aprobado con A");
} else if (puntaje >= 80) {
  console.log("Aprobado con B");
} else if (puntaje >= 70) {
  console.log("Aprobado con C");
} else {
  console.log("Reprobado");
}
```

### Operador ternario

El operador ternario (`condición ? valorSiVerdadero : valorSiFalso`) ofrece una forma concisa de expresar una estructura `if...else`.

Ejemplo:

```javascript
let esMayor = edad >= 18 ? "Sí" : "No";
console.log(`¿Es mayor de edad? ${esMayor}`);
```