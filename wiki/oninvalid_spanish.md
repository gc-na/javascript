<!--
Meta Description: # oninvalid: Validación de formularios en JavaScript ## Sinopsis El evento `oninvalid` en JavaScript se utiliza para manejar la validación de formular...
Meta Keywords: oninvalid, evento, formulario, validación, javascript
-->

# oninvalid: Validación de formularios en JavaScript

## Sinopsis
El evento `oninvalid` en JavaScript se utiliza para manejar la validación de formularios, permitiendo a los desarrolladores personalizar la respuesta cuando un campo de formulario no cumple con los criterios de validación establecidos.

## Documentación
El evento `oninvalid` se activa en un elemento de formulario cuando se intenta enviar el formulario y uno o más campos no son válidos. Esto permite a los desarrolladores interceptar el proceso de envío y proporcionar retroalimentación personalizada al usuario.

### Propósito
El `oninvalid` es útil para mejorar la experiencia del usuario al permitir que se muestren mensajes de error específicos o se realicen ajustes visuales en el formulario antes de que se envíe.

### Uso
El evento `oninvalid` se puede asociar a un campo de formulario HTML, como un `<input>`, `<textarea>`, o `<select>`. Se define mediante el atributo `oninvalid` en el HTML o mediante JavaScript al añadir un event listener.

#### Sintaxis en HTML:
```html
<input type="text" required oninvalid="miFuncionDeError()">
```

#### Sintaxis en JavaScript:
```javascript
document.getElementById("miCampo").addEventListener("invalid", function(event) {
  // Personalización del manejo de error
});
```

## Ejemplos

### Ejemplo 1: Uso básico en HTML
```html
<form id="miFormulario">
  <input type="text" required oninvalid="alert('Por favor, complete este campo.')" />
  <input type="submit" value="Enviar" />
</form>
```

### Ejemplo 2: Uso con JavaScript
```html
<form id="miFormulario">
  <input type="email" id="email" required />
  <input type="submit" value="Enviar" />
</form>

<script>
  document.getElementById("email").addEventListener("invalid", function(event) {
    event.preventDefault(); // Previene el envío del formulario
    alert("El correo electrónico es obligatorio y debe ser válido.");
  });
</script>
```

## Explicación
Al usar el evento `oninvalid`, es importante tener en cuenta que el evento se dispara solo si el campo es inválido en el momento en que se intenta enviar el formulario. Esto significa que si se corrige el campo antes de enviar, el evento no se activará.

### Pitfalls comunes
- **Prevención del envío:** Al manejar el evento, si no se llama a `event.preventDefault()`, el formulario se enviará de todos modos, ignorando la validación personalizada.
- **Interacción con otros eventos:** Asegúrate de que no haya conflictos con otros eventos de validación como `oninput` o `onsubmit`, ya que pueden afectar el flujo de validación.

## Resumen en una línea
El evento `oninvalid` en JavaScript permite personalizar la validación de formularios, proporcionando retroalimentación específica cuando los campos no cumplen con los requisitos establecidos.