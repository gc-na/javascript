<!--
Meta Description: # scrollTo: Desplazamiento suave en JavaScript ## Sinopsis El método `scrollTo` en JavaScript permite desplazar la posición de desplazamiento de la ve...
Meta Keywords: scrollto, desplazamiento, javascript, método, que
-->

# scrollTo: Desplazamiento suave en JavaScript

## Sinopsis
El método `scrollTo` en JavaScript permite desplazar la posición de desplazamiento de la ventana o un elemento específico a una ubicación determinada en la página, facilitando la navegación y mejorando la experiencia del usuario.

## Documentación
### Propósito
El método `scrollTo` se utiliza para desplazar la posición de desplazamiento de la ventana del navegador o de un elemento HTML a unas coordenadas específicas en la página. Este método es especialmente útil para implementar desplazamientos suaves y llevar al usuario a secciones específicas de un documento.

### Uso
El método `scrollTo` puede ser utilizado en el objeto `window` o en elementos específicos de la página. La sintaxis básica es la siguiente:

```javascript
window.scrollTo(x, y);
```

O, para un desplazamiento suave:

```javascript
window.scrollTo({
  top: y,
  left: x,
  behavior: 'smooth'
});
```

Donde:
- `x` es la posición horizontal en píxeles a la que se quiere desplazar.
- `y` es la posición vertical en píxeles a la que se quiere desplazar.
- `behavior` es un parámetro opcional que puede ser `'auto'` (predeterminado) o `'smooth'`, que indica si el desplazamiento debe ser instantáneo o suave.

### Detalles
- `scrollTo` es un método de nivel de ventana que puede ser usado en cualquier documento HTML.
- Se puede aplicar a elementos con desplazamiento para moverlos a posiciones específicas dentro de su contenedor.
- Este método es compatible con la mayoría de los navegadores modernos, incluyendo Chrome, Firefox, Safari y Edge.

## Ejemplos
### Ejemplo 1: Desplazamiento a una posición específica
```javascript
// Desplaza la ventana a 200 píxeles hacia abajo.
window.scrollTo(0, 200);
```

### Ejemplo 2: Desplazamiento suave a una posición específica
```javascript
// Desplaza la ventana a 500 píxeles hacia abajo de forma suave.
window.scrollTo({
  top: 500,
  left: 0,
  behavior: 'smooth'
});
```

### Ejemplo 3: Desplazamiento a un elemento específico
```javascript
const element = document.getElementById('miElemento');
element.scrollTo({
  top: element.offsetTop,
  behavior: 'smooth'
});
```

## Explicación
- **Problemas comunes**: Uno de los errores más comunes al usar `scrollTo` es no tener en cuenta el contexto del desplazamiento. Si se aplica a un elemento que no tiene un overflow adecuado, el desplazamiento no tendrá efecto.
- **Compatibilidad**: `scrollTo` con el comportamiento `'smooth'` puede no estar soportado en navegadores más antiguos, así que se recomienda verificar la compatibilidad o proporcionar una solución alternativa.
- **Desplazamiento relativo**: Para un desplazamiento relativo (en lugar de absoluto), se puede usar el método `scrollBy`.

## Resumen en una línea
El método `scrollTo` en JavaScript permite desplazar la ventana o un elemento a coordenadas específicas, mejorando la navegación en páginas web.