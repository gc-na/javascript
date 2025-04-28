<!--
Meta Description: # onanimationiteration: Manejo de Eventos de Animación en JavaScript ## Sinopsis `onanimationiteration` es un evento de JavaScript que se activa cada ...
Meta Keywords: animación, evento, que, onanimationiteration, una
-->

# onanimationiteration: Manejo de Eventos de Animación en JavaScript

## Sinopsis
`onanimationiteration` es un evento de JavaScript que se activa cada vez que una animación CSS completa un ciclo. Este evento es útil para ejecutar funciones o lógica adicional en respuesta a la repetición de una animación.

## Documentación
El evento `onanimationiteration` forma parte de la interfaz `Element` en el DOM y se utiliza para detectar cuando una animación CSS ha terminado un ciclo. Permite a los desarrolladores ejecutar código en cada iteración de la animación, lo que es útil en situaciones donde se desea realizar cambios en la interfaz de usuario o la lógica del programa en función de las animaciones.

### Propósito
El principal propósito de `onanimationiteration` es proporcionar un punto de anclaje para ejecutar código JavaScript durante la ejecución de animaciones. Esto es especialmente valioso en aplicaciones web interactivas donde las animaciones juegan un rol importante en la experiencia del usuario.

### Uso
Para utilizar `onanimationiteration`, se debe asignar una función manejadora al evento en un elemento que tenga una animación CSS aplicada. Esto se puede hacer directamente en JavaScript o mediante atributos en el HTML.

### Detalles
- El evento se dispara cada vez que una animación CSS definida utilizando la propiedad `animation` se repite.
- Se puede utilizar junto con otros eventos de animación como `onanimationstart` y `onanimationend`.
- El evento puede ser escuchado directamente en un elemento o mediante la propiedad `addEventListener`.

## Ejemplos

### Ejemplo básico usando `onanimationiteration`
```html
<div id="miElemento" class="animacion"></div>

<style>
.animacion {
    width: 100px;
    height: 100px;
    background-color: red;
    animation: cambioColor 2s infinite;
}

@keyframes cambioColor {
    0% { background-color: red; }
    50% { background-color: blue; }
    100% { background-color: red; }
}
</style>

<script>
const elemento = document.getElementById('miElemento');

elemento.onanimationiteration = function() {
    console.log('La animación ha completado un ciclo.');
};
</script>
```

### Ejemplo usando `addEventListener`
```html
<div id="miElemento" class="animacion"></div>

<style>
.animacion {
    width: 100px;
    height: 100px;
    background-color: green;
    animation: mover 1s infinite;
}

@keyframes mover {
    0% { transform: translateX(0); }
    100% { transform: translateX(100px); }
}
</style>

<script>
const elemento = document.getElementById('miElemento');

elemento.addEventListener('animationiteration', function() {
    console.log('La animación ha repetido un ciclo.');
});
</script>
```

## Explicación
Al utilizar `onanimationiteration`, es importante tener en cuenta que:
- Si la animación está configurada para no repetirse, el evento no se disparará.
- Las animaciones que se detienen o se cancelan antes de completar su ciclo no desencadenarán el evento.
- Si se utilizan múltiples animaciones en un solo elemento, el evento se activará por cada animación que complete un ciclo, lo que puede resultar en múltiples disparos del evento.

## Resumen en una línea
`onanimationiteration` es un evento de JavaScript que se activa cada vez que una animación CSS finaliza un ciclo, permitiendo ejecutar código en respuesta.