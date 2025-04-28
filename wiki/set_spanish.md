<!--
Meta Description: # Conjunto en JavaScript: Uso y Ejemplos Prácticos ## Sinopsis El objeto `Set` en JavaScript es una colección de valores que permite almacenar datos ú...
Meta Keywords: set, numeros, javascript, los, que
-->

# Conjunto en JavaScript: Uso y Ejemplos Prácticos

## Sinopsis
El objeto `Set` en JavaScript es una colección de valores que permite almacenar datos únicos, eliminando automáticamente duplicados. Es una herramienta útil para manejar listas de elementos sin repeticiones.

## Documentación
El objeto `Set` es parte del estándar ECMAScript 2015 (ES6) y se utiliza para crear colecciones de valores. A diferencia de los arrays, los `Set` no permiten elementos duplicados y su orden es el mismo que el orden de inserción. 

### Propósito
Los `Set` son especialmente útiles cuando se necesita almacenar valores únicos y se desea realizar operaciones como la unión, intersección o diferencia de conjuntos.

### Uso
Para crear un `Set`, se utiliza la siguiente sintaxis:

```javascript
const mySet = new Set([iterable]);
```

Donde `iterable` es una colección que puede ser un array, un string, o cualquier objeto iterable.

### Métodos Principales
- `add(value)`: Agrega un nuevo elemento al conjunto.
- `delete(value)`: Elimina un elemento del conjunto.
- `has(value)`: Devuelve `true` si el valor existe en el conjunto, de lo contrario `false`.
- `clear()`: Elimina todos los elementos del conjunto.
- `size`: Propiedad que devuelve el número de elementos en el conjunto.

## Ejemplos

### Crear un Set
```javascript
const numeros = new Set([1, 2, 3, 4, 5]);
console.log(numeros); // Set { 1, 2, 3, 4, 5 }
```

### Agregar elementos
```javascript
numeros.add(6);
console.log(numeros); // Set { 1, 2, 3, 4, 5, 6 }
```

### Verificar existencia
```javascript
console.log(numeros.has(3)); // true
console.log(numeros.has(7)); // false
```

### Eliminar elementos
```javascript
numeros.delete(2);
console.log(numeros); // Set { 1, 3, 4, 5, 6 }
```

### Limpiar el Set
```javascript
numeros.clear();
console.log(numeros); // Set {}
```

## Explicación
Al utilizar `Set`, es importante tener en cuenta que solo los valores primitivos son considerados únicos. Por ejemplo, dos objetos diferentes se consideran valores distintos, incluso si tienen el mismo contenido. Además, los `Set` mantienen el orden de inserción, lo que puede ser ventajoso en ciertas aplicaciones.

Un error común es pensar que los `Set` pueden contener duplicados. Si intentas agregar el mismo valor más de una vez, el `Set` no generará un error, pero simplemente ignorará el valor duplicado.

## Resumen en una línea
El objeto `Set` en JavaScript permite almacenar valores únicos en una colección, eliminando automáticamente los duplicados.