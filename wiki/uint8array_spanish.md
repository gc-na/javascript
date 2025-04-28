<!--
Meta Description: # Uint8Array en JavaScript: Uso y Ejemplos ## Sinopsis `Uint8Array` es un tipo de objeto de arreglo en JavaScript que permite trabajar con arreglos de...
Meta Keywords: uint8array, arreglo, array, javascript, que
-->

# Uint8Array en JavaScript: Uso y Ejemplos

## Sinopsis
`Uint8Array` es un tipo de objeto de arreglo en JavaScript que permite trabajar con arreglos de enteros sin signo de 8 bits. Es parte de la interfaz `TypedArray`, que proporciona un enfoque eficiente para manipular datos binarios.

## Documentación
`Uint8Array` se utiliza para crear un arreglo que almacena números enteros en el rango de 0 a 255. Este tipo de arreglo es especialmente útil cuando se trabaja con datos binarios, como en aplicaciones de procesamiento de imágenes, audio y otros tipos de datos que requieren un formato específico.

### Propósito
El propósito principal de `Uint8Array` es proporcionar un medio eficiente para almacenar y manipular datos binarios, optimizando tanto el rendimiento como el uso de memoria.

### Uso
Para crear un `Uint8Array`, se puede utilizar una de las siguientes formas:
- **Sin argumentos**: Crea un arreglo vacío.
- **Con un número entero**: Crea un arreglo de la longitud especificada.
- **Con un arreglo o un objeto iterable**: Crea un `Uint8Array` a partir de los elementos de ese arreglo u objeto.

#### Sintaxis
```javascript
let array1 = new Uint8Array(); // Crea un Uint8Array vacío.
let array2 = new Uint8Array(10); // Crea un Uint8Array de longitud 10.
let array3 = new Uint8Array([1, 2, 3, 4, 5]); // Crea un Uint8Array a partir de un arreglo.
```

### Métodos disponibles
`Uint8Array` ofrece varios métodos útiles, como:
- `.set()`: Establece elementos de otro arreglo en el `Uint8Array`.
- `.subarray()`: Devuelve una vista de subsección del arreglo.
- `.fill()`: Llena todos los elementos del arreglo con un valor estático.

## Ejemplos
### Ejemplo 1: Creación de un Uint8Array
```javascript
let array = new Uint8Array(5);
console.log(array); // Uint8Array(5) [0, 0, 0, 0, 0]
```

### Ejemplo 2: Uso de set()
```javascript
let array = new Uint8Array(3);
array.set([1, 2, 3]);
console.log(array); // Uint8Array(3) [1, 2, 3]
```

### Ejemplo 3: Uso de subarray()
```javascript
let array = new Uint8Array([10, 20, 30, 40, 50]);
let subArray = array.subarray(1, 4);
console.log(subArray); // Uint8Array(3) [20, 30, 40]
```

### Ejemplo 4: Uso de fill()
```javascript
let array = new Uint8Array(5);
array.fill(1);
console.log(array); // Uint8Array(5) [1, 1, 1, 1, 1]
```

## Explicación
Al trabajar con `Uint8Array`, es importante tener en cuenta que:
- Los valores deben estar en el rango de 0 a 255. Cualquier valor fuera de este rango se ajustará automáticamente.
- Los `TypedArrays`, incluido `Uint8Array`, no permiten valores `null`, `undefined` o `NaN`.
- La memoria se asigna de manera continua, lo que mejora el rendimiento al acceder a sus elementos, pero también limita la flexibilidad en comparación con los arreglos normales de JavaScript.
- Es fundamental recordar que el método `.subarray()` no crea una copia del arreglo, sino que devuelve una vista del mismo.

## Resumen en una línea
`Uint8Array` es un tipo de arreglo en JavaScript que permite almacenar y manipular enteros sin signo de 8 bits de manera eficiente y con bajo consumo de memoria.