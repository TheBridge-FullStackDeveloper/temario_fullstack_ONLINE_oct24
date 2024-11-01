# Operadores en JavaScript

## Descripción

Los operadores en JavaScript son símbolos que se utilizan para realizar operaciones en variables y valores. Pueden realizar operaciones aritméticas, comparaciones, asignaciones, lógicas, entre otras. Estos operadores son esenciales para manipular y controlar datos en un programa.

### Operadores Aritméticos

Los operadores aritméticos se utilizan para realizar operaciones matemáticas en números. Algunos operadores aritméticos comunes son:

- `+`: Suma
- `-`: Resta
- `*`: Multiplicación
- `/`: División
- `%`: Módulo (resto de la división)

Ejemplos:

```javascript
let a = 10;
let b = 5;
let suma = a + b; // suma será 15
let resta = a - b; // resta será 5
let multiplicacion = a * b; // multiplicacion será 50
let division = a / b; // division será 2
let modulo = a % b; // modulo será 0
```

### Operadores de Comparación

Los operadores de comparación se utilizan para comparar valores y devuelven un valor booleano (true o false) que indica si la comparación es verdadera o falsa. Algunos operadores de comparación comunes son:

- `==`: Igualdad
- `===`: Igualdad estricta (compara valor y tipo de dato)
- `!=`: Desigualdad
- `!==`: Desigualdad estricta
- `>`: Mayor que
- `<`: Menor que
- `>=`: Mayor o igual que
- `<=`: Menor o igual que

Ejemplos:

```javascript
let x = 10;
let y = 5;
let esIgual = x === y; // esIgual será false
let esMayor = x > y; // esMayor será true
```

### Operadores Lógicos

Los operadores lógicos se utilizan para realizar operaciones lógicas en valores booleanos. Algunos operadores lógicos comunes son:

- `&&`: AND lógico (true si ambos operandos son true)
- `||`: OR lógico (true si al menos uno de los operandos es true)
- `!`: NOT lógico (invierte el valor booleano)

Ejemplos:

```javascript
let a = true;
let b = false;
let resultadoAnd = a && b; // resultadoAnd será false
let resultadoOr = a || b; // resultadoOr será true
let resultadoNot = !a; // resultadoNot será false
```

### Operadores de asignación

Los operadores de asignación se utilizan para asignar valores a variables. Algunos operadores de asignación comunes son:

- `=`: Asignación simple
- `+=`: Asignación con suma
- `-=`: Asignación con resta
- `*=`: Asignación con multiplicación
- `/=`: Asignación con división

Ejemplos:

```javascript
let x = 10;
x += 5; // x será 15 después de esta operación
let y = 20;
y -= 8; // y será 12 después de esta operación
```