<!--
Meta Description: # NodeIterator en JavaScript: Manipulación Eficiente del DOM ## Sinopsis NodeIterator es una interfaz en JavaScript que permite recorrer los nodos de ...
Meta Keywords: que, nodos, los, currentnode, nodeiterator
-->

# NodeIterator en JavaScript: Manipulación Eficiente del DOM

## Sinopsis
NodeIterator es una interfaz en JavaScript que permite recorrer los nodos de un documento HTML o XML de manera eficiente. Proporciona una forma sencilla de iterar sobre los nodos de un árbol DOM, permitiendo filtrar y acceder a los elementos que cumplen con ciertos criterios.

## Documentación
### Propósito
NodeIterator se utiliza para crear un iterador que permite recorrer nodos en un documento, facilitando la manipulación y el acceso a los elementos del DOM. Es especialmente útil cuando se trabaja con grandes cantidades de nodos y se necesita un rendimiento óptimo.

### Uso
Para crear un NodeIterator, se utiliza el método `document.createNodeIterator()` que recibe los siguientes parámetros:

- **root**: El nodo raíz a partir del cual se comenzará la iteración.
- **whatToShow** (opcional): Un valor que determina qué tipos de nodos deben ser iterados. Puede ser un conjunto de constantes de tipo `NodeFilter`.
- **filter** (opcional): Un objeto que implementa la interfaz NodeFilter, permitiendo definir criterios personalizados para la iteración.
- **entityReferenceExpansion** (opcional): Un booleano que indica si se deben expandir las referencias de entidad.

### Detalles
El iterador devuelto por `createNodeIterator` ofrece métodos como `nextNode()` y `previousNode()`, que permiten avanzar o retroceder en la lista de nodos. También se puede utilizar el método `detach()` para liberar los recursos asociados al iterador.

## Ejemplos
Aquí hay algunos ejemplos básicos de cómo usar NodeIterator en JavaScript:

### Ejemplo 1: Iterar a través de todos los nodos de un documento
```javascript
const rootNode = document.getElementById('miElemento');
const iterator = document.createNodeIterator(rootNode, NodeFilter.SHOW_ALL, null, false);

let currentNode;
while (currentNode = iterator.nextNode()) {
    console.log(currentNode.nodeName);
}
```

### Ejemplo 2: Filtrar nodos de tipo ELEMENT_NODE
```javascript
const rootNode = document.getElementById('miElemento');
const iterator = document.createNodeIterator(rootNode, NodeFilter.SHOW_ELEMENT, null, false);

let currentNode;
while (currentNode = iterator.nextNode()) {
    console.log(currentNode.tagName);
}
```

### Ejemplo 3: Usar un filtro personalizado
```javascript
const customFilter = {
    acceptNode: function(node) {
        return (node.nodeType === Node.ELEMENT_NODE && node.classList.contains('activo')) ? NodeFilter.FILTER_ACCEPT : NodeFilter.FILTER_SKIP;
    }
};

const rootNode = document.getElementById('miElemento');
const iterator = document.createNodeIterator(rootNode, NodeFilter.SHOW_ALL, customFilter, false);

let currentNode;
while (currentNode = iterator.nextNode()) {
    console.log(currentNode.tagName);
}
```

## Explicación
Al usar NodeIterator, es importante tener en cuenta que se puede perder de vista el estado del iterador si se hacen cambios en el DOM que afectan los nodos que ya han sido iterados. Por lo tanto, es recomendable realizar la iteración en un contexto donde los nodos no cambien, o actualizar el iterador después de modificaciones en el DOM.

Otro aspecto a considerar es que el método `detach()` debe ser llamado si el iterador ya no es necesario, para evitar fugas de memoria.

## Resumen en una línea
NodeIterator es una interfaz en JavaScript que permite iterar de manera eficiente sobre nodos del DOM, facilitando la manipulación y acceso a los elementos.