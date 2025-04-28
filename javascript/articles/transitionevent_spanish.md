<!--
Meta Description: # Evento de Transición (TransitionEvent) en JavaScript: Todo lo que Necesitas Saber ## Sinopsis El evento de transición (TransitionEvent) en JavaScrip...
Meta Keywords: que, evento, css, transición, elemento
-->

# Evento de Transición (TransitionEvent) en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
El evento de transición (TransitionEvent) en JavaScript permite a los desarrolladores gestionar las animaciones CSS de forma efectiva, proporcionando información sobre el inicio y la finalización de las transiciones CSS en los elementos del DOM.

## Documentación
### Propósito
El `TransitionEvent` es un tipo de evento que se activa cuando una transición CSS de un elemento ha comenzado o ha finalizado. Su principal propósito es permitir a los desarrolladores responder a los cambios en las propiedades CSS que se están animando, mejorando así la interactividad y la experiencia del usuario en aplicaciones web.

### Uso
Para usar el `TransitionEvent`, primero debes asegurarte de que tu elemento tiene una transición CSS definida en su estilo. Luego, puedes agregar un event listener que escuche por el evento `transitionend`, que es el evento que se disparará cuando una transición CSS completa su ejecución.

### Detalles
- **Propiedades del Evento**:
  - `propertyName`: El nombre de la propiedad CSS que ha cambiado.
  - `elapsedTime`: El tiempo que ha transcurrido desde que comenzó la transición.
  - `pseudoElement`: El pseudo-elemento en el que se produjo el evento (si corresponde).
  
- **Método de Escucha**:
  Puedes utilizar `addEventListener` para escuchar el evento `transitionend`.

## Ejemplos
### Ejemplo Básico
```javascript
const elemento = document.querySelector('.miElemento');

elemento.addEventListener('transitionend', (evento) => {
    console.log(`La transición de ${evento.propertyName} ha terminado.`);
});

// Aplicar una transición CSS
elemento.style.transition = 'opacity 2s';
elemento.style.opacity = '0';
```

### Ejemplo con Múltiples Transiciones
```javascript
const box = document.querySelector('.caja');

box.addEventListener('transitionend', (event) => {
    console.log(`La transición de ${event.propertyName} ha terminado.`);
});

box.style.transition = 'width 1s, height 1s';
box.style.width = '200px';
box.style.height = '200px';
```

## Explicación
Al trabajar con `TransitionEvent`, es fundamental tener en cuenta que el evento se dispara una vez para cada propiedad que ha cambiado. Si aplicas múltiples transiciones a un elemento, recibirás un evento `transitionend` para cada una de ellas. Además, asegúrate de que las propiedades CSS definidas en la transición realmente cambien; de lo contrario, el evento no se disparará.

Algunos errores comunes incluyen:
- No definir correctamente las propiedades CSS que se desean animar.
- No añadir el listener de eventos antes de cambiar el estilo del elemento, lo que puede llevar a perder el evento.

## Resumen en Una Línea
El `TransitionEvent` en JavaScript permite gestionar las transiciones CSS en elementos del DOM, proporcionando información sobre el inicio y finalización de estas animaciones.