<!--
Meta Description: # onbeforeinput: Evento Crucial para Manejar Cambios en Entradas en JavaScript ## Sinopsis El evento `onbeforeinput` en JavaScript permite interceptar...
Meta Keywords: que, evento, event, entrada, onbeforeinput
-->

# onbeforeinput: Evento Crucial para Manejar Cambios en Entradas en JavaScript

## Sinopsis
El evento `onbeforeinput` en JavaScript permite interceptar y gestionar los cambios en los campos de entrada antes de que estos se reflejen en el valor del elemento. Es útil para validar o modificar el contenido que el usuario intenta ingresar.

## Documentación
El evento `onbeforeinput` se activa antes de que se produzca un cambio en un campo de entrada, lo que permite a los desarrolladores realizar acciones como la validación del contenido, la modificación del texto o la cancelación de la acción de entrada.

### Propósito
Su propósito principal es proporcionar un punto de intervención antes de que el valor de un input sea modificado, ofreciendo así una oportunidad para realizar validaciones o transformaciones.

### Uso
Para utilizar el evento `onbeforeinput`, se puede añadir un listener directo a un elemento de entrada, como un `<input>` o un `<textarea>`. Este evento es particularmente útil en formularios donde se necesita asegurar que los datos ingresados cumplen con ciertos criterios.

### Detalles
- **Tipo de evento**: `Event`
- **Soporte en navegadores**: Compatible con la mayoría de los navegadores modernos (Chrome, Firefox, Safari, Edge).
- **Propiedades del evento**: Proporciona detalles sobre el tipo de cambio que se está solicitando, incluyendo el texto que se va a insertar o eliminar.

## Ejemplos
### Ejemplo 1: Cancelar la entrada si no es un número
```html
<input type="text" id="miInput" onbeforeinput="validarEntrada(event)" placeholder="Ingrese solo números">
<script>
  function validarEntrada(event) {
    const valorIngresado = event.data;
    if (isNaN(valorIngresado)) {
      event.preventDefault(); // Cancela la entrada
      alert("Solo se permiten números.");
    }
  }
</script>
```

### Ejemplo 2: Transformar texto a mayúsculas
```html
<input type="text" id="miInput" onbeforeinput="convertirAMayusculas(event)" placeholder="Ingrese texto">
<script>
  function convertirAMayusculas(event) {
    if (event.data) {
      event.preventDefault(); // Cancela la entrada original
      document.getElementById('miInput').value += event.data.toUpperCase(); // Inserta en mayúsculas
    }
  }
</script>
```

## Explicación
Al usar `onbeforeinput`, es importante tener en cuenta que el evento se activa antes de que el valor del input cambie, lo que significa que cualquier modificación que se realice en este evento debe ser cuidadosamente gestionada. Un error común es no cancelar la entrada cuando se desea controlar el texto, lo que puede resultar en entradas no deseadas. Además, es crucial asegurarse de que el código se ejecute en navegadores compatibles, ya que el soporte puede variar.

## Resumen en una línea
El evento `onbeforeinput` permite gestionar cambios en los campos de entrada antes de que se reflejen, facilitando la validación y modificación del contenido ingresado por el usuario.