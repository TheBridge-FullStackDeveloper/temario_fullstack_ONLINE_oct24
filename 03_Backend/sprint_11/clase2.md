# Scraping con JavaScript: Axios y Cheerio

El scraping con JavaScript se refiere a la extracción de datos de sitios web, y dos herramientas populares para facilitar esta tarea son Axios y Cheerio.

## Axios

Axios es una biblioteca basada en Promesas que permite realizar solicitudes HTTP de manera sencilla. Es especialmente útil para realizar peticiones a sitios web y obtener el HTML de las páginas que se desean analizar con Cheerio.

### Ejemplo de Uso de Axios:

```javascript
const axios = require("axios");

async function obtenerHTML(url) {
  try {
    const response = await axios.get(url);
    return response.data;
  } catch (error) {
    console.error("Error al obtener el HTML:", error.message);
    throw error;
  }
}

const urlEjemplo = "https://www.ejemplo.com";
obtenerHTML(urlEjemplo).then((html) => {
  console.log("HTML obtenido:", html);
});
```

En este ejemplo, la función `obtenerHTML` utiliza Axios para realizar una solicitud GET a una URL y devuelve el HTML de la respuesta.

## Cheerio

Cheerio es una biblioteca ligera y rápida que implementa un analizador y manipulador de HTML basado en jQuery. Permite navegar y manipular fácilmente el DOM de las páginas web, facilitando la extracción de datos.

### Ejemplo:

```javascript
const cheerio = require("cheerio");

function extraerDatos(html) {
  const $ = cheerio.load(html);

  // Ejemplo: Obtener el título de la página
  const titulo = $("title").text();
  console.log("Título de la página:", titulo);

  return { titulo };
}

const htmlEjemplo =
  "<html><head><title>Página de Ejemplo</title></head><body></body></html>";
const datosExtraidos = extraerDatos(htmlEjemplo);
console.log("Datos extraídos:", datosExtraidos);
```

En este ejemplo, la función `extraerDatos` utiliza Cheerio para cargar el HTML y acceder a elementos específicos, como el título de la página.

## Combinando Axios y Cheerio para Scraping

La combinación de Axios y Cheerio es común en proyectos de scraping. Axios se utiliza para obtener el HTML de la página web, y Cheerio se emplea para analizar y manipular ese HTML para extraer la información deseada.

```javascript
const axios = require("axios");
const cheerio = require("cheerio");

async function realizarScraping(url) {
  try {
    const html = await axios.get(url);
    const datosExtraidos = extraerDatos(html.data);
    console.log("Datos extraídos:", datosExtraidos);
  } catch (error) {
    console.error("Error en el scraping:", error.message);
  }
}

const urlScraping = "https://www.sitioaescrapear.com";
realizarScraping(urlScraping);
```

En este ejemplo, la función `realizarScraping` utiliza Axios para obtener el HTML de la página web y luego utiliza Cheerio para extraer datos específicos de esa página.