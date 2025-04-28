<!--
Meta Description: # FinalizationRegistry en JavaScript: Gestión de Recursos y Limpieza Efectiva ## Sinopsis FinalizationRegistry es una característica introducida en EC...
Meta Keywords: finalizationregistry, javascript, que, objeto, objetos
-->

# FinalizationRegistry en JavaScript: Gestión de Recursos y Limpieza Efectiva

## Sinopsis
FinalizationRegistry es una característica introducida en ECMAScript 2021 que permite a los desarrolladores registrar objetos y recibir notificaciones cuando esos objetos son recolectados por el recolector de basura, facilitando la gestión de recursos y la limpieza de memoria en aplicaciones JavaScript.

## Documentación

### Propósito
FinalizationRegistry proporciona una forma de ejecutar un callback cuando los objetos registrados son recogidos por el recolector de basura. Esto es útil para limpiar recursos externos, como conexiones a bases de datos o manejadores de eventos, que no pueden ser automáticamente liberados por el recolector de basura de JavaScript.

### Uso
Para utilizar FinalizationRegistry, se debe crear una instancia de la clase pasando un callback como argumento. Luego, se registran los objetos junto con una clave que se pasará al callback cuando el objeto sea recolectado.

#### Sintaxis
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`El objeto con valor ${heldValue} ha sido recolectado.`);
});
```

#### Registro de un objeto
```javascript
let obj = {};
registry.register(obj, 'valor asociado');
```

## Ejemplos

### Ejemplo Básico
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`El objeto con valor ${heldValue} ha sido recolectado.`);
});

let obj = {};
registry.register(obj, 'valor asociado');

obj = null; // El objeto queda disponible para el recolector de basura
```

### Ejemplo con Temporizador
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`Recurso limpiado: ${heldValue}`);
});

function createResource() {
    const resource = {};
    registry.register(resource, 'recurso importante');
    return resource;
}

let myResource = createResource();
myResource = null; // El recurso será recolectado eventualmente
```

## Explicación
Algunas consideraciones importantes sobre el uso de FinalizationRegistry:

- **No hay garantía de tiempo**: No se garantiza cuándo se ejecutará el callback. Puede que no se ejecute inmediatamente después de que el objeto sea recolectado.
- **Ejecución en un contexto diferente**: El callback puede ejecutarse en un contexto diferente al que registró el objeto, lo que podría afectar el acceso a las variables locales.
- **Uso adecuado de referencias**: Si se mantiene una referencia del objeto registrado, el recolector de basura no lo recolectará. Asegúrate de eliminar la referencia cuando ya no sea necesaria.
- **No es un reemplazo para WeakMap**: Aunque FinalizationRegistry ofrece funcionalidades adicionales, no debe ser considerado un reemplazo directo para WeakMap, que es más adecuado para mantener referencias débiles a objetos.

## Resumen en Una Línea
FinalizationRegistry permite a los desarrolladores registrar objetos en JavaScript y recibir notificaciones cuando esos objetos son recolectados por el recolector de basura, facilitando la gestión de recursos.