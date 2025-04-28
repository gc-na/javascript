<!--
Meta Description: # SVGNumberList en JavaScript: Manipulación de listas de números en SVG ## Sinopsis SVGNumberList es una interfaz que permite la manipulación de lista...
Meta Keywords: número, numberlist, números, svgnumberlist, svg
-->

# SVGNumberList en JavaScript: Manipulación de listas de números en SVG

## Sinopsis
SVGNumberList es una interfaz que permite la manipulación de listas de números en gráficos SVG (Scalable Vector Graphics) mediante JavaScript. Proporciona métodos para agregar, eliminar y acceder a elementos numéricos en un contexto SVG.

## Documentación

### Propósito
SVGNumberList forma parte del DOM (Document Object Model) de SVG y se utiliza para representar una colección de valores numéricos, que son comúnmente utilizados en atributos SVG como `stroke-dasharray`, `transform`, y otros que requieren una lista de números.

### Uso
La interfaz SVGNumberList se utiliza para acceder y manipular listas de números en atributos SVG. Esta interfaz permite realizar operaciones como la adición de nuevos números, la eliminación de números existentes, y la obtención de valores individuales de la lista.

### Métodos Principales
- **`appendItem(newItem)`**: Agrega un nuevo número al final de la lista.
- **`clear()`**: Elimina todos los números de la lista.
- **`getItem(index)`**: Devuelve el número en la posición especificada.
- **`insertItemBefore(newItem, index)`**: Inserta un nuevo número antes del índice especificado.
- **`removeItem(index)`**: Elimina el número en la posición especificada.
- **`replaceItem(newItem, index)`**: Reemplaza el número en el índice especificado con un nuevo número.

## Ejemplos

### Ejemplo 1: Crear y manipular un SVGNumberList
```javascript
// Crear un nuevo SVGNumberList
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "circle");
let numberList = svgElement.getAttribute("stroke-dasharray");

// Agregar números a la lista
numberList.appendItem(5);
numberList.appendItem(10);
numberList.appendItem(15);

// Obtener un número específico
console.log(numberList.getItem(1)); // Salida: 10

// Reemplazar un número
numberList.replaceItem(20, 1); // Reemplaza el 10 con 20

// Eliminar un número
numberList.removeItem(0); // Elimina el número 5
```

### Ejemplo 2: Usar insertItemBefore
```javascript
// Crear un nuevo SVGNumberList
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "rect");
let numberList = svgElement.getAttribute("stroke-dasharray");

// Agregar números
numberList.appendItem(30);
numberList.appendItem(50);

// Insertar un número antes del primer elemento
numberList.insertItemBefore(40, 0); // Inserta 40 antes de 30
```

## Explicación
Al trabajar con SVGNumberList, es importante recordar que esta interfaz no es una matriz JavaScript tradicional. Por lo tanto, no se pueden utilizar métodos de matriz estándar como `map`, `filter` o `forEach`. Además, al manipular elementos de la lista, los índices comienzan desde 0. Al usar `removeItem`, el índice debe ser válido; de lo contrario, se producirá un error. También es recomendable verificar la existencia de un elemento antes de intentar acceder a él.

## Resumen en una línea
SVGNumberList en JavaScript permite la manipulación de listas de números en gráficos SVG, facilitando operaciones como agregar, eliminar y acceder a elementos numéricos.