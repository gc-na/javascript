<!--
Meta Description: # onfocus: Manejo de Eventos de Enfoque en JavaScript ## Sinopsis El evento `onfocus` en JavaScript es una propiedad que se usa para detectar cuando u...
Meta Keywords: onfocus, evento, que, script, del
-->

# onfocus: Manejo de Eventos de Enfoque en JavaScript

## Sinopsis
El evento `onfocus` en JavaScript es una propiedad que se usa para detectar cuando un elemento de formulario, como un campo de entrada, recibe el foco. Este evento es esencial para mejorar la experiencia del usuario, ya que permite realizar acciones específicas al interactuar con elementos de la interfaz.

## Documentación
El evento `onfocus` se activa cuando un elemento se convierte en el objetivo del foco. Esto puede suceder cuando el usuario hace clic en un campo de entrada o navega a él mediante la tecla Tab. Es importante notar que el evento `onfocus` no se propaga, lo que significa que no se puede capturar en los elementos padres.

### Propósito
El propósito principal del evento `onfocus` es permitir que los desarrolladores realicen acciones específicas cuando un elemento de formulario recibe el foco, como mostrar información adicional, cambiar el estilo del elemento o realizar validaciones.

### Uso
Para utilizar el evento `onfocus`, puedes asignarlo directamente en el HTML o a través de JavaScript. A continuación se presentan ejemplos de ambas metodologías.

## Ejemplos

### Ejemplo 1: Uso en HTML
```html
<input type="text" id="miCampo" onfocus="mostrarMensaje()">
<script>
function mostrarMensaje() {
    alert("Campo de texto enfocado");
}
</script>
```

### Ejemplo 2: Uso en JavaScript
```html
<input type="text" id="miCampo">
<script>
document.getElementById('miCampo').onfocus = function() {
    alert("Campo de texto enfocado");
};
</script>
```

### Ejemplo 3: Uso con jQuery
```html
<input type="text" id="miCampo">
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script>
$(document).ready(function() {
    $('#miCampo').focus(function() {
        alert("Campo de texto enfocado");
    });
});
</script>
```

## Explicación
A pesar de su simplicidad, hay algunos aspectos que es importante considerar al utilizar `onfocus`:

- **No Propagación**: A diferencia de otros eventos, `onfocus` no se propaga a los elementos padres. Si intentas manejarlo en un contenedor, no funcionará.
- **Compatibilidad**: Este evento es compatible con todos los navegadores modernos, pero siempre es recomendable realizar pruebas en diferentes navegadores.
- **Interacción del Usuario**: Asegúrate de que el uso de este evento no interrumpa la experiencia del usuario, como mostrar mensajes emergentes con frecuencia.
- **Uso con `onblur`**: A menudo se usa en conjunto con el evento `onblur`, que se activa cuando el elemento pierde el foco.

## Resumen en una Línea
El evento `onfocus` en JavaScript permite detectar cuando un elemento recibe el foco, lo que permite realizar acciones interactivas y mejorar la experiencia del usuario.