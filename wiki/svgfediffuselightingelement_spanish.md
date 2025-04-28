<!--
Meta Description: # SVGFEDiffuseLightingElement: Elemento de Iluminación Difusa en SVG para JavaScript ## Sinopsis El `SVGFEDiffuseLightingElement` es un componente SVG...
Meta Keywords: luz, svg, que, iluminación, efectos
-->

# SVGFEDiffuseLightingElement: Elemento de Iluminación Difusa en SVG para JavaScript

## Sinopsis
El `SVGFEDiffuseLightingElement` es un componente SVG utilizado para aplicar efectos de iluminación difusa a gráficos vectoriales escalables. Este elemento permite crear efectos de luz que simulan cómo la luz se dispersa sobre las superficies, mejorando el aspecto visual de las ilustraciones SVG en aplicaciones web.

## Documentación
El `SVGFEDiffuseLightingElement` se encuentra dentro del contexto de las primitivas de filtro SVG y se utiliza para generar efectos de iluminación difusa en elementos gráficos. Este elemento se puede manipular mediante JavaScript para crear efectos dinámicos en interfaces web.

### Propósito
El propósito principal de `SVGFEDiffuseLightingElement` es permitir a los desarrolladores aplicar efectos de luz sobre objetos SVG, lo que mejora la profundidad y la percepción visual de los elementos en el diseño gráfico.

### Uso
Para utilizar `SVGFEDiffuseLightingElement`, se debe incluir dentro de un filtro SVG. Aquí hay una estructura básica:

```html
<filter id="filtro-iluminacion">
    <feDiffuseLighting in="SourceGraphic" lighting-color="white" surfaceScale="5">
        <feDistantLight azimuth="45" elevation="55" />
    </feDiffuseLighting>
</filter>
```

En este ejemplo, el filtro aplica una iluminación difusa a la gráfica base (`SourceGraphic`) con un color de iluminación blanco y una escala de superficie de 5. La luz se establece a una dirección específica mediante `feDistantLight`.

### Atributos Clave
- `in`: Especifica la entrada del filtro, comúnmente `SourceGraphic`.
- `lighting-color`: Define el color de la luz que se aplica.
- `surfaceScale`: Controla la escala de la superficie iluminada.
- `feDistantLight`: Define la dirección de la luz. Los atributos `azimuth` y `elevation` determinan la posición de la luz.

## Ejemplos
### Ejemplo Básico
```html
<svg width="200" height="200">
    <defs>
        <filter id="iluminacion">
            <feDiffuseLighting in="SourceGraphic" lighting-color="yellow" surfaceScale="3">
                <feDistantLight azimuth="135" elevation="45" />
            </feDiffuseLighting>
        </filter>
    </defs>
    <rect x="10" y="10" width="180" height="180" fill="blue" filter="url(#iluminacion)" />
</svg>
```
En este ejemplo, se aplica un filtro de iluminación difusa a un rectángulo azul, creando un efecto luminoso amarillo.

### Ejemplo con Interacción JavaScript
```html
<svg width="300" height="300" id="miSVG">
    <defs>
        <filter id="iluminacion">
            <feDiffuseLighting in="SourceGraphic" lighting-color="white" surfaceScale="5">
                <feDistantLight id="luz" azimuth="0" elevation="45" />
            </feDiffuseLighting>
        </filter>
    </defs>
    <circle cx="150" cy="150" r="100" fill="red" filter="url(#iluminacion)" />
</svg>
<script>
    const luz = document.getElementById('luz');
    luz.setAttribute('azimuth', '90'); // Cambiando la dirección de la luz
</script>
```
Este ejemplo permite cambiar la dirección de la luz mediante JavaScript, lo que proporciona una interacción dinámica.

## Explicación
Uno de los errores comunes al trabajar con `SVGFEDiffuseLightingElement` es no establecer correctamente el atributo `in`. Asegúrese de que esté configurado en relación con la fuente gráfica que desea iluminar. Además, el uso de colores de iluminación inadecuados o la escala de superficie incorrecta puede resultar en efectos visuales poco atractivos.

Es importante también tener en cuenta que la renderización de estos efectos puede variar entre diferentes navegadores, así que siempre es recomendable probar en múltiples entornos para asegurar la compatibilidad y la calidad visual.

## Resumen en Una Línea
`SVGFEDiffuseLightingElement` es un componente SVG que permite aplicar efectos de iluminación difusa a gráficos vectoriales en JavaScript, mejorando la experiencia visual en aplicaciones web.