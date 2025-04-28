<!--
Meta Description: # Promesas en JavaScript: Manejo Asíncrono Eficiente ## Sinopsis Las promesas en JavaScript son un objeto que representan la eventual finalización (o ...
Meta Keywords: una, promise, promesas, javascript, las
-->

# Promesas en JavaScript: Manejo Asíncrono Eficiente

## Sinopsis
Las promesas en JavaScript son un objeto que representan la eventual finalización (o falla) de una operación asíncrona y su valor resultante. Permiten manejar operaciones asíncronas de manera más sencilla y legible, evitando el uso excesivo de callbacks.

## Documentación
### ¿Qué es una Promesa?
Una promesa es un objeto que puede estar en uno de tres estados:
- **Pendiente (Pending)**: El estado inicial, ni cumplida ni rechazada.
- **Cumplida (Fulfilled)**: La operación se completó exitosamente.
- **Rechazada (Rejected)**: La operación falló.

### Propósito
Las promesas se utilizan para manejar operaciones que pueden tardar en completarse, como solicitudes de red, lectura de archivos y temporizadores. Proporcionan una forma más clara y estructurada de trabajar con código asíncrono.

### Uso
Para crear una promesa, se utiliza el constructor `Promise`. Acepta una función que toma dos argumentos: `resolve` y `reject`.

```javascript
const miPromesa = new Promise((resolve, reject) => {
    // Lógica asíncrona
});
```

Para manejar el resultado de una promesa, se utilizan los métodos `.then()` y `.catch()`:

```javascript
miPromesa
    .then(resultado => {
        // Código a ejecutar si la promesa se cumple
    })
    .catch(error => {
        // Código a ejecutar si la promesa se rechaza
    });
```

### Métodos Adicionales
- **Promise.all()**: Espera a que todas las promesas se cumplan o se rechacen.
- **Promise.race()**: Retorna la primera promesa que se cumpla o se rechace.

## Ejemplos
### Ejemplo Básico
```javascript
const promesaEjemplo = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("¡Operación completada!");
    }, 1000);
});

promesaEjemplo
    .then(mensaje => console.log(mensaje))
    .catch(error => console.error(error));
```

### Uso de `Promise.all()`
```javascript
const promesa1 = Promise.resolve(3);
const promesa2 = new Promise((resolve) => setTimeout(resolve, 100, '¡Hola!'));
const promesa3 = new Promise((resolve, reject) => reject('Error!'));

Promise.all([promesa1, promesa2])
    .then(valores => console.log(valores)) // [3, '¡Hola!']
    .catch(error => console.error(error));
```

## Explicación
### Errores Comunes
- **No manejar errores**: Olvidar usar `.catch()` para manejar errores puede llevar a excepciones no controladas.
- **Anidación excesiva**: Aunque las promesas evitan el "callback hell", anidar promesas puede dificultar la legibilidad. Se recomienda encadenarlas de manera adecuada.

### Notas Adicionales
- Las promesas no son solo para operaciones asíncronas: también pueden ser utilizadas para operaciones sincrónicas que devuelven resultados en un futuro.
- Las promesas son una parte fundamental de las características modernas de JavaScript, como `async` y `await`, que permiten escribir código asíncrono de manera más sincrónica.

## Resumen en una Línea
Las promesas en JavaScript son una herramienta esencial para manejar operaciones asíncronas, mejorando la legibilidad y el manejo de errores en el código.