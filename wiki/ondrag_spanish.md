<!--
Meta Description: # Evento ondrag en JavaScript: Controlando el Arrastre de Elementos ## Sinopsis El evento `ondrag` en JavaScript permite a los desarrolladores gestion...
Meta Keywords: ondrag, evento, html, draggable, div
-->

# Evento ondrag en JavaScript: Controlando el Arrastre de Elementos

## Sinopsis
El evento `ondrag` en JavaScript permite a los desarrolladores gestionar la acción de arrastrar un elemento dentro de una página web. Este evento es parte de la API de arrastre y soltar (Drag and Drop), proporcionando una experiencia interactiva para los usuarios.

## Documentación
### Propósito
El evento `ondrag` se activa cuando un elemento está siendo arrastrado. Es utilizado en aplicaciones web para mejorar la interactividad, permitiendo a los usuarios mover elementos visuales, como imágenes o divs, dentro de la interfaz.

### Uso
Para utilizar el evento `ondrag`, primero es necesario habilitar la capacidad de arrastre en un elemento HTML. Esto se logra configurando el atributo `draggable` a `true`. Luego, se puede asignar una función al evento `ondrag` para manejar la lógica deseada.

#### Sintaxis básica
```html
<div id="miElemento" draggable="true" ondrag="miFuncion(event)">Arrástrame</div>
```

### Detalles
- **draggable**: Este atributo debe estar presente y configurado a `true` para que el evento `ondrag` funcione.
- **event**: El objeto del evento que contiene información sobre el elemento que se está arrastrando y el contexto del arrastre.

## Ejemplos
### Ejemplo 1: Evento ondrag básico
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de ondrag</title>
    <script>
        function mostrarMensaje(event) {
            console.log("Estás arrastrando el elemento!");
        }
    </script>
</head>
<body>
    <div id="miElemento" draggable="true" ondrag="mostrarMensaje(event)" style="width: 100px; height: 100px; background-color: coral;">
        Arrástrame
    </div>
</body>
</html>
```

### Ejemplo 2: Manejo de varios elementos
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de ondrag múltiples</title>
    <script>
        function moverElemento(event) {
            let elemento = event.target;
            console.log("Arrastrando: " + elemento.id);
        }
    </script>
</head>
<body>
    <div id="elemento1" draggable="true" ondrag="moverElemento(event)" style="width: 50px; height: 50px; background-color: blue;"></div>
    <div id="elemento2" draggable="true" ondrag="moverElemento(event)" style="width: 50px; height: 50px; background-color: green;"></div>
</body>
</html>
```

## Explicación
### Errores comunes y notas importantes
- **No establecer draggable**: Si no se configura el atributo `draggable` a `true`, el evento `ondrag` no se activará.
- **Uso del evento ondrag sin ondragstart**: Aunque `ondrag` se puede usar solo, es recomendable implementar también el evento `ondragstart` para manejar la lógica de inicio del arrastre.
- **Accesibilidad**: Asegúrate de que tu implementación del arrastre no interfiera con la accesibilidad para usuarios que dependen de teclado o lectores de pantalla.

## Resumen en una línea
El evento `ondrag` en JavaScript permite gestionar el arrastre de elementos en una página web, mejorando la interactividad y la experiencia del usuario.