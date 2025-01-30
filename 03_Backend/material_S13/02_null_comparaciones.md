# Diferencia entre `= NULL` y `IS NULL`

n **MySQL**, comparar un valor con `NULL` usando el operador `=` (o `!=`) **no funciona** como lo haría con otros valores. Esto se debe a cómo MySQL maneja el valor especial `NULL`.

### Diferencia entre `= NULL` y `IS NULL`

1. **`= NULL` no funciona**:
    
    - Cuando usas `edad = NULL`, MySQL no puede evaluar esta condición porque `NULL` representa un valor desconocido.
    - Según las reglas de SQL, cualquier comparación con `NULL` (usando `=` o `!=`) siempre resulta en `FALSE` o `UNKNOWN`.
    
    ```sql
    --Ejemplo:--
    SELECT * FROM usuarios_lenguajes WHERE edad = NULL;
    ```
    
    Esto **no devolverá resultados**, incluso si hay filas donde `edad` es `NULL`.
    
2. **`IS NULL` funciona**:
    
    - La condición `IS NULL` es la forma correcta de verificar si un campo tiene el valor `NULL`.
    - Específicamente evalúa si un campo es `NULL`.
    
    ```sql
	--Ejemplo:--
    SELECT * FROM usuarios_lenguajes WHERE edad IS NULL;
    ```
    
    Esto devolverá todas las filas donde el valor de `edad` es `NULL`.
    
### Ejemplo práctico

|id|nombre|edad|
|---|---|---|
|1|Juan|25|
|2|María|NULL|
|3|Ana|30|

```sql
    --Si consultas:--
    SELECT * FROM usuarios_lenguajes WHERE edad = NULL;
```
    
No devolverá resultados, porque `= NULL` no evalúa correctamente.
    
```sql
    --Si consultas:--
    SELECT * FROM usuarios_lenguajes WHERE edad IS NULL;
```
    
Devolverá la fila con `María`, ya que su campo `edad` es `NULL`.
    
### Conclusión

Usa `IS NULL` para verificar si un valor es `NULL`. 
Usa `IS NOT NULL` para verificar si un valor **no** es `NULL`.
