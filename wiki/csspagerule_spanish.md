<!--
Meta Description: # CSSPageRule en JavaScript: Guía Completa y Ejemplos ## Sinopsis CSSPageRule es una interfaz en JavaScript que representa una regla de estilo específ...
Meta Keywords: estilo, una, que, regla, csspagerule
-->

# CSSPageRule en JavaScript: Guía Completa y Ejemplos

## Sinopsis
CSSPageRule es una interfaz en JavaScript que representa una regla de estilo específica dentro de un conjunto de reglas de estilo de una hoja de estilo CSS, aplicada a páginas impresas o visualizadas en medios como PDF. Permite a los desarrolladores acceder y manipular estilos relacionados con la impresión y otras presentaciones.

## Documentación
### Propósito
El propósito de CSSPageRule es proporcionar una forma de interactuar con las reglas de estilo que se aplican a elementos de página específicos en un documento CSS. Esto es especialmente útil cuando se trabaja con estilos que se aplican a diferentes formatos de presentación, como la impresión.

### Uso
Para utilizar CSSPageRule, primero se debe acceder a una hoja de estilo a través del objeto `document.styleSheets`. A partir de ahí, se pueden obtener las reglas de estilo mediante la propiedad `cssRules`. Cada regla puede ser de tipo `CSSPageRule`, que se puede identificar y manipular.

### Detalles
- **Propiedades**:
  - `selectorText`: Contiene el texto del selector de la regla.
  - `style`: Proporciona acceso al objeto CSSStyleDeclaration que permite modificar las propiedades CSS de la regla.
  
- **Métodos**:
  - `deleteRule()`: Elimina la regla de la hoja de estilo.
  - `insertRule()`: Inserta una nueva regla en la hoja de estilo.

## Ejemplos
### Ejemplo Básico de Uso
```javascript
// Acceder a la primera hoja de estilo
var stylesheet = document.styleSheets[0];

// Acceder a las reglas de la hoja de estilo
var rules = stylesheet.cssRules;

// Iterar sobre las reglas para encontrar una regla CSSPageRule
for (var i = 0; i < rules.length; i++) {
  if (rules[i] instanceof CSSPageRule) {
    console.log(rules[i].selectorText); // Muestra el selector de la regla
    console.log(rules[i].style.cssText); // Muestra las propiedades CSS
  }
}
```

### Ejemplo de Inserción de una Nueva Regla
```javascript
var stylesheet = document.styleSheets[0];

// Insertar una nueva regla de página
stylesheet.insertRule('@page { margin: 1in; }', stylesheet.cssRules.length);
```

## Explicación
Uno de los errores comunes al trabajar con CSSPageRule es olvidar que solo se aplica a reglas específicas de `@page`. Asegúrate de que el tipo de regla que estás manipulando sea efectivamente una `CSSPageRule`. Además, ten en cuenta que las reglas de estilo pueden no ser aplicables en todos los navegadores, especialmente en versiones más antiguas, lo que puede causar inconsistencias en la presentación de los estilos.

Otro punto a considerar es que la manipulación de reglas de estilos en tiempo de ejecución puede no ser reflejada inmediatamente en el renderizado de la página, dependiendo del navegador y su implementación de CSS.

## Resumen en una Línea
CSSPageRule permite a los desarrolladores acceder y manipular reglas de estilo específicas para la presentación de páginas en documentos CSS mediante JavaScript.