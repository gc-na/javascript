<!--
Meta Description: # SVGAnimatedNumberList: Manipulación de Listas de Números Animados en JavaScript ## Sinopsis SVGAnimatedNumberList es una interfaz en JavaScript que ...
Meta Keywords: que, setattribute, svganimatednumberlist, circle, números
-->

# SVGAnimatedNumberList: Manipulación de Listas de Números Animados en JavaScript

## Sinopsis
SVGAnimatedNumberList es una interfaz en JavaScript que permite manejar listas de números animados en gráficos SVG, facilitando la creación de animaciones fluidas y dinámicas en elementos gráficos.

## Documentación
### Propósito
SVGAnimatedNumberList se utiliza para representar una lista de números que pueden ser animados a través de SVG (Scalable Vector Graphics). Proporciona una manera de manipular atributos que pueden variar en el tiempo, lo que es especialmente útil en gráficos interactivos y animaciones.

### Uso
La interfaz SVGAnimatedNumberList consta de dos propiedades principales:

- **baseVal**: Esta propiedad contiene el valor base de la lista de números. Es un objeto de tipo `SVGNumberList` que se puede modificar para alterar la representación gráfica.
  
- **animVal**: Esta propiedad representa el valor actual animado de la lista. Aunque se puede leer, no se puede modificar directamente; en su lugar, su valor se actualiza a medida que se aplica la animación.

### Detalles
SVGAnimatedNumberList es comúnmente utilizado en elementos SVG como `<animate>` y `<animateTransform>`. Se puede emplear en gráficos vectoriales escalables que requieren cambios dinámicos en sus propiedades numéricas.

## Ejemplos

### Ejemplo 1: Crear una lista de números animados
```javascript
// Crear un SVG y un elemento de círculo
const svgNS = "http://www.w3.org/2000/svg";
const circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "40");
circle.setAttribute("fill", "red");

// Agregar el círculo al documento
document.body.appendChild(circle);

// Definir una animación que cambie el radio del círculo
const animateRadius = document.createElementNS(svgNS, "animate");
animateRadius.setAttribute("attributeName", "r");
animateRadius.setAttribute("from", "40");
animateRadius.setAttribute("to", "80");
animateRadius.setAttribute("dur", "1s");
animateRadius.setAttribute("repeatCount", "indefinite");

// Agregar la animación al círculo
circle.appendChild(animateRadius);
```

### Ejemplo 2: Acceder a `baseVal` y `animVal`
```javascript
const animatedList = new SVGAnimatedNumberList();
animatedList.baseVal.appendItem(new SVGNumber(10));
animatedList.baseVal.appendItem(new SVGNumber(20));

// Leer los valores
console.log(animatedList.baseVal.getItem(0).value); // Salida: 10
console.log(animatedList.animVal.getItem(1).value); // Salida: 20 (valor animado)
```

## Explicación
Al trabajar con SVGAnimatedNumberList, es importante recordar que:

- La propiedad `animVal` no se puede modificar directamente. Cualquier cambio en los valores animados debe hacerse a través de la animación misma.
- La manipulación de listas de números puede ser un poco confusa, especialmente cuando se trata de añadir o eliminar elementos. Asegúrate de utilizar métodos como `appendItem` y `removeItem` adecuadamente.
- La compatibilidad con navegadores puede variar, así que es recomendable probar en diferentes entornos para asegurar una experiencia de usuario consistente.

## Resumen en una línea
SVGAnimatedNumberList permite la manipulación de listas de números animados en SVG, facilitando la creación de animaciones dinámicas en JavaScript.