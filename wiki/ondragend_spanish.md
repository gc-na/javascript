<!--
Meta Description: # Evento ondragend en JavaScript: Manejo de Finalización de Arrastre ## Sinopsis El evento `ondragend` en JavaScript se utiliza para detectar cuando u...
Meta Keywords: ondragend, que, evento, elemento, html
-->

# Evento ondragend en JavaScript: Manejo de Finalización de Arrastre

## Sinopsis
El evento `ondragend` en JavaScript se utiliza para detectar cuando un elemento que ha sido arrastrado finaliza su movimiento, lo que permite ejecutar acciones específicas al soltar el elemento.

## Documentación
El evento `ondragend` se activa cuando se libera un elemento que se está arrastrando. Este evento es parte de la API de arrastre de HTML5 y se puede utilizar en elementos que tienen el atributo `draggable` establecido en `true`.

### Propósito
El propósito principal del evento `ondragend` es proporcionar un mecanismo para manejar la lógica necesaria después de que un usuario suelta un elemento en una ubicación válida o en una superficie de destino.

### Uso
Para utilizar este evento, debes seguir estos pasos:

1. Asegúrate de que el elemento que deseas arrastrar tenga el atributo `draggable` establecido en `true`.
2. Asigna un controlador de eventos para `ondragend` al elemento arrastrable.
3. Dentro del controlador, define las acciones que deseas realizar al finalizar el arrastre.

### Detalles
- **Sintaxis**: 
  ```javascript
  element.ondragend = function(event) {
      // Código a ejecutar al finalizar el arrastre
  };
  ```
- **Propiedades del evento**: El evento proporciona información sobre el arrastre, como la posición del puntero del mouse y el elemento que se está moviendo.

## Ejemplos

### Ejemplo Básico
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejemplo ondragend</title>
    <style>
        #drag-item {
            width: 100px;
            height: 100px;
            background-color: blue;
            color: white;
            text-align: center;
            line-height: 100px;
            cursor: move;
        }
    </style>
</head>
<body>
    <div id="drag-item" draggable="true">Arrástrame</div>

    <script>
        const dragItem = document.getElementById('drag-item');

        dragItem.ondragend = function(event) {
            alert('Arrastre finalizado');
        };
    </script>
</body>
</html>
```

### Ejemplo con Más Detalles
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejemplo Completo ondragend</title>
    <style>
        #drag-item {
            width: 100px;
            height: 100px;
            background-color: green;
            color: white;
            text-align: center;
            line-height: 100px;
            cursor: move;
        }
        #drop-area {
            width: 200px;
            height: 200px;
            border: 2px dashed red;
            margin-top: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    </style>
</head>
<body>
    <div id="drag-item" draggable="true">Arrástrame</div>
    <div id="drop-area">Zona de caída</div>

    <script>
        const dragItem = document.getElementById('drag-item');
        const dropArea = document.getElementById('drop-area');

        dragItem.ondragend = function(event) {
            if (event.target === dropArea) {
                alert('Elemento soltado en la zona de caída');
            } else {
                alert('Elemento soltado fuera de la zona de caída');
            }
        };
    </script>
</body>
</html>
```

## Explicación
Al utilizar el evento `ondragend`, es importante tener en cuenta que este solo se activa una vez que se libera el botón del mouse. Algunas trampas comunes incluyen:

- **No asignar el atributo `draggable`**: Asegúrate de que el elemento arrastrable tenga el atributo `draggable="true"`; de lo contrario, el evento no se activará.
- **Confusión con otros eventos**: Los eventos `ondrag`, `ondragenter`, y `ondragleave` son diferentes y no deben confundirse con `ondragend`.

## Resumen en Una Frase
El evento `ondragend` en JavaScript permite ejecutar funciones específicas cuando un elemento arrastrado se suelta, facilitando la interacción dinámica en aplicaciones web.