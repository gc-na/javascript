<!--
Meta Description: # ontransitionrun en JavaScript: Comprendiendo el Evento de Transición ## Sinopsis El evento `ontransitionrun` en JavaScript se activa cuando una tran...
Meta Keywords: transición, elemento, ontransitionrun, que, javascript
-->

# ontransitionrun en JavaScript: Comprendiendo el Evento de Transición

## Sinopsis
El evento `ontransitionrun` en JavaScript se activa cuando una transición CSS comienza a ejecutarse en un elemento, permitiendo a los desarrolladores manejar animaciones y efectos visuales de manera más dinámica.

## Documentación
El evento `ontransitionrun` es parte de la interfaz de eventos de transición en el DOM. Se utiliza para detectar el inicio de una transición CSS en un elemento HTML. Este evento es útil para ejecutar código JavaScript en el momento preciso en que una transición comienza, lo que permite crear interacciones más ricas y fluidas en aplicaciones web.

### Propósito
El propósito principal de `ontransitionrun` es permitir que los desarrolladores respondan a la activación de transiciones, lo que puede ser útil para iniciar otras animaciones, registrar información o manipular el DOM.

### Uso
El evento `ontransitionrun` se puede asignar a un elemento de la siguiente manera:

```javascript
elemento.ontransitionrun = function(event) {
    // Código a ejecutar cuando la transición comienza
};
```

Alternativamente, se puede utilizar `addEventListener` para agregar un manejador de eventos:

```javascript
elemento.addEventListener('transitionrun', function(event) {
    // Código a ejecutar cuando la transición comienza
});
```

## Ejemplos

### Ejemplo básico
```html
<div id="miCaja" style="width: 100px; height: 100px; background-color: red; transition: background-color 1s;"></div>
<button id="cambiarColor">Cambiar Color</button>

<script>
    const caja = document.getElementById('miCaja');
    const boton = document.getElementById('cambiarColor');

    caja.addEventListener('transitionrun', function() {
        console.log('La transición ha comenzado.');
    });

    boton.addEventListener('click', function() {
        caja.style.backgroundColor = 'blue';
    });
</script>
```

### Ejemplo con múltiples transiciones
```javascript
const elemento = document.getElementById('miElemento');

elemento.addEventListener('transitionrun', function(event) {
    console.log('Transición en curso: ' + event.propertyName);
});

elemento.style.transition = 'all 0.5s ease';
elemento.style.transform = 'translateX(100px)';
```

## Explicación
Al utilizar `ontransitionrun`, es importante tener en cuenta las siguientes consideraciones:

1. **Compatibilidad**: Asegúrate de que el navegador en el que se ejecuta tu aplicación sea compatible con los eventos de transición. La mayoría de los navegadores modernos son compatibles, pero siempre es bueno verificar en [Can I use](https://caniuse.com).

2. **Múltiples transiciones**: Si un elemento tiene varias propiedades que están siendo animadas, el evento `ontransitionrun` se disparará por cada propiedad que comience a cambiar.

3. **Prevención de efectos no deseados**: Si no se maneja adecuadamente, el uso de transiciones y animaciones puede causar parpadeos o efectos inesperados en la interfaz de usuario. Asegúrate de probar y ajustar tu código.

## Resumen en una línea
`ontransitionrun` es un evento en JavaScript que se activa al iniciar una transición CSS, permitiendo a los desarrolladores ejecutar código en ese momento crítico.