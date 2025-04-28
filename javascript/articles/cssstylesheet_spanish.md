<!--
Meta Description: # CSSStyleSheet en JavaScript: Manipulación de Hojas de Estilo ## Sinopsis `CSSStyleSheet` es un objeto de JavaScript que representa una hoja de estil...
Meta Keywords: una, regla, estilo, css, que
-->

# CSSStyleSheet en JavaScript: Manipulación de Hojas de Estilo

## Sinopsis
`CSSStyleSheet` es un objeto de JavaScript que representa una hoja de estilo CSS en el DOM, permitiendo a los desarrolladores manipular sus reglas y propiedades de manera dinámica.

## Documentación
`CSSStyleSheet` proporciona una interfaz para interactuar con las hojas de estilo CSS. Puedes acceder a las hojas de estilo a través del objeto `document.styleSheets`. Cada instancia de `CSSStyleSheet` contiene una colección de reglas CSS que pueden ser leídas o modificadas.

### Propósito
El propósito principal de `CSSStyleSheet` es permitir a los desarrolladores manipular estilos CSS de manera programática, facilitando la creación de interfaces dinámicas y responsivas.

### Uso
Para acceder a una hoja de estilo, puedes usar el siguiente patrón:

```javascript
let hojaEstilo = document.styleSheets[0]; // Accede a la primera hoja de estilo
```

Una vez que tienes una referencia a la hoja de estilo, puedes agregar, eliminar o modificar reglas CSS.

### Detalles
- **Propiedades Principales**:
  - `cssRules`: Una colección de todas las reglas CSS en la hoja de estilo.
  - `insertRule()`: Método que permite agregar una nueva regla a la hoja de estilo.
  - `deleteRule()`: Método que permite eliminar una regla existente.

## Ejemplos
### Acceder y Modificar una Regla CSS
```javascript
let hojaEstilo = document.styleSheets[0];

// Acceder a la primera regla
let regla = hojaEstilo.cssRules[0];

// Modificar la propiedad de la regla
regla.style.color = 'red';
```

### Agregar una Nueva Regla
```javascript
let hojaEstilo = document.styleSheets[0];

// Agregar una nueva regla
hojaEstilo.insertRule('body { background-color: blue; }', hojaEstilo.cssRules.length);
```

### Eliminar una Regla Existente
```javascript
let hojaEstilo = document.styleSheets[0];

// Eliminar la primera regla
hojaEstilo.deleteRule(0);
```

## Explicación
Es importante tener en cuenta que no todas las hojas de estilo son modificables. Algunas pueden ser de solo lectura, especialmente las que provienen de dominios cruzados debido a las restricciones de seguridad del navegador (CORS). Además, al modificar reglas CSS, los cambios son inmediatos pero no persistentes: si se recarga la página, se perderán.

Una trampa común es intentar modificar tantas reglas como sea posible sin verificar el índice o la existencia de la regla, lo que puede generar errores. Siempre es recomendable manejar excepciones al trabajar con `insertRule` y `deleteRule`.

## Resumen en Una Línea
`CSSStyleSheet` permite la manipulación programática de hojas de estilo CSS en JavaScript, facilitando la creación de interfaces dinámicas.