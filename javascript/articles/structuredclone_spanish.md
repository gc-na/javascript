<!--
Meta Description: # structuredClone: Clonación de Objetos en JavaScript ## Sinopsis `structuredClone` es una función nativa de JavaScript que permite realizar copias pr...
Meta Keywords: structuredclone, que, clonación, objetos, javascript
-->

# structuredClone: Clonación de Objetos en JavaScript

## Sinopsis
`structuredClone` es una función nativa de JavaScript que permite realizar copias profundas de objetos, arrays y otros tipos de datos complejos. A diferencia del método de clonación superficial, `structuredClone` asegura que todos los niveles de un objeto sean copiados, manteniendo la estructura y el tipo de datos.

## Documentación
### Propósito
La función `structuredClone` fue introducida para proporcionar una manera efectiva y segura de clonar estructuras de datos complejas en JavaScript. Permite la clonación de objetos que contienen tipos de datos que no se pueden clonar mediante métodos tradicionales, como `JSON.parse(JSON.stringify(obj))`.

### Uso
La sintaxis básica de `structuredClone` es la siguiente:

```javascript
const clonedObject = structuredClone(originalObject);
```

- **originalObject**: El objeto que se desea clonar.
- **clonedObject**: El nuevo objeto que es una copia profunda de `originalObject`.

### Detalles
`structuredClone` puede manejar una variedad de tipos de datos, incluyendo:
- Objetos regulares
- Arrays
- Mapas y Conjuntos
- Typed Arrays
- Objetos Date
- Objetos RegExp
- Y más...

La función lanzará un error si intentas clonar un tipo de datos que no es clonable, como funciones o símbolos.

## Ejemplos

### Ejemplo 1: Clonación de un objeto simple
```javascript
const original = { name: "Juan", age: 30 };
const cloned = structuredClone(original);

console.log(cloned); // { name: "Juan", age: 30 }
```

### Ejemplo 2: Clonación de un array
```javascript
const arrayOriginal = [1, 2, 3, { a: 1 }];
const arrayClonado = structuredClone(arrayOriginal);

console.log(arrayClonado); // [1, 2, 3, { a: 1 }]
```

### Ejemplo 3: Clonación de un objeto complejo con Map
```javascript
const mapOriginal = new Map();
mapOriginal.set('key1', { value: 'value1' });
const mapClonado = structuredClone(mapOriginal);

console.log(mapClonado.get('key1')); // { value: 'value1' }
```

## Explicación
Aunque `structuredClone` es una herramienta poderosa, hay algunas trampas comunes que los desarrolladores deben tener en cuenta:

- **Clonación de funciones**: `structuredClone` no puede clonar funciones. Si intentas hacerlo, lanzarás un TypeError.
- **Ciclos en objetos**: Si el objeto original contiene referencias circulares, `structuredClone` manejará la clonación sin errores, a diferencia de otros métodos que fallarían.
- **Tipos no clonables**: Algunos tipos de datos como `undefined`, `Infinity`, o `NaN` no se clonarán y se convertirán en un comportamiento específico según el tipo.

## Resumen en una línea
`structuredClone` es una función de JavaScript que permite realizar copias profundas de objetos y estructuras de datos complejas de manera sencilla y segura.