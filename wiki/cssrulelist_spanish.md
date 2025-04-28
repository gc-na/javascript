<!--
Meta Description: # CSSRuleList: Manipulación de Reglas CSS con JavaScript ## Sinopsis `CSSRuleList` es una interfaz que representa una colección de objetos `CSSRule`, ...
Meta Keywords: css, una, rules, reglas, var
-->

# CSSRuleList: Manipulación de Reglas CSS con JavaScript

## Sinopsis
`CSSRuleList` es una interfaz que representa una colección de objetos `CSSRule`, permitiendo a los desarrolladores acceder y manipular las reglas CSS dentro de una hoja de estilo mediante JavaScript.

## Documentación
### Propósito
La interfaz `CSSRuleList` es fundamental para interactuar con las reglas CSS de las hojas de estilo. Proporciona una forma de acceder a cada regla CSS, permitiendo realizar operaciones como la lectura, modificación o eliminación de estas reglas.

### Uso
`CSSRuleList` se utiliza comúnmente en el contexto de la propiedad `cssRules` de un objeto `CSSStyleSheet`. Cada `CSSStyleSheet` contiene una lista de reglas CSS que pueden ser accedidas a través de esta propiedad.

### Detalles
- **Propiedades**:
  - `length`: Devuelve el número de reglas en la lista.
- **Métodos**:
  - `item(index)`: Devuelve la regla CSS en la posición especificada por el índice.

### Acceso a CSSRuleList
Para acceder a un `CSSRuleList`, primero debes obtener una referencia a una hoja de estilo:

```javascript
var stylesheet = document.styleSheets[0]; // Accede a la primera hoja de estilo
var rules = stylesheet.cssRules; // Obtiene el CSSRuleList
```

## Ejemplos
### Ejemplo 1: Listar todas las reglas CSS
```javascript
var stylesheet = document.styleSheets[0];
var rules = stylesheet.cssRules;

for (var i = 0; i < rules.length; i++) {
    console.log(rules[i].cssText); // Imprime el texto de cada regla CSS
}
```

### Ejemplo 2: Modificar una regla CSS
```javascript
var stylesheet = document.styleSheets[0];
var rules = stylesheet.cssRules;

if (rules.length > 0) {
    rules[0].style.color = "red"; // Cambia el color del primer selector a rojo
}
```

### Ejemplo 3: Eliminar una regla CSS
```javascript
var stylesheet = document.styleSheets[0];
var rules = stylesheet.cssRules;

if (rules.length > 0) {
    stylesheet.deleteRule(0); // Elimina la primera regla CSS
}
```

## Explicación
- **Problemas comunes**: Un error común es intentar acceder a `cssRules` en hojas de estilo que están en un dominio diferente (cross-origin), lo que generará un error de seguridad.
- **Uso de índices**: Recuerda que los índices de las reglas comienzan en 0, por lo que la primera regla se encuentra en `rules[0]`.
- **Compatibilidad**: Asegúrate de verificar la compatibilidad entre navegadores, ya que algunas propiedades y métodos pueden no estar soportados en versiones más antiguas.

## Resumen en una línea
`CSSRuleList` permite acceder y manipular dinámicamente las reglas CSS de una hoja de estilo mediante JavaScript.