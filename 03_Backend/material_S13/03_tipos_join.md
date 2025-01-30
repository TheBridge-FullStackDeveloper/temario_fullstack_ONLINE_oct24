# Tipos de JOIN en SQL


ÍNDICE
### 1. TIPOS DE JOIN:
**¿Qué es un `JOIN` en SQL?**
1. INNER JOIN (Solo coincidencias)
2. LEFT JOIN (Todos los de la izquierda + coincidencias de la derecha)
3. RIGHT JOIN (Todos los de la derecha + coincidencias de la izquierda)
4. FULL OUTER JOIN (Todos los datos de ambas tablas, aunque no tengan coincidencias)
5. CROSS JOIN (Todas las combinaciones posibles)
6. SELF JOIN (Comparar dentro de la misma tabla)
### 2. EJEMPLOS.
### 3. DUDAS FRECUENTES.


---

## **📌 ¿Qué es un `JOIN` en SQL?**

Un `JOIN` es una cláusula que **combina filas de dos o más tablas** basándose en una columna en común. Esto nos permite relacionar datos dispersos en varias tablas y consultarlos de manera eficiente.

---
### 🚀 **Resumen de los tipos de `JOIN` en SQL**

Los `JOIN` se usan para combinar datos de **dos tablas** según una columna en común.

❌ `JOIN` **no modifica las tablas**.  
✅ `JOIN` **solo une los datos para visualizarlos en la consulta**.  
❗ Para hacer cambios en la base de datos, debes usar `UPDATE`, `INSERT` o `DELETE`.

---

### **1️⃣ INNER JOIN (Solo coincidencias)**

🔹 Une las filas **que tienen coincidencias** en ambas tablas.  
🔹 Si un dato no tiene coincidencia, se **excluye**.

```sql
SELECT * FROM TablaA  
INNER JOIN TablaB ON TablaA.id = TablaB.id;
```

✅ Se usa cuando solo quieres los registros que existen en ambas tablas.

---

### **2️⃣ LEFT JOIN (Todos los de la izquierda + coincidencias de la derecha)**

🔹 Devuelve **todos los registros de la primera tabla** (izquierda) y **solo las coincidencias** de la segunda (derecha).  
🔹 Si no hay coincidencia, pone `NULL`.

```sql
SELECT * FROM TablaA  
LEFT JOIN TablaB ON TablaA.id = TablaB.id;
```

✅ Se usa cuando necesitas **todos los datos de la tabla izquierda** aunque no haya coincidencias.

---

### **3️⃣ RIGHT JOIN (Todos los de la derecha + coincidencias de la izquierda)**

🔹 Similar a `LEFT JOIN`, pero devuelve **todos los registros de la segunda tabla** (derecha) y solo las coincidencias de la primera (izquierda).  
🔹 Si no hay coincidencia, pone `NULL`.

```sql
SELECT * FROM TablaA  
RIGHT JOIN TablaB ON TablaA.id = TablaB.id;
```

✅ Se usa cuando necesitas **todos los datos de la tabla derecha** aunque no haya coincidencias.

---

### **4️⃣ FULL OUTER JOIN (Todos los datos de ambas tablas)**

🔹 Devuelve **todos los registros** de ambas tablas.  
🔹 Si no hay coincidencia, pone `NULL`.

```sql
SELECT * FROM TablaA  
FULL OUTER JOIN TablaB ON TablaA.id = TablaB.id;
```

✅ Se usa cuando quieres ver **todos los datos**, aunque no haya coincidencias.

---

### 5️⃣ **CROSS JOIN (Todas las combinaciones posibles)**

🔹 Combina **cada fila de la primera tabla con todas las filas de la segunda tabla**, generando todas las combinaciones posibles.
🔹 **No requiere coincidencias** (`ON`), simplemente cruza todos los datos.

```sql
SELECT * FROM TablaA CROSS JOIN TablaB;
```

✅ Se usa cuando quieres ver **todos los datos**, aunque no haya coincidencias.

💡 **Ejemplo práctico:**  
Tienes una tabla de **productos** y otra de **descuentos**. Con `CROSS JOIN`, puedes generar todas las combinaciones posibles de productos con descuentos.

### **6️⃣ SELF JOIN (Unir una tabla consigo misma)**

🔹 **Compara filas dentro de la misma tabla**.  
🔹 Se usa cuando los datos están **relacionados entre sí**, como empleados y jefes o conexiones entre usuarios.

```sql
SELECT a.*, b.* 
FROM TablaA a 
JOIN TablaA b ON a.campo = b.campo;
```

✅ Se usa cuando quieres **comparar datos dentro de la misma tabla**.

💡 **Ejemplo práctico:**  
Tienes una tabla de empleados donde cada uno puede tener un **jefe** (que también está en la misma tabla).
### **📌 Resumen rápido**

| JOIN                | ¿Qué devuelve?                                     |
| ------------------- | -------------------------------------------------- |
| **INNER JOIN**      | Solo coincidencias                                 |
| **LEFT JOIN**       | Todo de la izquierda + coincidencias de la derecha |
| **RIGHT JOIN**      | Todo de la derecha + coincidencias de la izquierda |
| **FULL OUTER JOIN** | Todo de ambas tablas, aunque no haya coincidencias |


## 2. EJEMPLOS 

### **1️⃣ INNER JOIN (Solo coincidencias en ambas tablas)**

💡 **Sirve para obtener solo los datos que coinciden en ambas tablas**.  
Si un dato está en una tabla pero no en la otra, **NO se muestra en el resultado**.

💡 **Ejemplo real: Clientes y Pedidos**  
Tienes una lista de clientes y otra de pedidos.  
Quieres ver **solo los clientes que han hecho pedidos**.

📌 **Datos:**
#### **Tabla `Clientes`**

|id|nombre|
|---|---|
|1|Juan|
|2|María|
|3|Pedro|
|4|Laura|

#### **Tabla `Pedidos`**

| id  | cliente_id | producto  |
| --- | ---------- | --------- |
| 1   | 2          | Laptop    |
| 2   | 3          | Televisor |
| 3   | 4          | Tablet    |

📌 **Consulta con `INNER JOIN`**

```sql
SELECT Clientes.nombre, Pedidos.producto  
FROM Clientes  
INNER JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

📌 **Resultado:**

| nombre | producto  |
| ------ | --------- |
| María  | Laptop    |
| Pedro  | Televisor |
| Laura  | Tablet    |

✅ **Solo aparecen los clientes que han hecho pedidos.**  
✅ **Juan no aparece porque no tiene pedidos registrados.**

### 📌 **¿Cuándo se usa en la vida real?**

✔️ Para ver **usuarios que han comprado productos**.  
✔️ Para encontrar **empleados asignados a proyectos**.  
✔️ Para unir **facturas con clientes** (solo si existen en ambas tablas).

---

### **2️⃣ LEFT JOIN (Todos los datos de la izquierda + coincidencias de la derecha)**

💡 **Devuelve todos los registros de la tabla de la izquierda** (aunque no tengan coincidencias en la derecha).  Si no hay coincidencia, muestra `NULL` en los datos de la derecha.

💡 **Ejemplo real: Clientes y Pedidos**  
Quieres ver **todos los clientes, aunque no hayan hecho pedidos**.

📌 **Consulta con `LEFT JOIN`**

```sql
SELECT Clientes.nombre, Pedidos.producto  
FROM Clientes  
LEFT JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

📌 **Resultado:**

| nombre | producto  |
| ------ | --------- |
| Juan   | NULL      |
| María  | Laptop    |
| Pedro  | Televisor |
| Laura  | Tablet    |

✅ **Juan aparece aunque no tenga pedidos (`NULL`).**  
✅ **El resto de clientes tienen pedidos asignados.**

### 📌 **¿Cuándo se usa en la vida real?**

✔️ Para ver **todos los clientes, incluso los que no han comprado nada**.  
✔️ Para ver **empleados, aunque no tengan un proyecto asignado**.  
✔️ Para encontrar **productos sin ventas**.

---

### **3️⃣ RIGHT JOIN (Todos los datos de la derecha + coincidencias de la izquierda)**

💡 **Devuelve todos los registros de la tabla de la derecha** (aunque no tengan coincidencias en la izquierda).  
Si no hay coincidencia, muestra `NULL` en los datos de la izquierda.

💡 **Ejemplo real: Pedidos y Clientes**  
Quieres ver **todos los pedidos, aunque no sepamos de qué cliente son**.

📌 **Consulta con `RIGHT JOIN`**

```sql
SELECT Clientes.nombre, Pedidos.producto  
FROM Clientes  
RIGHT JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

📌 **Resultado:**

| nombre | producto  |
| ------ | --------- |
| María  | Laptop    |
| Pedro  | Televisor |
| Laura  | Tablet    |
| NULL   | Monitor   |

✅ **El pedido del "Monitor" aparece aunque no tenga cliente (`NULL`).**  
✅ **Los demás pedidos tienen clientes asignados.**

### 📌 **¿Cuándo se usa en la vida real?**

✔️ Para ver **todos los pedidos, incluso si no tienen cliente**.  
✔️ Para encontrar **facturas sin cliente asignado**.  
✔️ Para ver **productos en inventario, incluso si no tienen proveedor registrado**.


---
### 4️⃣ **FULL JOIN (ver TODO, incluso lo que no coincide)**

💡  Sirve para combinar **dos listas de datos distintas** y ver **qué elementos tienen coincidencias y cuáles no**.  Es útil cuando manejas **datos incompletos** y quieres ver qué información falta en cada lado.

💡 **Ejemplo real: Clientes y Pedidos**  

Tienes dos listas:

1. **Clientes** (algunos no han hecho pedidos todavía).
2. **Pedidos** (algunos pedidos son de clientes que ya no existen en la base de datos).

📌 **Datos:**

#### **Tabla `Clientes`**

|id|nombre|
|---|---|
|1|Juan|
|2|María|
|3|Pedro|

#### **Tabla `Pedidos`**

| id  | cliente_id | producto  |
| --- | ---------- | --------- |
| 1   | 2          | Laptop    |
| 2   | 3          | Televisor |
| 3   | 4          | Tablet    |

📌 **Consulta con `FULL JOIN`**

```sql
SELECT Clientes.nombre, Pedidos.producto 
FROM Clientes FULL 
JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;`
```

📌 **Resultado:**

| nombre | producto  |
| ------ | --------- |
| María  | Laptop    |
| Pedro  | Televisor |
| Juan   | NULL      |
| NULL   | Tablet    |

✅ **María y Pedro aparecen porque han hecho pedidos.**  
✅ **Juan aparece con `NULL` porque no ha hecho ningún pedido.**  
✅ **El pedido de la Tablet aparece con `NULL` porque su cliente ya no está registrado.**

### 📌 **¿Cuándo se usa en la vida real?**

✔️ Para encontrar **clientes sin pedidos** o **pedidos sin clientes**.  
✔️ Para fusionar bases de datos donde **no todos los datos coinciden**.  
✔️ Para encontrar **inconsistencias** en sistemas  o si faltan datos.

---

### 5️⃣ **CROSS JOIN - Todas las combinaciones posibles**

💡 Sirve para **generar todas las combinaciones posibles** entre dos conjuntos de datos.  
Es útil para probar **todas las opciones de algo**, como precios, combinaciones de productos o asignaciones.

💡 **Ejemplo real: Menú de restaurante**  

Tienes dos listas:
1. **Platos** (hamburguesa, pizza, ensalada).
2. **Bebidas** (coca-cola, zumo, agua).

📌 **Datos:**
#### **Tabla `Platos`**

|id|nombre|
|---|---|
|1|Hamburguesa|
|2|Pizza|
|3|Ensalada|

#### **Tabla `Bebidas`**

| id  | nombre    |
| --- | --------- |
| 1   | Coca-Cola |
| 2   | Zumo      |
| 3   | Agua      |

📌 **Consulta con `CROSS JOIN`**

``` sql

SELECT Platos.nombre AS Plato, Bebidas.nombre AS Bebida 
FROM Platos CROSS JOIN Bebidas;
```

📌  **Resultado (todas las combinaciones posibles de comidas y bebidas):**

| Plato       | Bebida    |
| ----------- | --------- |
| Hamburguesa | Coca-Cola |
| Hamburguesa | Zumo      |
| Hamburguesa | Agua      |
| Pizza       | Coca-Cola |
| Pizza       | Zumo      |
| Pizza       | Agua      |
| Ensalada    | Coca-Cola |
| Ensalada    | Zumo      |
| Ensalada    | Agua      |

✅ **Todas las comidas se combinan con todas las bebidas.**  
✅ **Esto genera automáticamente un menú completo con todas las opciones.**

### 📌 **¿Cuándo se usa en la vida real?**

✔️ Para generar **todas las combinaciones posibles de productos y opciones** (ej. menú de restaurante, combos en tiendas).  
✔️ Para probar **todas las combinaciones posibles** en experimentos o cálculos.  
✔️ Para asignar **turnos de trabajo** (ej. combinar empleados con horarios disponibles).

---

### 6️⃣ **SELF JOIN (Comparar datos dentro de la misma tabla)**

💡 Sirve para **comparar filas dentro de la misma tabla**.  
Se usa cuando los datos están **relacionados consigo mismos**, como empleados y jefes, productos similares o conexiones entre usuarios.

💡 **Ejemplo real: Empleados y sus jefes**  
Tienes una lista de empleados donde **algunos empleados son jefes de otros empleados**.

📌 **Datos:**
#### **Tabla `Empleados`**

|id|nombre|jefe_id|
|---|---|---|
|1|Carlos|NULL|
|2|Ana|1|
|3|Pedro|1|
|4|Luis|2|

📌 **Consulta con `SELF JOIN`**

```sql
SELECT e1.nombre AS Empleado, e2.nombre AS Jefe 
FROM Empleados e1 
JOIN Empleados e2 ON e1.jefe_id = e2.id;
```

📌 **Resultado:**

|Empleado|Jefe|
|---|---|
|Ana|Carlos|
|Pedro|Carlos|
|Luis|Ana|

✅ **Ana y Pedro trabajan bajo Carlos.**  
✅ **Luis trabaja bajo Ana.**  
✅ **Carlos no aparece como empleado porque él no tiene jefe (`NULL`).**

### 📌 **¿Cuándo se usa en la vida real?**

✔️ Para encontrar **relaciones entre empleados y jefes** en una empresa.  
✔️ Para buscar **productos relacionados** (ej. productos que tienen el mismo precio o categoría).  
✔️ Para analizar **amistades en redes sociales** (ej. quién sigue a quién en Instagram).

---

### **📌 Resumen**

|`JOIN`|¿Qué hace?|
|---|---|
|**INNER JOIN**|Solo muestra coincidencias entre ambas tablas|
|**LEFT JOIN**|Muestra todo de la izquierda y las coincidencias de la derecha|
|**RIGHT JOIN**|Muestra todo de la derecha y las coincidencias de la izquierda|
|**FULL OUTER JOIN**|Muestra todo de ambas tablas, con `NULL` donde no hay coincidencias|
|**CROSS JOIN**|Hace todas las combinaciones posibles entre las dos tablas|
|**SELF JOIN**|Une una tabla consigo misma para relaciones jerárquicas o relacionadas|

### **📌 Resumen con ejemplos

| `JOIN`              | Explicación                                             | Ejemplo                                                |
| ------------------- | ------------------------------------------------------- | ------------------------------------------------------ |
| **INNER JOIN**      | Solo coincidencias                                      | Frutas que tienen color asignado                       |
| **LEFT JOIN**       | Todas las frutas, colores si existen                    | Todas las frutas, `NULL` si no tienen color            |
| **RIGHT JOIN**      | Todos los colores, frutas si existen                    | Todos los colores, `NULL` si no hay fruta de ese color |
| **FULL OUTER JOIN** | Unir dos listas, incluso si hay datos sin coincidencias | Ver clientes sin pedidos y pedidos sin clientes        |
| **CROSS JOIN**      | Crear todas las combinaciones posibles                  | Generar todas las combinaciones de comida y bebida     |
| **SELF JOIN**       | Comparar datos dentro de la misma tabla                 | Ver empleados y sus jefes en una empresa               |


---

# 3. DUDAS FRECUENTES

#### **¿Las consultas con JOIN modifica las tablas existentes?**

Los `JOIN` en SQL **no modifican las tablas**, solo sirven para **combinar y visualizar** los datos de manera temporal en los resultados de una consulta.

### 🔍 **¿Qué significa esto?**

Cuando usas `JOIN`, los datos de las tablas se combinan **en la consulta**, pero **las tablas originales siguen intactas**.

---

### **Ejemplo práctico**

Supongamos que tienes estas dos tablas:

#### **Tabla `Clientes`**

|id|nombre|
|---|---|
|1|Ana|
|2|Juan|
|3|Pedro|

#### **Tabla `Pedidos`**

|id_pedido|cliente_id|producto|
|---|---|---|
|101|1|Camiseta|
|102|2|Zapatos|
|103|1|Pantalón|

---

### **Consulta con `JOIN`**

```sql
SELECT Clientes.nombre, Pedidos.producto
FROM Clientes
JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

### **Resultado (vista temporal)**

|nombre|producto|
|---|---|
|Ana|Camiseta|
|Ana|Pantalón|
|Juan|Zapatos|

✅ **IMPORTANTE:**  
**Las tablas originales `Clientes` y `Pedidos` NO se modifican.**  
El `JOIN` solo crea un resultado basado en la consulta.

---

### **¿Qué pasaría si quiero modificar los datos?**

Para modificar los datos en la base de datos, necesitarías usar comandos como:

- `UPDATE` → Para modificar datos.
- `INSERT` → Para agregar datos.
- `DELETE` → Para eliminar datos.

Ejemplo:

```sql
UPDATE Clientes
SET nombre = 'Carlos'
WHERE id = 1;
```

👆 **Esto sí cambia la tabla real.**

Si solo usas `JOIN`, **no estás cambiando nada**, solo estás viendo una combinación de los datos.

---

### **Conclusión**

❌ `JOIN` **no modifica las tablas**.  
✅ `JOIN` **solo une los datos para visualizarlos en la consulta**.  
❗ Para hacer cambios en la base de datos, debes usar `UPDATE`, `INSERT` o `DELETE`.


Enlaces de interés:
- [w3schools](https://www.w3schools.com/sql/sql_join.asp)
- [mysql - join clause](https://dev.mysql.com/doc/refman/8.4/en/join.html)
- [tutorial-uniones-join](https://www.freecodecamp.org/espanol/news/tutorial-de-uniones-en-sql/)

