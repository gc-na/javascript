<!--
Meta Description: # SVGLinearGradientElement en JavaScript: Guía Completa ## Sinopsis `SVGLinearGradientElement` es una interfaz del DOM SVG que representa un elemento ...
Meta Keywords: stop, svg, 100, degradado, color
-->

# SVGLinearGradientElement en JavaScript: Guía Completa

## Sinopsis
`SVGLinearGradientElement` es una interfaz del DOM SVG que representa un elemento de degradado lineal en un gráfico vectorial escalable (SVG). Permite la creación de transiciones de color suaves a lo largo de una línea recta, añadiendo profundidad y atractivo visual a gráficos y diseños.

## Documentación
`SVGLinearGradientElement` se utiliza para definir degradados lineales en documentos SVG. Este elemento se puede usar en combinación con otras primitivas SVG, como rectangles, círculos y paths, para proporcionar efectos visuales más ricos. 

### Propósito
El propósito principal de `SVGLinearGradientElement` es proporcionar una forma de aplicar degradados lineales a los elementos SVG, lo que permite personalizar la apariencia visual de gráficos vectoriales.

### Uso
Para utilizar `SVGLinearGradientElement`, es necesario incluirlo dentro de un elemento `<defs>` en el SVG y luego referenciarlo en un elemento gráfico como un atributo `fill` o `stroke`. 

#### Ejemplo de estructura básica:
```xml
<svg width="200" height="200">
    <defs>
        <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
            <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
            <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
        </linearGradient>
    </defs>
    <rect width="200" height="200" fill="url(#grad1)" />
</svg>
```

### Atributos clave
- **id**: Identificador único del degradado.
- **x1, y1, x2, y2**: Coordenadas que definen la dirección del degradado.
- **stop**: Elementos hijos que definen los colores en el degradado.

## Ejemplos
### Ejemplo 1: Degradado Lineal Simple
```html
<svg width="300" height="100">
    <defs>
        <linearGradient id="simpleGradient" x1="0%" y1="0%" x2="100%" y2="0%">
            <stop offset="0%" style="stop-color:blue;stop-opacity:1" />
            <stop offset="100%" style="stop-color:green;stop-opacity:1" />
        </linearGradient>
    </defs>
    <rect width="300" height="100" fill="url(#simpleGradient)" />
</svg>
```

### Ejemplo 2: Degradado Lineal con múltiples colores
```html
<svg width="300" height="100">
    <defs>
        <linearGradient id="multiGradient" x1="0%" y1="0%" x2="100%" y2="0%">
            <stop offset="0%" style="stop-color:red;stop-opacity:1" />
            <stop offset="50%" style="stop-color:yellow;stop-opacity:1" />
            <stop offset="100%" style="stop-color:blue;stop-opacity:1" />
        </linearGradient>
    </defs>
    <rect width="300" height="100" fill="url(#multiGradient)" />
</svg>
```

## Explicación
Al trabajar con `SVGLinearGradientElement`, es importante tener en cuenta algunos puntos clave:

- **Coordenadas**: Los atributos `x1`, `y1`, `x2` y `y2` determinan la dirección del degradado. Valores incorrectos pueden llevar a resultados inesperados.
- **Compatibilidad**: Asegúrate de que el navegador que estés utilizando soporte SVG, ya que algunos navegadores más antiguos pueden tener problemas de visualización.
- **Referencias**: Al referenciar el degradado en otros elementos, el id debe coincidir exactamente, incluyendo mayúsculas y minúsculas.

## Resumen en una línea
`SVGLinearGradientElement` permite la creación de degradados lineales en SVG, mejorando la estética de gráficos vectoriales en aplicaciones web.