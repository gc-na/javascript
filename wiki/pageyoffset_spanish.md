<!--
Meta Description: # pageYOffset en JavaScript: Comprendiendo el Desplazamiento Vertical de la Página ## Sinopsis `pageYOffset` es una propiedad en JavaScript que permit...
Meta Keywords: desplazamiento, pageyoffset, que, window, javascript
-->

# pageYOffset en JavaScript: Comprendiendo el Desplazamiento Vertical de la Página

## Sinopsis
`pageYOffset` es una propiedad en JavaScript que permite obtener la cantidad de píxeles que el documento se ha desplazado verticalmente desde la parte superior de la página.

## Documentación
La propiedad `pageYOffset` pertenece al objeto `window` y devuelve un valor numérico que representa el desplazamiento vertical de la ventana de visualización. Este valor es útil para determinar la posición actual de desplazamiento del usuario, lo que puede ser aprovechado en aplicaciones que requieren un cambio de comportamiento basado en la posición de desplazamiento.

### Uso
```javascript
let desplazamientoVertical = window.pageYOffset;
```

- **Tipo de datos**: `number`
- **Valor devuelto**: La cantidad de píxeles que se han desplazado desde la parte superior de la página. Si no hay desplazamiento, el valor será `0`.

## Ejemplos

### Ejemplo 1: Obtener el Desplazamiento Vertical
```javascript
window.onscroll = function() {
    console.log("Desplazamiento vertical: " + window.pageYOffset + " píxeles");
};
```

### Ejemplo 2: Cambiar el Estilo de un Elemento Basado en el Desplazamiento
```javascript
window.onscroll = function() {
    let elemento = document.getElementById("miElemento");
    if (window.pageYOffset > 100) {
        elemento.style.backgroundColor = "red";
    } else {
        elemento.style.backgroundColor = "blue";
    }
};
```

## Explicación
Algunos puntos a considerar al trabajar con `pageYOffset`:

- **Compatibilidad del Navegador**: `pageYOffset` es compatible con la mayoría de los navegadores modernos. Sin embargo, en navegadores más antiguos, podrías necesitar usar `document.body.scrollTop` como alternativa.
  
- **Uso Conjuntamente con scroll**: La propiedad `pageYOffset` es especialmente útil cuando se combina con eventos de desplazamiento (`scroll`). Puedes ejecutar funciones en respuesta al desplazamiento del usuario en la página.

- **Desplazamiento Horizontal**: Si necesitas obtener el desplazamiento horizontal, puedes usar `window.pageXOffset`.

- **Rendimiento**: Escuchar eventos de desplazamiento puede afectar el rendimiento si se manejan de manera ineficiente. Considera usar técnicas como el "debounce" o "throttle" para limitar la frecuencia de las llamadas a la función.

## Resumen en una Línea
`pageYOffset` es una propiedad de JavaScript que devuelve el número de píxeles que se ha desplazado verticalmente en la página desde la parte superior.