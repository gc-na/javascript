<!--
Meta Description: # ondragleave: Evento de arrastre en JavaScript ## Sinopsis El evento `ondragleave` en JavaScript se activa cuando un elemento que se está arrastrando...
Meta Keywords: ondragleave, evento, área, elemento, del
-->

# ondragleave: Evento de arrastre en JavaScript

## Sinopsis
El evento `ondragleave` en JavaScript se activa cuando un elemento que se está arrastrando sale del área de un elemento objetivo. Este evento es fundamental para implementar interacciones de arrastre y soltar en aplicaciones web.

## Documentación
El evento `ondragleave` es parte de la API de arrastre de HTML5 y se utiliza para manejar situaciones donde un elemento arrastrado deja el área de un elemento que puede recibirlo. Este evento se puede utilizar en cualquier elemento HTML, pero es más común en aquellos que tienen la capacidad de recibir elementos arrastrados, como `div`, `section`, o `form`.

### Propósito
El propósito del evento `ondragleave` es notificar a los desarrolladores cuando un objeto arrastrado ha salido del área de un elemento, permitiendo realizar acciones específicas, como cambiar estilos, mostrar mensajes o realizar una limpieza de estado.

### Uso
Para utilizar el evento `ondragleave`, se debe asignar un controlador de eventos a un elemento HTML. Esto se puede hacer de varias maneras, ya sea mediante atributos HTML o utilizando JavaScript.

**Ejemplo de uso básico en HTML:**
```html
<div id="drop-area" ondragleave="handleDragLeave()">
    Arrastra un archivo aquí
</div>
```

**Ejemplo de uso básico en JavaScript:**
```javascript
const dropArea = document.getElementById('drop-area');

dropArea.ondragleave = function(event) {
    console.log('El objeto arrastrado ha salido del área de recepción.');
};
```

## Ejemplos
### Ejemplo 1: Cambio de estilo al salir
```html
<div id="drop-area" style="width: 300px; height: 200px; border: 2px dashed #ccc;">
    Arrastra algo aquí
</div>

<script>
    const dropArea = document.getElementById('drop-area');

    dropArea.ondragover = (event) => {
        event.preventDefault(); // Permitir el arrastre
        dropArea.style.borderColor = 'green'; // Cambiar el borde al arrastrar
    };

    dropArea.ondragleave = () => {
        dropArea.style.borderColor = '#ccc'; // Restablecer el borde al salir
    };
</script>
```

### Ejemplo 2: Mensaje al salir
```html
<div id="drop-area" style="width: 300px; height: 200px; border: 2px solid #000;">
    Arrastra algo aquí
</div>
<div id="message"></div>

<script>
    const dropArea = document.getElementById('drop-area');
    const message = document.getElementById('message');

    dropArea.ondragleave = () => {
        message.textContent = 'Has salido del área de arrastre.';
    };
</script>
```

## Explicación
Al trabajar con el evento `ondragleave`, es importante recordar que este evento solo se activa cuando el objeto arrastrado sale completamente del área del elemento objetivo. Si el objeto se mueve dentro del área, no se disparará el evento. Además, es crucial prevenir el comportamiento predeterminado utilizando `event.preventDefault()` en el evento `ondragover` para asegurar que el área acepte los elementos arrastrados.

### Errores comunes
- No usar `event.preventDefault()` en `ondragover`, lo que puede hacer que no se active el área de recepción.
- Suponer que `ondragleave` se activará al mover el ratón dentro del área, cuando en realidad solo se activa al salir completamente.

## Resumen en una línea
El evento `ondragleave` en JavaScript se activa cuando un elemento arrastrado sale del área de un elemento objetivo, permitiendo gestionar interacciones de arrastre de manera efectiva.