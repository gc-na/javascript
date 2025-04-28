<!--
Meta Description: # DOMTokenList: Manejo de Clases y Tokens en JavaScript ## Sinopsis `DOMTokenList` es una interfaz en JavaScript que permite gestionar listas de token...
Meta Keywords: elemento, que, clase, clases, javascript
-->

# DOMTokenList: Manejo de Clases y Tokens en JavaScript

## Sinopsis
`DOMTokenList` es una interfaz en JavaScript que permite gestionar listas de tokens, comúnmente utilizados para manejar clases de elementos HTML y atributos. Proporciona métodos para añadir, eliminar y verificar la existencia de tokens, facilitando la manipulación de las clases de los elementos del DOM.

## Documentación
`DOMTokenList` es una propiedad que se encuentra en elementos del DOM, particularmente en el atributo `classList` de los elementos HTML. Su propósito principal es simplificar la manipulación de las clases CSS asociadas a un elemento, permitiendo operaciones como añadir, eliminar o comprobar la existencia de una clase sin necesidad de gestionar manualmente las cadenas de texto.

### Propiedades y Métodos Principales
- **`add(token)`**: Añade uno o más tokens a la lista.
- **`remove(token)`**: Elimina uno o más tokens de la lista.
- **`toggle(token)`**: Añade el token si no existe, o lo elimina si ya está presente.
- **`contains(token)`**: Devuelve `true` si el token existe en la lista, de lo contrario `false`.
- **`length`**: Propiedad que devuelve el número total de tokens en la lista.

### Uso
Para utilizar `DOMTokenList`, primero debes acceder a la propiedad `classList` de un elemento HTML. Por ejemplo:

```javascript
let elemento = document.getElementById("miElemento");
let listaClases = elemento.classList;
```

## Ejemplos

### Añadir Clases
```javascript
let elemento = document.getElementById("miElemento");
elemento.classList.add("nueva-clase");
```

### Eliminar Clases
```javascript
let elemento = document.getElementById("miElemento");
elemento.classList.remove("clase-a-eliminar");
```

### Comprobar la Existencia de una Clase
```javascript
let elemento = document.getElementById("miElemento");
if (elemento.classList.contains("clase-a-comprobar")) {
    console.log("La clase existe.");
} else {
    console.log("La clase no existe.");
}
```

### Alternar Clases
```javascript
let elemento = document.getElementById("miElemento");
elemento.classList.toggle("clase-a-alternar");
```

## Explicación
Al utilizar `DOMTokenList`, es fundamental recordar que los métodos como `add`, `remove` y `toggle` pueden aceptar múltiples argumentos, lo que permite modificar varias clases a la vez. Sin embargo, es importante tener en cuenta que los nombres de clase son sensibles a mayúsculas y minúsculas, por lo que "Clase" y "clase" se consideran diferentes.

Otro aspecto a considerar es que `classList` no es compatible con versiones muy antiguas de navegadores, por lo que se recomienda verificar la compatibilidad si se trabaja en un entorno que soporte navegadores obsoletos.

## Resumen en una línea
`DOMTokenList` es una interfaz en JavaScript que facilita la manipulación de listas de tokens, como las clases CSS, permitiendo añadir, eliminar y verificar clases de manera eficiente.