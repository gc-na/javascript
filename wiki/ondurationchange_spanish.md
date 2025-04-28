<!--
Meta Description: # Evento `ondurationchange` en JavaScript: Manejo de Cambios en la Duración de Medios ## Sinopsis El evento `ondurationchange` en JavaScript permite a...
Meta Keywords: video, ondurationchange, evento, duración, html
-->

# Evento `ondurationchange` en JavaScript: Manejo de Cambios en la Duración de Medios

## Sinopsis
El evento `ondurationchange` en JavaScript permite a los desarrolladores detectar cambios en la duración de un elemento multimedia (como un video o audio) cuando se carga o se modifica. Este evento es esencial para aplicaciones que requieren una interacción dinámica con contenido multimedia.

## Documentación
### ¿Qué es `ondurationchange`?
El evento `ondurationchange` se activa cuando la duración de un elemento `<audio>` o `<video>` ha cambiado. Esto puede ocurrir cuando un archivo multimedia se carga inicialmente o si el archivo se modifica en tiempo de ejecución.

### Propósito
El propósito de este evento es permitir a los desarrolladores ejecutar código específico en respuesta a cambios en la duración de un medio. Esto es especialmente útil para actualizar la interfaz de usuario o para sincronizar otras acciones en la aplicación.

### Uso
Para utilizar el evento `ondurationchange`, primero debes seleccionar el elemento multimedia en tu documento HTML y luego agregar un manejador de eventos que ejecute la lógica deseada cuando se produzca el evento.

### Sintaxis
```javascript
elemento.onDurationChange = function() {
    // Lógica a ejecutar cuando cambie la duración
};
```

## Ejemplos
### Ejemplo Básico
A continuación se muestra un ejemplo básico de cómo utilizar `ondurationchange`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo de ondurationchange</title>
</head>
<body>
    <video id="miVideo" width="640" height="360" controls>
        <source src="video.mp4" type="video/mp4">
        Tu navegador no soporta el video.
    </video>
    <p id="duracion">Duración: 0 segundos</p>

    <script>
        const video = document.getElementById('miVideo');
        const duracionTexto = document.getElementById('duracion');

        video.ondurationchange = function() {
            duracionTexto.textContent = `Duración: ${video.duration} segundos`;
        };
    </script>
</body>
</html>
```

### Ejemplo Avanzado
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo Avanzado de ondurationchange</title>
</head>
<body>
    <video id="miVideo" width="640" height="360" controls>
        <source src="video.mp4" type="video/mp4">
        Tu navegador no soporta el video.
    </video>
    <p id="duracion">Duración: 0 segundos</p>
    <button id="cargarNuevo">Cargar Nuevo Video</button>

    <script>
        const video = document.getElementById('miVideo');
        const duracionTexto = document.getElementById('duracion');
        const nuevoVideoBtn = document.getElementById('cargarNuevo');

        video.ondurationchange = function() {
            duracionTexto.textContent = `Duración: ${video.duration} segundos`;
        };

        nuevoVideoBtn.onclick = function() {
            video.src = "nuevo_video.mp4"; // Cambia la fuente del video
            video.load(); // Carga el nuevo video
        };
    </script>
</body>
</html>
```

## Explicación
### Errores Comunes
1. **No Detectar Cambios**: Asegúrate de que el archivo de medios esté completamente cargado para que el evento `ondurationchange` se active. Si el archivo no se carga correctamente, el evento podría no dispararse.
2. **Uso Incorrecto de Propiedades**: Al acceder a `video.duration`, recuerda que puede devolver `NaN` si el video no ha sido cargado adecuadamente.
3. **Compatibilidad del Navegador**: Verifica la compatibilidad del navegador, ya que algunos navegadores pueden comportarse de manera diferente respecto a este evento.

## Resumen en Una Línea
El evento `ondurationchange` en JavaScript permite detectar cambios en la duración de elementos multimedia, facilitando la interacción dinámica con el contenido.