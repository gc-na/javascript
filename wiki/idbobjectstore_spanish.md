<!--
Meta Description: # IDBObjectStore en JavaScript: Almacenamiento de Objetos en IndexedDB ## Sinopsis IDBObjectStore es una interfaz clave de la API de IndexedDB en Java...
Meta Keywords: que, objeto, objetos, datos, const
-->

# IDBObjectStore en JavaScript: Almacenamiento de Objetos en IndexedDB

## Sinopsis
IDBObjectStore es una interfaz clave de la API de IndexedDB en JavaScript que permite almacenar y recuperar datos estructurados en una base de datos de manera eficiente. Proporciona un contenedor para objetos que se pueden almacenar de manera persistente en el navegador.

## Documentación

### Propósito
IDBObjectStore se utiliza para manejar el almacenamiento de datos en IndexedDB, que es una solución de almacenamiento en el navegador para aplicaciones web que requieren guardar grandes cantidades de datos. Permite crear, leer, actualizar y eliminar objetos.

### Uso
Para usar IDBObjectStore, primero es necesario abrir una base de datos utilizando el constructor `indexedDB.open()`. Luego, se puede crear un objeto de almacenamiento dentro de una transacción.

### Métodos Principales
- **add(value)**: Añade un nuevo objeto a la tienda de objetos.
- **put(value)**: Modifica un objeto existente o añade uno nuevo si no se encuentra.
- **get(key)**: Recupera un objeto por su clave.
- **delete(key)**: Elimina un objeto por su clave.
- **clear()**: Elimina todos los objetos de la tienda.
- **openCursor()**: Abre un cursor para recorrer los objetos en la tienda.

### Ejemplo de Uso
```javascript
// Abrir la base de datos
const request = indexedDB.open('miBaseDeDatos', 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    // Crear un objeto de almacenamiento
    const objectStore = db.createObjectStore('miTienda', { keyPath: 'id' });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction('miTienda', 'readwrite');
    const objectStore = transaction.objectStore('miTienda');

    // Añadir un objeto
    const item = { id: 1, nombre: 'Ejemplo', valor: 100 };
    const addRequest = objectStore.add(item);

    addRequest.onsuccess = function() {
        console.log('Objeto añadido exitosamente');
    };

    // Recuperar un objeto
    const getRequest = objectStore.get(1);
    getRequest.onsuccess = function() {
        console.log('Objeto recuperado:', getRequest.result);
    };
};

request.onerror = function(event) {
    console.error('Error al abrir la base de datos:', event.target.error);
};
```

## Explicación
Al utilizar IDBObjectStore, es importante tener en cuenta que las operaciones son asíncronas, lo que significa que se deben manejar adecuadamente las promesas o los manejadores de eventos (`onsuccess`, `onerror`). Además, asegúrate de que la base de datos y la tienda de objetos estén correctamente configuradas antes de intentar realizar operaciones.

Un error común es intentar realizar operaciones en la tienda de objetos antes de que la base de datos esté completamente abierta. Esto puede resultar en errores de referencia o excepciones.

## Resumen en una Línea
IDBObjectStore es una interfaz de IndexedDB en JavaScript que permite almacenar y gestionar objetos de manera persistente en el navegador.