# MySQL - Estructuras y Consultas Básicas

## Introducción

MySQL es un sistema de gestión de bases de datos relacional ampliamente utilizado. Utiliza SQL (Structured Query Language) como lenguaje para gestionar y manipular datos. En este README, además de las operaciones básicas, cubriremos los tipos de datos disponibles en MySQL y ejemplos de consultas comunes.

## Tipos de Datos

En MySQL, hay tres tipos principales de datos: string, numeric y date and time.

### Tipos de Datos de Cadena (String)

| Tipo de Datos               | Descripción                                                                                                                                                                                                                                                                                |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| CHAR(size)                  | Una cadena de longitud FIJA (puede contener letras, números, y caracteres especiales). El parámetro 'size' especifica la longitud de la columna en caracteres, puede ser de 0 a 255. El valor predeterminado es 1.                                                                         |
| VARCHAR(size)               | Una cadena de longitud VARIABLE (puede contener letras, números, y caracteres especiales). El parámetro 'size' especifica la longitud máxima de la cadena en caracteres, puede ser de 0 a 65535.                                                                                           |
| BINARY(size)                | Igual a CHAR(), pero almacena cadenas de bytes binarios. El parámetro 'size' especifica la longitud de la columna en bytes. El valor predeterminado es 1.                                                                                                                                  |
| VARBINARY(size)             | Igual a VARCHAR(), pero almacena cadenas de bytes binarios. El parámetro 'size' especifica la longitud máxima de la columna en bytes.                                                                                                                                                      |
| TINYBLOB                    | Para BLOBs (Binary Large Objects). Longitud máxima: 255 bytes.                                                                                                                                                                                                                             |
| TINYTEXT                    | Almacena una cadena con una longitud máxima de 255 caracteres.                                                                                                                                                                                                                             |
| TEXT(size)                  | Almacena una cadena con una longitud máxima de 65,535 bytes.                                                                                                                                                                                                                               |
| BLOB(size)                  | Para BLOBs (Binary Large Objects). Almacena hasta 65,535 bytes de datos.                                                                                                                                                                                                                   |
| MEDIUMTEXT                  | Almacena una cadena con una longitud máxima de 16,777,215 caracteres.                                                                                                                                                                                                                      |
| MEDIUMBLOB                  | Para BLOBs (Binary Large Objects). Almacena hasta 16,777,215 bytes de datos.                                                                                                                                                                                                               |
| LONGTEXT                    | Almacena una cadena con una longitud máxima de 4,294,967,295 caracteres.                                                                                                                                                                                                                   |
| LONGBLOB                    | Para BLOBs (Binary Large Objects). Almacena hasta 4,294,967,295 bytes de datos.                                                                                                                                                                                                            |
| ENUM(val1, val2, val3, ...) | Un objeto de cadena que puede tener solo un valor, elegido de una lista de valores posibles. Puedes listar hasta 65535 valores en una lista ENUM. Si se inserta un valor que no está en la lista, se insertará un valor en blanco. Los valores se ordenan en el orden en que los ingresas. |
| SET(val1, val2, val3, ...)  | Un objeto de cadena que puede tener 0 o más valores, elegidos de una lista de valores posibles. Puedes listar hasta 64 valores en una lista SET.                                                                                                                                           |

### Tipos de Datos Numéricos (Numeric)

| Tipo de Datos             | Descripción                                                                                                                                                                                                                                                                                                                  |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT(size)                 | Un tipo de valor de bits. El número de bits por valor se especifica en 'size'. El parámetro 'size' puede contener un valor de 1 a 64. El valor predeterminado para 'size' es 1.                                                                                                                                              |
| TINYINT(size)             | Un entero muy pequeño. El rango firmado es de -128 a 127. El rango no firmado es de 0 a 255. El parámetro 'size' especifica el ancho máximo de visualización (que es 255).                                                                                                                                                   |
| BOOL                      | Cero es considerado falso, los valores no nulos se consideran verdaderos.                                                                                                                                                                                                                                                    |
| BOOLEAN                   | Igual a BOOL.                                                                                                                                                                                                                                                                                                                |
| SMALLINT(size)            | Un entero pequeño. El rango firmado es de -32768 a 32767. El rango no firmado es de 0 a 65535. El parámetro 'size' especifica el ancho máximo de visualización (que es 255).                                                                                                                                                 |
| MEDIUMINT(size)           | Un entero mediano. El rango firmado es de -8388608 a 8388607. El rango no firmado es de 0 a 16777215. El parámetro 'size' especifica el ancho máximo de visualización (que es 255).                                                                                                                                          |
| INT(size)                 | Un entero mediano. El rango firmado es de -2147483648 a 2147483647. El rango no firmado es de 0 a 4294967295. El parámetro 'size' especifica el ancho máximo de visualización (que es 255).                                                                                                                                  |
| INTEGER(size)             | Igual a INT(size).                                                                                                                                                                                                                                                                                                           |
| BIGINT(size)              | Un entero grande. El rango firmado es de -9223372036854775808 a 9223372036854775807. El rango no firmado es de 0 a 18446744073709551615. El parámetro 'size' especifica el ancho máximo de visualización (que es 255).                                                                                                       |
| FLOAT(size, d)            | Un número de punto flotante. El número total de dígitos se especifica en 'size'. El número de dígitos después del punto decimal se especifica en el parámetro 'd'. Esta sintaxis está obsoleta en MySQL 8.0.17 y se eliminará en futuras versiones de MySQL.                                                                 |
| FLOAT(p)                  | Un número de punto flotante. MySQL usa el valor 'p' para determinar si usar FLOAT o DOUBLE para el tipo de datos resultante. Si 'p' es de 0 a 24, el tipo de datos se convierte en FLOAT(). Si 'p' es de 25 a 53, el tipo de datos se convierte en DOUBLE().                                                                 |
| DOUBLE(size, d)           | Un número de punto flotante de tamaño normal. El número total de dígitos se especifica en 'size'. El número de dígitos después del punto decimal se especifica en el parámetro 'd'.                                                                                                                                          |
| DOUBLE PRECISION(size, d) | Igual a DOUBLE(size, d).                                                                                                                                                                                                                                                                                                     |
| DECIMAL(size, d)          | Un número de punto fijo exacto. El número total de dígitos se especifica en 'size'. El número de dígitos después del punto decimal se especifica en el parámetro 'd'. El número máximo para 'size' es 65. El número máximo para 'd' es 30. El valor predeterminado para 'size' es 10. El valor predeterminado para 'd' es 0. |
| DEC(size, d)              | Igual a DECIMAL(size, d).                                                                                                                                                                                                                                                                                                    |

### Tipos de Datos de Fecha y Hora (Date and Time)

| Tipo de Datos  | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DATE           | Una fecha. Formato: YYYY-MM-DD. El rango admitido es desde '1000-01-01' hasta '9999-12-31'.                                                                                                                                                                                                                                                                                                                                                                   |
| DATETIME(fsp)  | Una combinación de fecha y hora. Formato: YYYY-MM-DD hh:mm:ss. El rango admitido es desde '1000-01-01 00:00:00' hasta '9999-12-31 23:59:59'. Puedes agregar DEFAULT y ON UPDATE en la definición de la columna para obtener la inicialización automática y la actualización a la fecha y hora actual.                                                                                                                                                         |
| TIMESTAMP(fsp) | Un sello de tiempo. Los valores de TIMESTAMP se almacenan como el número de segundos desde la época de Unix ('1970-01-01 00:00:00' UTC). Formato: YYYY-MM-DD hh:mm:ss. El rango admitido es desde '1970-01-01 00:00:01' UTC hasta '2038-01-09 03:14:07' UTC. Se puede especificar la inicialización automática y la actualización a la fecha y hora actual utilizando DEFAULT CURRENT_TIMESTAMP y ON UPDATE CURRENT_TIMESTAMP en la definición de la columna. |
| TIME(fsp)      | Una hora. Formato: hh:mm:ss. El rango admitido es desde '-838:59:59' hasta '838:59:59'.                                                                                                                                                                                                                                                                                                                                                                       |
| YEAR           | Un año en formato de cuatro dígitos. Los valores permitidos en formato de cuatro dígitos son de 1901 a 2155, y 0000. MySQL 8.0 no admite el año en formato de dos dígitos.                                                                                                                                                                                                                                                                                    |

Es posible agregar las opciones adicionales UNSIGNED o ZEROFILL a todos los tipos de datos numéricos. Si se agrega la opción UNSIGNED, MySQL prohíbe valores negativos para la columna. Si se agrega la opción ZEROFILL, MySQL agrega automáticamente también el atributo UNSIGNED a la columna.

## Creación de Tablas

La creación de tablas en MySQL se realiza utilizando la sentencia `CREATE TABLE`. A continuación, se muestra un ejemplo que incorpora algunos de los tipos de datos mencionados:

```sql
CREATE TABLE Ejemplo (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    edad TINYINT UNSIGNED,
    salario DECIMAL(10, 2),
    fecha_contratacion DATE
);
```

En este ejemplo:

- `id` es una columna de tipo INT y clave primaria.
- `nombre` es una columna de tipo VARCHAR(50).
- `edad` es una columna de tipo TINYINT UNSIGNED.
- `salario` es una columna de tipo DECIMAL(10, 2).
- `fecha_contratacion` es una columna de tipo DATE.

## Consultas Básicas

### Consultas Select

1. **Seleccionar todos los registros de una tabla:**

   ```sql
   SELECT * FROM nombre_tabla;
   ```

2. **Seleccionar columnas específicas de una tabla:**

   ```sql
   SELECT columna1, columna2 FROM nombre_tabla;
   ```

3. **Filtrar resultados con una condición WHERE:**

   ```sql
   SELECT * FROM nombre_tabla WHERE condicion;
   ```

4. **Ordenar resultados en orden ascendente o descendente:**

   ```sql
   SELECT * FROM nombre_tabla ORDER BY columna ASC; -- ASC para ascendente
   SELECT * FROM nombre_tabla ORDER BY columna DESC; -- DESC para descendente
   ```

5. **Agregar una condición de agrupación:**

   ```sql
   SELECT columna, COUNT(*) FROM nombre_tabla GROUP BY columna;
   ```

### Operadores y Cláusulas Adicionales

1. **LIKE y NOT LIKE**

- `LIKE`: Se utiliza para buscar un patrón en una columna.

  ```sql
  SELECT * FROM nombre_tabla WHERE columna LIKE 'patron%';
  ```

- `NOT LIKE`: Se utiliza para excluir resultados que coincidan con un patrón.
  ```sql
  SELECT * FROM nombre_tabla WHERE columna NOT LIKE 'patron%';
  ```

2. **NOT:**

   Se utiliza para negar una condición.

   ```sql
   SELECT * FROM nombre_tabla WHERE NOT condicion;
   ```

3. **NULL:**

   Se utiliza para filtrar registros donde una columna es nula.

   ```sql
   SELECT * FROM nombre_tabla WHERE columna IS NULL;
   ```

4. **OR y AND**:

- `OR`: Se utiliza para combinar condiciones con un "o" lógico.

  ```sql
  SELECT * FROM nombre_tabla WHERE condicion1 OR condicion2;
  ```

- `AND`: Se utiliza para combinar condiciones con un "y" lógico.

  ```sql
  SELECT * FROM nombre_tabla WHERE condicion1 AND condicion2;
  ```

5. **BETWEEN**:

   Se utiliza para filtrar resultados dentro de un rango.

   ```sql
   SELECT * FROM nombre_tabla WHERE columna BETWEEN valor1 AND valor2;
   ```

6. **HAVING**:

   Se utiliza con `GROUP BY` para filtrar resultados después de la agrupación.

   ```sql
   SELECT columna, COUNT(*) FROM nombre_tabla GROUP BY columna HAVING COUNT(*) > 1;
   ```

### Otras Consultas y Operadores

1. **LIMIT**:

   Se utiliza para limitar la cantidad de filas devueltas en el resultado.

   ```sql
   SELECT * FROM nombre_tabla LIMIT 10;
   ```

2. **ALIAS**:

   `AS`: Se utiliza para asignar un alias a una columna o tabla en el resultado de la consulta.

   ```sql
   SELECT columna1 AS alias1, columna2 AS alias2 FROM nombre_tabla;
   ```

3. **Funciones de Agregación (AVG, COUNT, MIN, MAX)**:

- `AVG`: Calcula el promedio de los valores en una columna.
- `COUNT`: Cuenta el número de filas en un conjunto de resultados.
- `MIN`: Encuentra el valor mínimo en una columna.
- `MAX`: Encuentra el valor máximo en una columna.

  ```sql
  SELECT AVG(columna), COUNT(*), MIN(columna), MAX(columna) FROM nombre_tabla;
  ```

4.  **LENGTH**:

    `LENGTH` o `CHAR_LENGTH`: Devuelve la longitud de una cadena de texto.

    ```sql
    SELECT columna, LENGTH(columna) AS longitud FROM nombre_tabla;
    ```