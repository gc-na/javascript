<!--
Meta Description: # SVGAnimatedLengthList: Manipulación de Listas de Longitudes Animadas en JavaScript ## Sinopsis SVGAnimatedLengthList es una interfaz en JavaScript q...
Meta Keywords: que, baseval, animación, longitudes, svganimatedlengthlist
-->

# SVGAnimatedLengthList: Manipulación de Listas de Longitudes Animadas en JavaScript

## Sinopsis
SVGAnimatedLengthList es una interfaz en JavaScript que permite manejar listas de longitudes animadas en gráficos SVG. Facilita la animación de propiedades de longitud, como el ancho y la altura, permitiendo una mayor interactividad y dinamismo en las representaciones gráficas.

## Documentación

### Propósito
SVGAnimatedLengthList es parte de la especificación SVG (Scalable Vector Graphics) y se utiliza para representar una lista de valores de longitud que pueden ser animados a lo largo del tiempo. Es especialmente útil en aplicaciones web donde se requieren gráficos vectoriales que cambian dinámicamente.

### Uso
La interfaz SVGAnimatedLengthList se utiliza comúnmente dentro de elementos SVG que tienen atributos de longitud que pueden ser animados, como `stroke-dasharray` y `points`. Proporciona dos propiedades principales:

- **baseVal**: Representa la lista de longitudes base. Esta propiedad puede ser leída y escrita.
- **animVal**: Representa la lista de longitudes animadas. Esta propiedad es solo de lectura y refleja el valor actual de la animación.

### Detalles
Ambas propiedades son instancias de `SVGLengthList`, que permite manipular los valores de longitud individuales. La diferencia clave entre `baseVal` y `animVal` radica en que `baseVal` se refiere al valor original del atributo antes de cualquier animación, mientras que `animVal` muestra el valor en el momento actual de la animación.

## Ejemplos

### Ejemplo 1: Acceso a baseVal y animVal
```javascript
const svgElement = document.getElementById('miSVGElemento');
const lengthList = svgElement.getAttribute('stroke-dasharray');

console.log(lengthList.baseVal);  // Muestra la lista de longitudes base
console.log(lengthList.animVal);   // Muestra la lista de longitudes animadas
```

### Ejemplo 2: Modificación de baseVal
```javascript
const svgElement = document.getElementById('miSVGElemento');
const lengthList = svgElement.getAttribute('stroke-dasharray');

// Modificando el valor de baseVal
lengthList.baseVal = "5 10 15";
console.log(lengthList.baseVal);  // Muestra "5 10 15"
```

## Explicación
Al trabajar con SVGAnimatedLengthList, es importante tener en cuenta que:

- La propiedad `animVal` solo refleja el estado actual de la animación y no puede ser modificada directamente. Cualquier cambio en la animación debe hacerse a través de la propiedad `baseVal`.
- Es fundamental verificar que el elemento SVG y sus atributos estén correctamente definidos y no sean nulos antes de intentar acceder o modificar sus valores.
- Las animaciones pueden ser afectadas por múltiples factores, como el tiempo de ejecución, el evento de inicio, y la duración de la animación, lo que puede llevar a resultados inesperados si no se manejan adecuadamente.

## Resumen en una línea
SVGAnimatedLengthList permite la manipulación y animación de listas de longitudes en elementos SVG utilizando JavaScript.