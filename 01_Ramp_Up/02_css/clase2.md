# Conceptos Básicos de CSS

## Transformaciones en CSS

La propiedad `transform` en CSS permite aplicar transformaciones geométricas a los elementos HTML. Estas transformaciones se utilizan para mover, escalar, rotar o distorsionar los elementos, lo que es especialmente útil para lograr efectos visuales dinámicos en una página web.

### Propiedades Comunes de Transformación

Las propiedades más comunes que se pueden utilizar con `transform` son:

- `translate`: Mueve el elemento a lo largo de los ejes x, y o z.
- `scale`: Escala el elemento a un factor especificado.
- `rotate`: Rota el elemento en un ángulo especificado.
- `skew`: Distorsiona el elemento en un ángulo especificado.

## Ejemplos

### Ejemplo 1: Translate

```css
/* Mueve el elemento 50px hacia la derecha y 20px hacia abajo */
.transformed-element {
  transform: translate(50px, 20px);
}
```

### Ejemplo 2: Scale

```css
/* Escala el elemento al doble de su tamaño original */
.transformed-element {
  transform: scale(2);
}
```

### Ejemplo 3: Rotate

```css
/* Rota el elemento 45 grados en sentido horario */
.transformed-element {
  transform: rotate(45deg);
}
```

### Ejemplo 4: Skew

```css
/* Distorsiona el elemento en el eje x */
.transformed-element {
  transform: skewX(30deg);
}
```

## Transiciones en CSS

Las transiciones son un tipo de animación CSS que permite aplicar cambios graduales a las propiedades CSS de un elemento. Estas transiciones se utilizan para crear efectos suaves, como la aparición, la desaparición o el cambio de tamaño de un elemento, proporcionando una experiencia de usuario más atractiva.

### Propiedades de Transición

Para utilizar transiciones, debes definir algunas propiedades clave:

- `transition-property`: Especifica las propiedades CSS que se cambiarán durante la transición. Puedes elegir una o varias propiedades separadas por comas.
- `transition-duration`: Indica la duración de la transición en segundos o milisegundos.
- `transition-timing-function`: Define la función de tiempo que se utilizará para la transición, lo que afecta la velocidad del cambio. Las funciones comunes incluyen `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out` y más.

### Ejemplo

A continuación, se muestra un ejemplo de cómo aplicar una transición a un botón que cambia de color al pasar el cursor sobre él:

```css
/* Aplicar una transición al color de fondo del botón */
.button {
  background-color: #3498db;
  transition-property: background-color;
  transition-duration: 0.5s;
  transition-timing-function: ease;
}

/* Cambiar el color de fondo al pasar el cursor sobre el botón */
.button:hover {
  background-color: #e74c3c;
}
```

En este ejemplo, cuando el cursor se posa sobre el botón, la propiedad background-color cambia gradualmente durante 0.5 segundos con una función de tiempo "ease", creando una transición suave.

## Animaciones en CSS

Las animaciones son una forma avanzada de crear efectos dinámicos y complejos en una página web utilizando CSS. Estas animaciones permiten combinar transiciones y transformaciones para lograr resultados visuales atractivos, como la apertura de un menú, el movimiento de un personaje o cualquier otra acción animada.

### Propiedades de Animación

Para utilizar animaciones, es necesario definir varias propiedades clave:

- `animation-name`: Especifica el nombre de la animación que se aplicará al elemento. El nombre de la animación se corresponde con una serie de reglas de animación definidas en tu hoja de estilos.
- `animation-duration`: Indica la duración de la animación en segundos o milisegundos.
- `animation-timing-function`: Define la función de tiempo que se utilizará para la animación, lo que afecta la velocidad del cambio.
- `animation-delay`: Especifica la demora antes de que comience la animación.

### Ejemplo

A continuación, se muestra un ejemplo simple de cómo definir y aplicar una animación en CSS:

```css
/* Definir una animación llamada "desvanecer" */
@keyframes desvanecer {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

/* Aplicar la animación al elemento "caja" */
.caja {
  animation-name: desvanecer;
  animation-duration: 2s;
  animation-timing-function: ease;
  animation-delay: 1s;
}
```

En este ejemplo, hemos definido una animación llamada "desvanecer" que cambia gradualmente la opacidad de 1 (completamente visible) a 0 (invisible). Luego, aplicamos esta animación a un elemento con la clase "caja" con una duración de 2 segundos, una función de tiempo "ease" y una demora de 1 segundo.

## Media Queries (Mobile First) en CSS

Las Media Queries son una característica esencial de CSS que permite adaptar el diseño de una página web a diferentes dispositivos y resoluciones, lo que es crucial para crear sitios web responsivos. La idea principal detrás de las Media Queries es que tu diseño se adapte primero a dispositivos móviles y luego, si es necesario, se realicen ajustes para dispositivos de pantalla más grandes.

### Sintaxis de Media Queries

La sintaxis básica de una Media Query es la siguiente:

```css
@media [tipo de medio] [condiciones] {
  /* Reglas CSS que se aplicarán si las condiciones se cumplen */
}
```

### Algunos conceptos clave

- **[tipo de medio]**: Especifica el tipo de medio al que se aplica la regla. Algunos tipos de medios comunes son:

  - `screen`: Se aplica a dispositivos de pantalla, como computadoras, teléfonos y tabletas.
  - `print`: Se aplica a documentos impresos.
  - `speech`: Se aplica a dispositivos de voz.
  - `all`: Se aplica a todos los dispositivos (valor por defecto).

- **[condiciones]**: Define las condiciones bajo las cuales se aplicarán las reglas CSS. Estas condiciones pueden basarse en factores como el ancho de la pantalla, la orientación, la resolución y más.

### Ejemplo de Media Query

Aquí hay un ejemplo de una Media Query que aplica reglas CSS específicas cuando la pantalla tiene un ancho máximo de 600 píxeles, lo que es común en dispositivos móviles:

```css
@media screen and (max-width: 600px) {
  /* Reglas CSS para dispositivos con una pantalla de ancho máximo de 600px */
  body {
    font-size: 16px;
  }
  .menu {
    display: none;
  }
}
```

En este ejemplo, las reglas CSS dentro de la Media Query se aplicarán solo a dispositivos de pantalla (screen) con un ancho máximo de 600 píxeles.

### Enfoque "Mobile First"

El enfoque "Mobile First" es una estrategia recomendada en el diseño web, donde se comienza diseñando para dispositivos móviles y luego se agregan estilos para dispositivos más grandes. Esto garantiza que tu sitio web sea amigable para dispositivos móviles desde el principio.