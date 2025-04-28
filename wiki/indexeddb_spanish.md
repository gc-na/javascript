<!--
Meta Description: # indexedDB: Almacenamiento de Datos Estructurados en JavaScript ## Sinopsis IndexedDB es una API de almacenamiento de datos en el navegador que permi...
Meta Keywords: datos, const, event, objectstore, que
-->

# indexedDB: Almacenamiento de Datos Estructurados en JavaScript

## Sinopsis
IndexedDB es una API de almacenamiento de datos en el navegador que permite a las aplicaciones web almacenar y recuperar objetos de datos estructurados, incluyendo archivos y blobs. A diferencia de otras soluciones de almacenamiento como LocalStorage, IndexedDB permite realizar consultas complejas y manejar grandes volúmenes de datos.

## Documentación
### Propósito
IndexedDB está diseñado para permitir que las aplicaciones web almacenen grandes cantidades de datos en el navegador de manera eficiente, persistente y estructurada. Es ideal para aplicaciones que necesitan trabajar sin conexión o que requieren almacenamiento más allá de los simples pares clave-valor.

### Uso
Para utilizar IndexedDB, primero se necesita abrir o crear una base de datos, definir un esquema, y luego realizar operaciones de lectura y escritura. La API está basada en promesas y eventos, lo que facilita la gestión de operaciones asincrónicas.

#### Pasos Básicos:
1. **Abrir o crear una base de datos**:
   ```javascript
   const request = indexedDB.open("miBaseDeDatos", 1);
   ```

2. **Definir el esquema**:
   ```javascript
   request.onupgradeneeded = function(event) {
       const db = event.target.result;
       const objectStore = db.createObjectStore("miAlmacen", { keyPath: "id" });
   };
   ```

3. **Agregar datos**:
   ```javascript
   request.onsuccess = function(event) {
       const db = event.target.result;
       const transaction = db.transaction("miAlmacen", "readwrite");
       const objectStore = transaction.objectStore("miAlmacen");
       const data = { id: 1, nombre: "Ejemplo" };
       objectStore.add(data);
   };
   ```

4. **Leer datos**:
   ```javascript
   const transaction = db.transaction("miAlmacen", "readonly");
   const objectStore = transaction.objectStore("miAlmacen");
   const request = objectStore.get(1);
   request.onsuccess = function(event) {
       console.log(event.target.result);
   };
   ```

## Ejemplos
### Ejemplo Completo
Aquí hay un ejemplo más completo que muestra cómo crear una base de datos, agregar un registro y luego leerlo.

```javascript
// Abrir o crear base de datos
const request = indexedDB.open("miBaseDeDatos", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    db.createObjectStore("miAlmacen", { keyPath: "id" });
};

request.onsuccess = function(event) {
    const db = event.target.result;

    // Agregar un objeto
    const transaction = db.transaction("miAlmacen", "readwrite");
    const objectStore = transaction.objectStore("miAlmacen");
    objectStore.add({ id: 1, nombre: "Ejemplo" });

    // Leer el objeto
    const getRequest = objectStore.get(1);
    getRequest.onsuccess = function(event) {
        console.log(getRequest.result); // { id: 1, nombre: "Ejemplo" }
    };
};

request.onerror = function(event) {
    console.error("Error al abrir la base de datos:", event.target.error);
};
```

## Explicación
### Errores Comunes
- **No manejar correctamente los eventos**: Asegúrate de manejar los eventos `onsuccess` y `onerror` para evitar que la aplicación falle sin saber por qué.
- **Olvidar el método `onupgradeneeded`**: Este método es fundamental para establecer el esquema de la base de datos y debe ser implementado correctamente para evitar problemas al abrir una base de datos existente.
- **Uso incorrecto de transacciones**: Recuerda que las transacciones deben ser utilizadas con el modo apropiado (`readwrite` o `readonly`), dependiendo de si vas a modificar los datos o solo leerlos.

## Resumen en una Línea
IndexedDB es una potente API de JavaScript que permite el almacenamiento y recuperación eficiente de datos estructurados en el navegador.