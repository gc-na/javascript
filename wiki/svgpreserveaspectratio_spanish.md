<!--
Meta Description: # SVGPreserveAspectRatio: Controlando la Escala de Gráficos SVG en JavaScript ## Sinopsis `SVGPreserveAspectRatio` es una propiedad clave en el manejo...
Meta Keywords: svg, gráfico, para, contenedor, que
-->

# SVGPreserveAspectRatio: Controlando la Escala de Gráficos SVG en JavaScript

## Sinopsis
`SVGPreserveAspectRatio` es una propiedad clave en el manejo de gráficos SVG que se utiliza para controlar cómo se escalan y posicionan los gráficos dentro de su contenedor. Esta propiedad es fundamental al trabajar con gráficos vectoriales escalables en aplicaciones web, especialmente cuando se manipulan mediante JavaScript.

## Documentación
### Propósito
La propiedad `preserveAspectRatio` de SVG define cómo se debe escalar un gráfico SVG para ajustarse a un contenedor específico. Permite a los desarrolladores decidir si el aspecto del gráfico debe mantenerse o si debe ser distorsionado para llenar el área asignada.

### Uso
La propiedad se puede establecer en un elemento SVG utilizando atributos en el código SVG directamente o a través de JavaScript. Los valores comunes para `preserveAspectRatio` incluyen:

- `none`: El gráfico se escalará para llenar el contenedor sin mantener el aspecto.
- `xMinYMin`: El gráfico se alineará en la esquina superior izquierda, manteniendo su aspecto.
- `xMidYMid`: El gráfico se centrará en el contenedor, manteniendo su aspecto.
- `meet`: Escala el gráfico para que encaje dentro del contenedor, manteniendo el aspecto.
- `slice`: Escala el gráfico para que cubra completamente el contenedor, lo que puede recortar partes del gráfico.

### Detalles
La propiedad `preserveAspectRatio` se aplica a los elementos `<svg>` y se puede manipular mediante JavaScript para responder dinámicamente a cambios en el tamaño del contenedor. Para establecer o modificar esta propiedad, se puede utilizar la interfaz DOM de SVG.

```javascript
const svgElement = document.getElementById('miSVG');
svgElement.setAttribute('preserveAspectRatio', 'xMidYMid meet');
```

## Ejemplos
### Ejemplo básico de uso en SVG
```html
<svg width="200" height="200" preserveAspectRatio="xMidYMid meet">
  <circle cx="100" cy="100" r="80" fill="blue" />
</svg>
```

### Ejemplo de manipulación con JavaScript
```html
<svg id="miSVG" width="300" height="300">
  <rect width="100%" height="100%" fill="red" />
</svg>

<script>
  const svgElement = document.getElementById('miSVG');
  svgElement.setAttribute('preserveAspectRatio', 'none');
</script>
```

## Explicación
Uno de los errores comunes al usar `preserveAspectRatio` es no considerar el tamaño del contenedor en relación con el tamaño del gráfico. Si el contenedor es significativamente más pequeño o más grande que el gráfico, se pueden producir distorsiones o recortes inesperados. Además, al utilizar valores como `slice`, es importante tener en cuenta que partes del gráfico pueden quedar fuera de la vista.

Es recomendable hacer pruebas visuales en diferentes resoluciones y tamaños de pantalla para asegurarse de que el comportamiento sea el esperado.

## Resumen en una línea
`SVGPreserveAspectRatio` permite controlar cómo se escalan los gráficos SVG en su contenedor, asegurando que el aspecto se mantenga o se ajuste según las necesidades de diseño.