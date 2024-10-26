# Conceptos Básicos de HTML

HTML (HyperText Markup Language) es el lenguaje fundamental utilizado para crear páginas web. A continuación, exploraremos en profundidad los conceptos esenciales de HTML y cómo se aplican en la construcción de sitios web.

## Encabezados en HTML

Los encabezados son elementos clave para estructurar y organizar una página web. HTML ofrece seis niveles de encabezados, desde `<h1>` hasta `<h6>`, donde `<h1>` es el encabezado principal y `<h6>` es el menos importante. Los encabezados no solo proporcionan formato, sino que también transmiten la jerarquía del contenido en una página. Esto es crucial para la accesibilidad y el SEO, ya que los motores de búsqueda utilizan estos encabezados para entender la estructura y la importancia del contenido.

### Ejemplo:

```html
<h1>Encabezado Principal</h1>
<h2>Subencabezado 1</h2>
<h2>Subencabezado 2</h2>
<h3>Subencabezado 2.1</h3>
```

## Párrafos en HTML

Los párrafos se utilizan para dividir el contenido textual en fragmentos coherentes y legibles. La etiqueta `<p>` se emplea para crear párrafos. Además de la presentación, los párrafos son esenciales para la comprensión del contenido y la navegación. A menudo se utilizan en conjunto con otros elementos HTML para formatear y estructurar el texto.

### Ejemplo:

```html
<p>Este es un párrafo de ejemplo que contiene texto legible.</p>
<p>
  Este es otro párrafo que sigue al anterior, permitiendo una presentación
  organizada del contenido.
</p>
```

## Etiquetas de Formato de Texto en HTML

Las etiquetas de formato de texto son fundamentales para dar estilo al texto en una página web. Las más comunes incluyen:

- `<strong>`: Para texto en negrita, indicando énfasis en el contenido.
- `<em`>: Para texto en cursiva, utilizado para resaltar un texto con énfasis adicional.
- `<u>`: Para subrayar texto, que a menudo indica que el texto es un enlace.
- `<s>`: Para aplicar un tachado al texto, que a veces se usa para marcar texto obsoleto.
- `<mark>`: Para resaltar texto con un fondo de color amarillo.
- `<q>`: Para texto en una cita en línea, con comillas.
- `<sup>`: Para texto en superíndice, útil para exponentes y notas al pie.
- `<sub>`: Para texto en subíndice, comúnmente utilizado en fórmulas químicas y ecuaciones.

Estas etiquetas mejoran la legibilidad y presentación del contenido, permitiendo una comunicación más efectiva con los visitantes de la página.

### Ejemplo:

```html
<p>
  El uso de <strong>etiquetas de formato de texto</strong> es esencial para
  mejorar la <em>legibilidad</em> del contenido y proporcionar <u>énfasis</u> en
  partes específicas. Incluso puedes <s>marcar texto obsoleto</s> y
  <mark>resaltar información clave</mark>. Además, puedes citar texto en línea
  con <q>citas</q> o agregar números <sup>superíndices</sup> y fórmulas químicas
  con <sub>subíndices</sub>.
</p>
```

Así se verá:

<p>El uso de <strong>etiquetas de formato de texto</strong> es esencial para mejorar la <em>legibilidad</em> del contenido y proporcionar <u>énfasis</u> en partes específicas. Incluso puedes <s>marcar texto obsoleto</s> y <mark>resaltar información clave</mark>. Además, puedes citar texto en línea con <q>citas</q> o agregar números <sup>superíndices</sup> y fórmulas químicas con <sub>subíndices</sub>.</p>

## Listas en HTML

Las listas son herramientas importantes para organizar y presentar información de manera estructurada en una página web. HTML admite dos tipos de listas:

### Listas Ordenadas (`<ol>`)

Las listas ordenadas se utilizan cuando se necesita presentar elementos en un orden específico. Los elementos de la lista se numeran secuencialmente, generalmente con números o letras.

### Ejemplo:

```html
<ol>
  <li>Elemento 1</li>
  <li>Elemento 2</li>
  <li>Elemento 3</li>
</ol>
```

Así se verá:

<ol>
    <li>Elemento 1</li>
    <li>Elemento 2</li>
    <li>Elemento 3</li>
</ol>

### Listas Desordenadas (`<ul>`)

Las listas desordenadas son adecuadas para elementos que no siguen un orden específico. Estos elementos se presentan con viñetas o símbolos.

### Ejemplo:

```html
<ul>
  <li>Elemento A</li>
  <li>Elemento B</li>
  <li>Elemento C</li>
</ul>
```

Así se verá:

<ul>
    <li>Elemento A</li>
    <li>Elemento B</li>
    <li>Elemento C</li>
</ul>

Las etiquetas `<li>` se utilizan para definir elementos individuales dentro de las listas.

## Enlaces, Imágenes, Vídeo y Audio en HTML

HTML permite la inclusión de elementos multimedia para enriquecer el contenido de una página web.

### Enlaces (`<a>`)

Los enlaces se utilizan para conectar una página web con otra. La etiqueta `<a>` se combina con el atributo href para especificar la dirección web a la que se enlaza.
Además, el atributo target permite definir si el enlace se abre en la misma ventana o en una nueva pestaña.

### Ejemplo:

```html
<a href="https://www.ejemplo.com" target="_blank">
  Este es un enlace a una página web de ejemplo
</a>
```

## Imágenes (`<img>`)

Las imágenes se utilizan para añadir contenido visual a una página web. La etiqueta `<img>` se combina con el atributo src para especificar la ubicación de la imagen. El atributo alt proporciona un texto alternativo que se muestra si la imagen no se carga y es esencial para la accesibilidad.

### Ejemplo:

```html
<img src="imagen.jpg" alt="Descripción de la imagen" />
```

## Vídeo (`<video>`) y Audio (`<audio>`)

Las etiquetas `<video>` y `<audio>` permiten incrustar contenido multimedia en una página web. Estas etiquetas se combinan con el atributo src para especificar la ubicación del archivo multimedia.

Además, los atributos controls y autoplay controlan la reproducción y visualización del contenido multimedia.

### Ejemplo:

```html
<video src="video.mp4" controls autoplay>
  Tu navegador no admite la reproducción de video.
</video>

<audio src="audio.mp3" controls autoplay>
  Tu navegador no admite la reproducción de audio.
</audio>
```

## Etiquetas Semánticas en HTML

Las etiquetas semánticas son cruciales para proporcionar información adicional sobre el contenido de una página. Ayudan a los motores de búsqueda y otros agentes a comprender la estructura y el propósito de cada elemento en la página.

### Ejemplos:

- `<header>`: Se utiliza para indicar el encabezado de una página web, que generalmente contiene el logotipo, el título y la navegación principal.
- `<nav>`: Indica un menú de navegación, lo que facilita la ubicación de las opciones de navegación.
- `<article>`: Define un artículo independiente o contenido autónomo, como un artículo de blog.
- `<section>`: Divide el contenido en secciones significativas, lo que permite una organización lógica.
- `<aside>`: Se utiliza para contenido secundario o complementario, como anuncios o notas.
- `<footer>`: Define el pie de página de una página web, que puede contener información de contacto o enlaces relacionados.

El uso de etiquetas semánticas es fundamental para mejorar la estructura y la accesibilidad de una página web.

## Formularios en HTML

Los formularios en HTML son una forma fundamental de interactuar con los usuarios y recopilar información. Los formularios se crean con la etiqueta `<form>`, que contiene elementos de formulario como `<input>`, `<select>`, `<textarea>` y `<button>`.

### Ejemplo:

```html
<form action="/procesar" method="post">
  <label for="nombre">Nombre:</label>
  <input type="text" id="nombre" name="nombre" required />

  <label for="correo">Correo Electrónico:</label>
  <input type="email" id="correo" name="correo" required />

  <label for="mensaje">Mensaje:</label>
  <textarea id="mensaje" name="mensaje" rows="4" required></textarea>

  <button type="submit">Enviar</button>
</form>
```

Los formularios pueden contener diversos tipos de campos, como campos de texto, contraseñas, direcciones de correo electrónico, números, fechas y más. Los atributos `required` y `placeholder` se pueden utilizar para garantizar que se proporcionen los datos necesarios y para proporcionar instrucciones adicionales a los usuarios.