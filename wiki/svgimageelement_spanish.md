<!--
Meta Description: # SVGImageElement en JavaScript: Manipulación de Imágenes SVG en el DOM ## Sinopsis `SVGImageElement` es un interfaz que representa un elemento `<imag...
Meta Keywords: image, svg, setattribute, imagen, svgimageelement
-->

# SVGImageElement en JavaScript: Manipulación de Imágenes SVG en el DOM

## Sinopsis
`SVGImageElement` es un interfaz que representa un elemento `<image>` dentro de un SVG (Scalable Vector Graphics), permitiendo la manipulación de imágenes rasterizadas dentro de un contexto SVG a través de JavaScript.

## Documentación

### Propósito
El `SVGImageElement` se utiliza para incluir imágenes rasterizadas en gráficos SVG. A través de esta interfaz, los desarrolladores pueden acceder y modificar atributos de imágenes en SVG, como la fuente, la posición y el tamaño.

### Uso
El elemento `<image>` se define en un SVG y puede ser manipulado utilizando JavaScript. Este elemento se puede crear dinámicamente o modificar uno existente en el DOM.

#### Creación de un SVGImageElement
Para crear un `SVGImageElement`, se puede usar el método `createElementNS` del documento:

```javascript
const svgNS = "http://www.w3.org/2000/svg";
const image = document.createElementNS(svgNS, "image");
image.setAttribute("href", "ruta/a/la/imagen.png");
image.setAttribute("x", "10");
image.setAttribute("y", "10");
image.setAttribute("width", "100");
image.setAttribute("height", "100");
```

### Atributos Comunes
- **href**: La URL de la imagen que se va a mostrar.
- **x**: La posición horizontal de la imagen dentro del SVG.
- **y**: La posición vertical de la imagen dentro del SVG.
- **width**: El ancho de la imagen.
- **height**: La altura de la imagen.

## Ejemplos

### Ejemplo 1: Crear y agregar un SVGImageElement
```javascript
const svg = document.getElementById("miSVG");
const image = document.createElementNS(svgNS, "image");
image.setAttribute("href", "imagen.png");
image.setAttribute("x", "0");
image.setAttribute("y", "0");
image.setAttribute("width", "100");
image.setAttribute("height", "100");
svg.appendChild(image);
```

### Ejemplo 2: Modificar un SVGImageElement existente
```javascript
const existingImage = document.querySelector("image");
existingImage.setAttribute("href", "nueva_imagen.png");
existingImage.setAttribute("width", "150");
existingImage.setAttribute("height", "150");
```

## Explicación
Al trabajar con `SVGImageElement`, es importante tener en cuenta que:
- Asegúrate de que la URL de la imagen sea accesible para evitar que no se muestre.
- Ten en cuenta el contexto de la visualización SVG, ya que el tamaño y la posición de la imagen se basan en el espacio de coordenadas SVG.
- La carga asíncrona de la imagen puede causar problemas si intentas manipular el elemento antes de que se cargue completamente.

## Resumen en una línea
`SVGImageElement` permite la inclusión y manipulación de imágenes rasterizadas dentro de gráficos SVG utilizando JavaScript.