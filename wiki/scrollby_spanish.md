<!--
Meta Description: # scrollBy: Desplazamiento Personalizado en JavaScript ## Sinopsis El método `scrollBy` en JavaScript permite desplazar la posición de desplazamiento ...
Meta Keywords: desplazamiento, scrollby, elemento, que, javascript
-->

# scrollBy: Desplazamiento Personalizado en JavaScript

## Sinopsis
El método `scrollBy` en JavaScript permite desplazar la posición de desplazamiento de un elemento o del documento en la ventana del navegador, en relación a su posición actual. Es una herramienta útil para crear animaciones y efectos de desplazamiento suaves en aplicaciones web.

## Documentación
### Propósito
`scrollBy` se utiliza para desplazar el contenido visible en la ventana del navegador o en un elemento específico, sin necesidad de calcular la posición absoluta. Esto es especialmente útil para crear interacciones dinámicas en la interfaz de usuario.

### Uso
El método `scrollBy` se invoca en un objeto de tipo `Window` o `Element`. Su sintaxis es la siguiente:

```javascript
window.scrollBy(x, y);
```

#### Parámetros
- **x**: (número) Desplazamiento horizontal en píxeles. Puede ser positivo (hacia la derecha) o negativo (hacia la izquierda).
- **y**: (número) Desplazamiento vertical en píxeles. Puede ser positivo (hacia abajo) o negativo (hacia arriba).

### Detalles
- `scrollBy` no devuelve un valor.
- El desplazamiento se aplica a la posición de desplazamiento actual, lo que significa que puedes llamar a este método varias veces para crear un efecto de desplazamiento continuo.
- El método se puede utilizar en elementos HTML individuales, así como en la ventana global, lo que permite diferentes contextos de desplazamiento.

## Ejemplos
### Ejemplo Básico
Desplazar la ventana del navegador 100 píxeles hacia abajo y 50 píxeles hacia la derecha:

```javascript
window.scrollBy(50, 100);
```

### Ejemplo con Elemento
Desplazar un elemento específico 20 píxeles hacia arriba:

```javascript
const elemento = document.getElementById('miElemento');
elemento.scrollBy(0, -20);
```

### Ejemplo de Desplazamiento Suave
Para lograr un desplazamiento suave, se puede utilizar `scrollBy` en combinación con `setTimeout` o `requestAnimationFrame`:

```javascript
function desplazarSuave() {
    window.scrollBy(0, 5);
    if (window.scrollY < 500) {
        requestAnimationFrame(desplazarSuave);
    }
}
desplazarSuave();
```

## Explicación
### Errores Comunes
- **Valores de desplazamiento excesivos**: Si se utilizan valores muy altos para `x` o `y`, es posible que el desplazamiento no sea perceptible o que cause un efecto abrupto.
- **Uso en elementos no desplazables**: Intentar usar `scrollBy` en un elemento que no tiene barra de desplazamiento visible no producirá efecto alguno.

### Notas Adicionales
- `scrollBy` se basa en el sistema de coordenadas del navegador, por lo que es importante tener en cuenta el tamaño y la posición del viewport.
- Para un desplazamiento más controlado, considera usar `scrollTo`, que permite especificar la posición absoluta.

## Resumen en Una Línea
El método `scrollBy` en JavaScript permite desplazar el contenido visible de la ventana o de un elemento en relación a su posición actual, facilitando la creación de efectos de desplazamiento dinámicos.