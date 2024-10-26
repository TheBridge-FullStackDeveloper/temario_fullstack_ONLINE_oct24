# Conceptos Básicos de CSS

**CSS**, que significa "Cascading Style Sheets" en inglés, es un lenguaje de hojas de estilo utilizado para definir la presentación y el diseño de documentos HTML (y otros tipos de documentos XML). CSS separa la estructura y el contenido de un documento HTML de su estilo visual, permitiendo a los diseñadores y desarrolladores web controlar la apariencia y el formato de una página web de manera más eficiente.

En resumen, **CSS** se utiliza para:

1. **Estilizar elementos HTML:** Permite definir cómo se ven elementos como texto, imágenes, enlaces, formularios, botones y otros componentes de una página web.

2. **Controlar el diseño:** CSS permite controlar la disposición de elementos en una página, como la ubicación, el tamaño, los márgenes y los espaciados entre elementos.

3. **Hacer que las páginas sean responsivas:** CSS es esencial para crear diseños que se adapten a diferentes tamaños de pantalla, como en dispositivos móviles, tabletas y computadoras de escritorio.

4. **Mejorar la accesibilidad:** Al separar la presentación del contenido, CSS facilita la creación de sitios web más accesibles, lo que beneficia a usuarios con discapacidades visuales u otras necesidades especiales.

5. **Mantener un diseño coherente:** Al utilizar hojas de estilo CSS, es más sencillo mantener un diseño coherente en todo un sitio web, ya que los estilos se pueden aplicar de manera consistente a través de múltiples páginas.

En resumen, **CSS** es una herramienta esencial en el desarrollo web moderno que permite crear páginas web atractivas y funcionales al controlar su aspecto visual y diseño.

## Selectores en CSS

Los selectores en CSS son las reglas que utilizamos para seleccionar los elementos HTML que deseamos modificar. Los selectores permiten definir qué partes del documento HTML serán afectadas por las reglas de estilo. Aquí tienes una descripción de los selectores más comunes:

### 1. Selector por Nombre o Elemento

Este selector se utiliza para seleccionar todos los elementos con un nombre o tipo específico. Por ejemplo, si deseas aplicar un estilo a todos los elementos de tipo `<p>`, usarías:

```css
p {
  /* Estilo para párrafos */
}
```

### 2. Selector por Clase

El selector por clase se utiliza para seleccionar todos los elementos que tienen una clase específica. Las clases se aplican a elementos HTML para agruparlos y aplicarles un estilo común. Aquí tienes un ejemplo:

```css
.mi-clase {
  /* Estilo para elementos con la clase "mi-clase" */
}
```

### 3. Selector por ID

El selector por ID se utiliza para seleccionar un elemento HTML único que tiene un ID específico. Los IDs deben ser únicos en la página. Aquí tienes un ejemplo:

```css
#mi-id {
  /* Estilo para el elemento con el ID "mi-id" */
}
```

### 4. Selector por Atributo

Este selector se utiliza para seleccionar elementos que tienen un atributo específico. Puedes utilizar este tipo de selector para estilizar elementos con ciertos atributos personalizados. Ejemplo:

```css
[data-color="rojo"] {
  /* Estilo para elementos con el atributo "data-color" igual a "rojo" */
}
```

## Modelo de cajas

El modelo de cajas es un concepto fundamental en CSS que describe cómo se representan los elementos HTML en la pantalla. Se divide en cuatro partes principales:

### 1. Contenido

El contenido es la parte real y visible del elemento, como el texto, las imágenes u otros elementos incrustados. Para controlar el tamaño del contenido, puedes usar las propiedades width y height.

```css
.box {
  width: 200px; /* Ancho de la caja */
  height: 100px; /* Alto de la caja */
}
```

### 2. Margen

El margen es el espacio que se encuentra alrededor del elemento y separa la caja de otros elementos. Puedes ajustar los márgenes usando la propiedad margin.

```css
.box {
  margin: 10px; /* Márgenes de 10 píxeles en todos los lados de la caja */
}
```

### 3. Relleno

El relleno es el espacio entre el contenido y el borde de la caja. Puedes controlar el relleno con la propiedad padding.

```css
.box {
  padding: 20px; /* Relleno de 20 píxeles en todos los lados del contenido */
}
```

### 4. Borde

El borde rodea la caja y puede tener un grosor, un estilo y un color definidos. Puedes utilizar la propiedad border para configurar el borde.

```css
.box {
  border: 2px solid #333; /* Borde de 2 píxeles de grosor, sólido y color #333 */
}
```

## Propiedades de Texto en CSS

Las propiedades de texto en CSS te permiten controlar cómo se muestra el texto en tus elementos HTML. Algunas propiedades comunes incluyen:

- `font-family`: Define la fuente del texto.
- `font-size`: Establece el tamaño de la fuente.
- `font-weight`: Controla el grosor de la fuente (normal, negrita, etc.).
- `color`: Define el color del texto.

Ejemplo:

```css
.texto-destacado {
  font-family: "Arial", sans-serif;
  font-size: 18px;
  font-weight: bold;
  color: #ff5733;
}
```

## Flexbox

Flexbox es un modelo de diseño en CSS que simplifica la alineación y distribución de elementos en un contenedor, incluso cuando tienen tamaños variables. Para usar Flexbox, primero debes establecer un contenedor como un contenedor flexible utilizando la propiedad display: flex;. Luego, puedes controlar cómo se alinean y distribuyen los elementos hijos dentro de ese contenedor.

Ejemplo:

```css
.contenedor-flex {
  display: flex; /* Establece el contenedor como flexible */
  justify-content: space-between; /* Distribuye elementos con espacio entre ellos */
  align-items: center; /* Centra verticalmente los elementos en el contenedor */
}
```