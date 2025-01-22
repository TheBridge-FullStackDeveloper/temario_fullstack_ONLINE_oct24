# 01 res.locals vs req

En Node.js, específicamente con el framework **Express**, `res.locals` es un objeto que se utiliza para almacenar información local para la respuesta que está siendo procesada. Los valores almacenados en `res.locals` están disponibles solo durante el ciclo de vida de una solicitud y no persisten en solicitudes posteriores.

### ¿Cuándo y cómo se usa `res.locals`?

1. **Pasar datos a vistas renderizadas**  
    Cuando se utiliza un motor de plantillas como **Pug**, **EJS** o **Handlebars**, `res.locals` permite pasar datos a la plantilla para que estén disponibles al renderizarla.
    
    ```javascript
    app.get('/profile', (req, res) => {
        res.locals.username = 'Ana Morales';
        res.locals.age = 30;
        res.render('profile'); // Estos datos estarán disponibles en la plantilla 'profile'
    });
    ```
    
2. **Compartir datos entre middlewares y rutas**  
    `res.locals` se puede usar para almacenar datos que un middleware genera o procesa, y que deben estar disponibles en la siguiente ruta o middleware.
    
    ```javascript
    app.use((req, res, next) => {
        res.locals.isLoggedIn = !!req.user; // Verifica si el usuario está autenticado
        next();
    });
    
    app.get('/dashboard', (req, res) => {
        if (res.locals.isLoggedIn) {
            res.render('dashboard');
        } else {
            res.redirect('/login');
        }
    });
    ```
    
3. **Customizar datos globales para todas las respuestas**  
    Se puede usar `res.locals` en un middleware global para definir datos que estarán disponibles en todas las rutas.
    
    ```javascript
    app.use((req, res, next) => {
        res.locals.appName = 'Mi Aplicación';
        res.locals.year = new Date().getFullYear();
        next();
    });
    ```
    
4. **Manejo de datos específicos del ciclo de vida de la solicitud**  
    Es útil para datos que no necesitan persistir más allá de la respuesta actual.
    
    ```javascript
    app.get('/settings', (req, res) => {
        res.locals.settings = { theme: 'dark', notifications: true };
        res.render('settings');
    });
    ```
    

### **Ventajas de usar `res.locals`**

- **Ciclo de vida limitado:** Los datos en `res.locals` existen solo durante la solicitud actual, lo que evita fugas de memoria.
- **Facilita la comunicación entre middlewares:** Puedes preparar datos en un middleware y utilizarlos en una ruta o en la vista.
- **Compatible con motores de plantillas:** Los datos en `res.locals` se pueden acceder directamente en las plantillas.

### **Diferencia entre `res.locals` y `req`**

- **`req`**: Se usa para almacenar datos relacionados con la solicitud (como parámetros, cuerpo o información de autenticación).
- **`res.locals`**: Se usa para almacenar datos relacionados con la respuesta que se está construyendo.

Usar `res.locals` es una práctica común para preparar datos de manera ordenada y clara dentro de un ciclo de solicitud-respuesta.