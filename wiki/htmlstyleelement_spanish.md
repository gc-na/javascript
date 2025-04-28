<!--
Meta Description: # HTMLStyleElement en JavaScript: Manipulación de Estilos en Documentos HTML ## Sinopsis El `HTMLStyleElement` es una interfaz de JavaScript que repre...
Meta Keywords: css, style, una, reglas, estilo
-->

# HTMLStyleElement en JavaScript: Manipulación de Estilos en Documentos HTML

## Sinopsis
El `HTMLStyleElement` es una interfaz de JavaScript que representa un elemento `<style>` en un documento HTML. Permite a los desarrolladores manipular y acceder a las reglas de estilo CSS en tiempo de ejecución, lo que facilita la personalización de la apariencia de una página web.

## Documentación

### Propósito
El `HTMLStyleElement` se utiliza para crear y gestionar estilos CSS dentro de un documento HTML. Permite añadir, eliminar y modificar reglas de estilo de manera dinámica, contribuyendo a la flexibilidad en el diseño de las páginas web.

### Uso
Para trabajar con `HTMLStyleElement`, primero se debe crear un elemento `<style>` y luego agregarlo al DOM. Esto se puede hacer utilizando JavaScript con el método `document.createElement()`, seguido de la adición de reglas CSS a través de la propiedad `sheet`.

### Detalles
- **Propiedades Principales**:
  - `type`: Define el tipo de contenido del estilo, generalmente "text/css".
  - `media`: Especifica los medios para los cuales el estilo es aplicable (por ejemplo, "screen", "print").
  - `sheet`: Permite acceder al objeto `CSSStyleSheet`, donde se pueden manipular las reglas CSS.

### Métodos Comunes
- `insertRule()`: Permite insertar una nueva regla de estilo en una hoja de estilos.
- `deleteRule()`: Permite eliminar una regla de estilo específica.

## Ejemplos

### Ejemplo 1: Crear y agregar un elemento `<style>`

```javascript
// Crear un nuevo elemento <style>
const styleElement = document.createElement('style');
styleElement.type = 'text/css';

// Agregar reglas CSS
styleElement.appendChild(document.createTextNode(`
  body {
    background-color: lightblue;
  }
`));

// Añadir el elemento <style> al <head>
document.head.appendChild(styleElement);
```

### Ejemplo 2: Modificar reglas de estilo existentes

```javascript
// Acceder al primer elemento <style> del documento
const styleElement = document.querySelector('style');
const sheet = styleElement.sheet;

// Insertar una nueva regla
sheet.insertRule('h1 { color: red; }', sheet.cssRules.length);

// Eliminar la primera regla
sheet.deleteRule(0);
```

## Explicación
Al trabajar con `HTMLStyleElement`, es importante tener en cuenta que la manipulación del DOM puede causar reflujo y repintado en la página, lo que puede afectar el rendimiento. Además, las reglas CSS deben ser válidas; de lo contrario, se generarán errores en tiempo de ejecución. Es recomendable realizar pruebas exhaustivas para asegurarse de que los estilos se aplican correctamente en todos los navegadores.

## Resumen en una línea
`HTMLStyleElement` permite manipular dinámicamente estilos CSS en documentos HTML mediante JavaScript.