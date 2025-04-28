<!--
Meta Description: # WeakSet en JavaScript: Todo lo que Necesitas Saber ## Sinopsis WeakSet es una colección en JavaScript que permite almacenar objetos débiles, es deci...
Meta Keywords: weakset, que, objetos, referencias, memoria
-->

# WeakSet en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
WeakSet es una colección en JavaScript que permite almacenar objetos débiles, es decir, objetos que son recolectados por el recolector de basura si no hay otras referencias a ellos. Esta estructura de datos es útil para gestionar objetos en memoria sin arriesgar filtraciones de memoria.

## Documentación
### Propósito
WeakSet se utiliza principalmente para almacenar un grupo de objetos sin mantener referencias fuertes a esos objetos. Esto significa que si un objeto almacenado en un WeakSet no tiene otras referencias en el código, puede ser recolectado por el recolector de basura, liberando memoria automáticamente.

### Uso
Se puede crear un WeakSet utilizando la sintaxis `new WeakSet()`. La colección ofrece métodos como `add`, `delete` y `has` para gestionar los objetos que contiene.

**Métodos de WeakSet:**
- **add(value)**: Agrega un objeto al WeakSet.
- **delete(value)**: Elimina un objeto del WeakSet.
- **has(value)**: Verifica si un objeto está presente en el WeakSet.

### Detalles
- A diferencia de un Set normal, los objetos almacenados en un WeakSet son débiles, lo que significa que no impiden que el recolector de basura elimine esos objetos si no hay otras referencias.
- Los WeakSets solo pueden contener objetos. Intentar agregar otro tipo de datos (como números o cadenas) resultará en un TypeError.
- No se puede iterar sobre un WeakSet, lo cual es una de sus características distintivas en comparación con el Set.

## Ejemplos

### Ejemplo 1: Creación y uso básico de WeakSet
```javascript
let objeto1 = { nombre: "objeto1" };
let objeto2 = { nombre: "objeto2" };

let weakset = new WeakSet();
weakset.add(objeto1);
weakset.add(objeto2);

console.log(weakset.has(objeto1)); // true
weakset.delete(objeto1);
console.log(weakset.has(objeto1)); // false
```

### Ejemplo 2: Comportamiento de recolección de basura
```javascript
let objeto3 = { nombre: "objeto3" };
let weakset2 = new WeakSet();
weakset2.add(objeto3);

// Si no hay más referencias a objeto3, será recolectado por el garbage collector
objeto3 = null; // En este punto, objeto3 puede ser recolectado
```

## Explicación
Un error común al trabajar con WeakSet es intentar almacenar tipos de datos primitivos. Por ejemplo, al intentar agregar un número o una cadena, se generará un TypeError. Además, dado que no se puede iterar a través de un WeakSet, los desarrolladores a veces se confunden al querer listar sus elementos.

Es importante destacar que los WeakSets son ideales para almacenar objetos que se utilizan como "marcadores" o "referencias temporales" sin mantenerlos en memoria indefinidamente, previniendo así posibles fugas de memoria.

## Resumen en Una Línea
WeakSet en JavaScript permite gestionar colecciones de objetos de manera eficiente, asegurando que la memoria se libere automáticamente cuando los objetos ya no son necesarios.