<!--
Meta Description: # CSSKeyframeRule en JavaScript: Guía Completa ## Sinopsis El `CSSKeyframeRule` es una interfaz de la API de CSS en JavaScript que representa una regl...
Meta Keywords: una, css, csskeyframerule, que, regla
-->

# CSSKeyframeRule en JavaScript: Guía Completa

## Sinopsis
El `CSSKeyframeRule` es una interfaz de la API de CSS en JavaScript que representa una regla de animación de keyframe en una hoja de estilo CSS. Permite definir los estilos a aplicar en diferentes etapas de una animación.

## Documentación
### Propósito
`CSSKeyframeRule` se utiliza para crear y manipular reglas de animación dentro de un documento CSS. Cada regla de keyframe define un conjunto de estilos CSS que se aplican en un punto específico durante la duración de una animación.

### Uso
Para utilizar `CSSKeyframeRule`, primero necesitas acceder a una hoja de estilo que contenga animaciones. Puedes crear o modificar animaciones utilizando JavaScript a través de la propiedad `styleSheet` y luego acceder a las reglas de keyframe.

### Detalles
- **Propiedades**:
  - `keyText`: Representa el texto del keyframe (por ejemplo, `0%`, `50%`, `100%`).
  - `style`: Permite acceder a un objeto `CSSStyleDeclaration` que contiene las propiedades CSS aplicadas en ese keyframe.
  
- **Métodos**:
  - `insertRule()`: Permite insertar una nueva regla CSS en la hoja de estilo.
  - `deleteRule()`: Permite eliminar una regla CSS existente.

## Ejemplos
### Ejemplo 1: Crear una regla de keyframe
```javascript
const styleSheet = document.styleSheets[0];
const keyframeRule = `
  @keyframes example {
    0% { background-color: red; }
    50% { background-color: yellow; }
    100% { background-color: green; }
  }
`;
styleSheet.insertRule(keyframeRule, styleSheet.cssRules.length);
```

### Ejemplo 2: Modificar una regla existente
```javascript
const keyframes = styleSheet.cssRules[0]; // Supongamos que es un @keyframes
if (keyframes instanceof CSSKeyframeRule) {
  keyframes.style.setProperty('background-color', 'blue', 'important');
}
```

## Explicación
Al trabajar con `CSSKeyframeRule`, es importante considerar que:
- No todos los navegadores manejan las animaciones CSS de la misma manera, por lo que debes verificar la compatibilidad.
- Cambiar reglas en tiempo de ejecución puede llevar a problemas de rendimiento si se hace con frecuencia.
- Al modificar reglas existentes, asegúrate de tener el índice correcto y de que la regla sea efectivamente un `CSSKeyframeRule`.

## Resumen en una línea
`CSSKeyframeRule` permite definir y manipular reglas de keyframe para animaciones CSS mediante JavaScript.