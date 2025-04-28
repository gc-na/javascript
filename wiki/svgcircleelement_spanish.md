<!--
Meta Description: # SVGCircleElement: Manipulación de Círculos en SVG con JavaScript ## Sinopsis El `SVGCircleElement` es una interfaz de JavaScript que representa un e...
Meta Keywords: circle, svg, círculo, del, setattribute
-->

# SVGCircleElement: Manipulación de Círculos en SVG con JavaScript

## Sinopsis
El `SVGCircleElement` es una interfaz de JavaScript que representa un elemento `<circle>` en un documento SVG (Scalable Vector Graphics). Permite a los desarrolladores manipular propiedades de círculos, como su posición, radio y estilo, facilitando gráficos vectoriales dinámicos en aplicaciones web.

## Documentación
### Propósito
`SVGCircleElement` es utilizado para crear y manipular círculos dentro de un SVG. Este elemento es esencial para cualquier gráfico que requiera la representación de círculos, desde gráficos simples hasta complejas visualizaciones de datos.

### Uso
Para utilizar `SVGCircleElement`, primero se debe crear un elemento SVG en el documento HTML. Luego, se pueden utilizar métodos y propiedades de `SVGCircleElement` para modificar sus atributos.

#### Creación de un círculo
```javascript
let svgNamespace = "http://www.w3.org/2000/svg";
let circle = document.createElementNS(svgNamespace, "circle");

circle.setAttribute("cx", "50"); // Posición X del centro
circle.setAttribute("cy", "50"); // Posición Y del centro
circle.setAttribute("r", "40");   // Radio
circle.setAttribute("fill", "red"); // Color de relleno

let svg = document.querySelector("svg");
svg.appendChild(circle);
```

### Propiedades
- `cx`: Establece o devuelve la posición X del centro del círculo.
- `cy`: Establece o devuelve la posición Y del centro del círculo.
- `r`: Establece o devuelve el radio del círculo.
- `fill`: Establece o devuelve el color de relleno del círculo.

### Métodos
- `getBBox()`: Devuelve las coordenadas del marco delimitador del círculo.
- `setAttribute()`: Permite modificar los atributos del círculo.

## Ejemplos
### Ejemplo 1: Crear y mostrar un círculo
```html
<svg width="100" height="100">
</svg>

<script>
let svgNamespace = "http://www.w3.org/2000/svg";
let circle = document.createElementNS(svgNamespace, "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "30");
circle.setAttribute("fill", "blue");

document.querySelector("svg").appendChild(circle);
</script>
```

### Ejemplo 2: Cambiar el radio de un círculo existente
```javascript
let existingCircle = document.querySelector("circle");
existingCircle.setAttribute("r", "20");
```

## Explicación
Al trabajar con `SVGCircleElement`, es importante notar que los valores de los atributos `cx`, `cy`, y `r` deben ser números y deben ser establecidos antes de añadir el círculo al DOM para evitar errores de visualización. Además, si se intenta manipular un círculo que no ha sido correctamente creado o añadido, se generará un error en la consola.

Una de las trampas comunes es olvidar incluir el espacio de nombres SVG al crear el elemento, lo que resultará en que el círculo no se renderice correctamente. Siempre se debe usar `document.createElementNS()` para crear elementos SVG.

## Resumen en una frase
`SVGCircleElement` permite la creación y manipulación de círculos en documentos SVG mediante JavaScript, facilitando la representación visual de datos en la web.