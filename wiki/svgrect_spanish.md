<!--
Meta Description: # SVGRect: Manipulación de Rectángulos SVG en JavaScript ## Sinopsis SVGRect es un objeto en JavaScript que representa un rectángulo en un gráfico SVG...
Meta Keywords: svg, svgrect, rect, que, rectángulo
-->

# SVGRect: Manipulación de Rectángulos SVG en JavaScript

## Sinopsis
SVGRect es un objeto en JavaScript que representa un rectángulo en un gráfico SVG (Scalable Vector Graphics). Proporciona propiedades y métodos que permiten definir y manipular rectángulos dentro de un contexto SVG, facilitando la creación de gráficos escalables en aplicaciones web.

## Documentación
### Propósito
SVGRect se utiliza para describir un rectángulo en un espacio SVG, permitiendo especificar su posición, dimensiones y otros atributos. Este objeto es fundamental para la manipulación de gráficos vectoriales en la web.

### Uso
El objeto SVGRect es comúnmente utilizado en conjunción con el método `getBBox()` de un elemento SVG, que devuelve un objeto SVGRect que describe la caja de delimitación del elemento.

### Propiedades
- **x**: Coordenada X de la esquina superior izquierda del rectángulo.
- **y**: Coordenada Y de la esquina superior izquierda del rectángulo.
- **width**: Ancho del rectángulo.
- **height**: Altura del rectángulo.
- **height**: (opcional) Altura del rectángulo.

### Métodos
Aunque SVGRect en sí no ofrece métodos directos, su uso se integra con otros métodos de manipulación de elementos SVG, permitiendo calcular y ajustar el tamaño y la posición de los elementos gráficos.

## Ejemplos
### Ejemplo 1: Creación de un rectángulo SVG
```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNamespace, "svg");
const rect = document.createElementNS(svgNamespace, "rect");

rect.setAttribute("x", 50);
rect.setAttribute("y", 50);
rect.setAttribute("width", 100);
rect.setAttribute("height", 100);
rect.setAttribute("fill", "blue");

svg.appendChild(rect);
document.body.appendChild(svg);
```

### Ejemplo 2: Obtener y usar las dimensiones de un SVGRect
```javascript
const bbox = rect.getBBox();
console.log(`Posición: (${bbox.x}, ${bbox.y}), Dimensiones: ${bbox.width}x${bbox.height}`);
```

## Explicación
Al trabajar con SVGRect, es importante tener en cuenta que las coordenadas y dimensiones se basan en el sistema de coordenadas del contenedor SVG. Además, los rectángulos pueden ser afectados por transformaciones aplicadas a sus elementos padres. Esto puede llevar a confusiones si no se comprenden bien los sistemas de coordenadas.

También es fundamental notar que el objeto SVGRect no se puede instanciar directamente; en su lugar, se obtiene a través de métodos como `getBBox()`, lo que puede ser un punto confuso para los principiantes.

## Resumen en una línea
SVGRect es un objeto en JavaScript que define y manipula rectángulos dentro de gráficos SVG, facilitando la creación de elementos gráficos escalables en la web.