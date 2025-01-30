
# 1. Instalación de MySQL y comprobación de versión:

Antes de comenzar, asegúrate de tener MySQL instalado en tu sistema. Puedes descargar e instalar MySQL desde el [sitio oficial de MySQL](https://dev.mysql.com/downloads/).

##### Instalación MySQL y Workbench

MySQL Server
Windows:    https://dev.mysql.com/downloads/installer/
	TIP: cuidado con la versión. 
	TIP: descargar el zip más pesado (es el ejecutable, además instala )
Mac:            https://dev.mysql.com/doc/refman/8.0/en/macos-installation-pkg.html

MySQL Workbench
https://dev.mysql.com/downloads/workbench/

Video instalación
https://www.youtube.com/watch?v=tAxTQoofbeM

---
##### Verificación

Puedes verificar si tienes MySQL instalado de la siguiente forma:

**A través de la línea de comandos:**
   - Abre la terminal (PowerShell) o el símbolo del sistema (cmd).
	   - Puedes hacerlo desde el buscador o con botón derecho de ratón sobre el escritorio.
   - Ejecuta el siguiente comando para verificar si MySQL está instalado:
```shell
mysql --version
```

**Nota**: Esto te mostrará la versión de MySQL instalada en tu sistema, si está presente.

Si MySQL no está instalado, recibirás un mensaje de error o una indicación de que el comando no se puede encontrar. Si está instalado, verás la versión en la salida del comando `mysql --version`

---

##### Nota Solución Error 

El error "mysql no se reconoce como un comando" en el símbolo del sistema (cmd) indica que el ejecutable de MySQL no está en la ruta del sistema o no se ha configurado correctamente.

Para solucionar esto, puedes seguir estos pasos:

1. **Añadir MySQL a la Ruta del Sistema:**
   - Busca la ubicación del ejecutable de MySQL en tu sistema. Por lo general, podría estar en algo como `C:\Program Files\MySQL\MySQL Server X.X\bin`, donde `X.X` es la versión específica de MySQL.
   - Copia la ruta completa del directorio binario de MySQL.
   - Abre la configuración avanzada del sistema: 
	   - configuración > sistema > información > configuración avanzada > variables de entorno
	   - también puedes poner en el buscador "variables de entorno" > hacer click en "editar las variables de entorno del sistema"
   - En la pestaña "Opciones avanzadas", haz clic en "Variables de entorno".
   - En la sección "Variables del USUARIO", selecciona la variable "Path" y haz clic en "Editar".  
	   - Nuevo > Agrega una nueva entrada y PEGA la ruta completa del directorio binario de MySQL. Ejemplo: `C:\Program Files\MySQL\MySQL Server X.X\bin`. Guarda / Acepta.
   - Si no tienes la variable "Path" tendrás que crearla:
	   - Nueva:
		   - Nombre de la:     Path
		   - Valor de la :         ``C:\Program Files\MySQL\MySQL Server 8.0\bin```
		   - Nota: sustituye el  `Valor de la `  por la ruta del del ejecutable de MySQL en tu sistema.
		   - Aceptar
   - En la sección "Variables del SISTEMA", selecciona la variable "Path" y haz clic en "Editar".
	   - Nuevo > Agrega una nueva entrada y PEGA a la ruta completa del directorio binario de MySQL. Guarda y cierra todas las ventanas.
-  Si no tienes la variable "Path" tendrás que crearla:
	   - Nueva:
		   - Nombre de la:     Path
		   - Valor de la :         `C:\Program Files\MySQL\MySQL Server 8.025\bin
		   - Nota: sustituye el  `Valor de la `  por la ruta del del ejecutable de MySQL en tu sistema.
		   - Aceptar todas las ventanas relacionadas y cerrar
			
		![[variables-entorno-myslq.png]]

2. **Reiniciar la Consola o cmd:**
   - Si la consola de comandos ya está abierta, ciérrala y ábrela de nuevo. Esto asegura que los cambios en la ruta se tomen en cuenta.

3. **Verificar la Instalación:**
   - Abre una nueva ventana de la consola de comandos y prueba `mysql --version` nuevamente.

4. **Verificar la Instalación de MySQL:**
   - Asegúrate de que MySQL esté instalado correctamente y que el servicio esté en ejecución. Puedes verificar esto desde el Panel de control -> Herramientas administrativas -> Servicios.

Si después de estos pasos aún encuentras problemas, podría ser útil reinstalar MySQL y asegurarte de seleccionar la opción durante la instalación que agrega MySQL a la ruta del sistema.
