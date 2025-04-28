<!--
Meta Description: # onsubmit: Manejo de Eventos de Envío en JavaScript ## Sinopsis El evento `onsubmit` en JavaScript permite manejar la acción de envío de un formulari...
Meta Keywords: onsubmit, envío, formulario, javascript, del
-->

# onsubmit: Manejo de Eventos de Envío en JavaScript

## Sinopsis
El evento `onsubmit` en JavaScript permite manejar la acción de envío de un formulario, facilitando la validación de datos y la ejecución de funciones antes de que el formulario sea procesado por el servidor.

## Documentación
### Propósito
El evento `onsubmit` se utiliza para ejecutar una función cuando un formulario se envía. Esto es útil para validar datos de entrada, prevenir envíos de formularios no deseados y realizar tareas como la recopilación de datos o la manipulación del DOM antes de que el formulario se procese.

### Uso
El evento `onsubmit` se puede asignar a un formulario HTML utilizando el atributo `onsubmit` o mediante JavaScript. La función asociada se ejecutará cuando el usuario intente enviar el formulario. Si la función devuelve `false`, el envío del formulario se cancelará.

#### Ejemplo de HTML:
```html
<form id="miFormulario" onsubmit="return validarFormulario()">
  <input type="text" name="nombre" required>
  <input type="submit" value="Enviar">
</form>
```

#### Ejemplo de JavaScript:
```javascript
document.getElementById('miFormulario').onsubmit = function() {
  return validarFormulario();
};

function validarFormulario() {
  // Lógica de validación
  return true; // o false para cancelar el envío
}
```

## Ejemplos
### Ejemplo Básico de Validación
```html
<form id="miFormulario" onsubmit="return validar()">
  <input type="text" id="nombre" required>
  <input type="submit" value="Enviar">
</form>

<script>
function validar() {
  var nombre = document.getElementById('nombre').value;
  if (nombre === "") {
    alert("El nombre no puede estar vacío.");
    return false; // Cancela el envío
  }
  return true; // Permite el envío
}
</script>
```

### Ejemplo de Prevención de Envío
```html
<form id="miFormulario">
  <input type="text" required>
  <input type="submit" value="Enviar">
</form>

<script>
document.getElementById('miFormulario').onsubmit = function(event) {
  event.preventDefault(); // Cancela el envío del formulario
  console.log("El envío del formulario ha sido cancelado.");
};
</script>
```

## Explicación
Al usar `onsubmit`, es importante tener en cuenta:

- **Devolución de Valor**: Si la función del evento `onsubmit` devuelve `false`, el navegador no enviará el formulario. Esto es útil para la validación.
- **Múltiples Formas**: Se puede asignar el evento utilizando JavaScript o HTML, pero se recomienda usar JavaScript para una mejor separación de la lógica y la presentación.
- **Eventos de Prevención**: Usar `event.preventDefault()` es una práctica común si se desea evitar el comportamiento predeterminado del envío del formulario sin depender de la devolución de `false`.

## Resumen en Una Línea
El evento `onsubmit` en JavaScript permite gestionar el envío de formularios, facilitando la validación y control de datos antes de su envío.