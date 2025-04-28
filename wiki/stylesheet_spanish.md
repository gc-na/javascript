<!--
Meta Description: # Hoja de Estilo (StyleSheet) en JavaScript: Guía Completa ## Sinopsis La interfaz `StyleSheet` en JavaScript permite interactuar con las hojas de est...
Meta Keywords: estilo, stylesheet, reglas, las, hoja
-->

# Hoja de Estilo (StyleSheet) en JavaScript: Guía Completa

## Sinopsis
La interfaz `StyleSheet` en JavaScript permite interactuar con las hojas de estilo CSS en un documento HTML, facilitando la manipulación dinámica de estilos en aplicaciones web.

## Documentación
### Propósito
El objeto `StyleSheet` representa una hoja de estilos CSS en un documento. Permite acceder y modificar las reglas de estilo, facilitando la creación de interfaces dinámicas y responsivas.

### Uso
Los objetos `StyleSheet` se pueden obtener a través de la propiedad `styleSheets` del objeto `document`. Esta propiedad devuelve una colección de todas las hojas de estilo que están presentes en el documento. Cada hoja de estilo en esta colección es un objeto `StyleSheet` que se puede manipular.

### Detalles
- **Propiedades clave**:
  - `cssRules`: Esta propiedad retorna una lista de todas las reglas de estilo definidas en la hoja de estilo.
  - `insertRule()`: Permite insertar una nueva regla CSS en la hoja de estilo.
  - `deleteRule()`: Permite eliminar una regla CSS existente.

- **Ejemplo de acceso a hojas de estilo**:
    ```javascript
    var hojasEstilo = document.styleSheets;
    console.log(hojasEstilo);
    ```

## Ejemplos

### Ejemplo 1: Acceder a las reglas de estilo
```javascript
var stylesheet = document.styleSheets[0]; // Accede a la primera hoja de estilo
var reglas = stylesheet.cssRules; // Obtiene las reglas CSS
console.log(reglas);
```

### Ejemplo 2: Insertar una nueva regla
```javascript
var stylesheet = document.styleSheets[0];
stylesheet.insertRule('body { background-color: lightblue; }', reglas.length);
```

### Ejemplo 3: Eliminar una regla existente
```javascript
var stylesheet = document.styleSheets[0];
stylesheet.deleteRule(0); // Elimina la primera regla de la hoja de estilo
```

## Explicación
Al trabajar con `StyleSheet`, es importante tener en cuenta lo siguiente:
- **Compatibilidad**: No todas las propiedades y métodos pueden estar disponibles en todos los navegadores. Es recomendable verificar la compatibilidad antes de implementar.
- **Orden de las reglas**: Al insertar reglas, estas se añadirán al final de la hoja de estilo, lo que puede afectar el comportamiento de los estilos si hay reglas conflictivas.
- **Reglas en línea**: Las reglas CSS en línea tienen mayor prioridad que aquellas definidas en hojas de estilo, lo que puede resultar en confusiones al intentar aplicar estilos.

## Resumen en una línea
El objeto `StyleSheet` en JavaScript permite manipular dinámicamente las hojas de estilo CSS de un documento HTML, facilitando la personalización de la apariencia de las aplicaciones web.