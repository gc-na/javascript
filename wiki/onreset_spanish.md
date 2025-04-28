<!--
Meta Description: # onreset en JavaScript: Manejo de eventos de reinicio en formularios ## Sinopsis El evento `onreset` en JavaScript se utiliza para detectar y manejar...
Meta Keywords: onreset, formulario, evento, javascript, type
-->

# onreset en JavaScript: Manejo de eventos de reinicio en formularios

## Sinopsis
El evento `onreset` en JavaScript se utiliza para detectar y manejar el restablecimiento de un formulario, permitiendo ejecutar funciones o acciones específicas cuando el usuario decide reiniciar los campos de un formulario.

## Documentación
El evento `onreset` se activa cuando se llama al método `reset()` de un formulario HTML, lo que provoca que todos los campos del formulario se restablezcan a sus valores iniciales. Este evento es útil para implementar lógica personalizada cuando un usuario decide limpiar los datos ingresados en el formulario.

### Propósito
El propósito del evento `onreset` es permitir a los desarrolladores ejecutar código JavaScript específico en respuesta a la acción de reinicio de un formulario, mejorando la experiencia del usuario y ofreciendo funcionalidades adicionales.

### Uso
Para utilizar el evento `onreset`, se puede agregar un manejador de eventos en el formulario utilizando JavaScript. Esto se puede hacer de varias maneras, incluyendo el uso de atributos HTML directamente en la etiqueta del formulario o mediante la asignación de un evento en JavaScript.

#### Ejemplo de uso en HTML
```html
<form id="miFormulario" onreset="miFuncion()">
    <input type="text" name="nombre" placeholder="Nombre">
    <input type="email" name="correo" placeholder="Correo">
    <button type="reset">Reiniciar</button>
</form>
```

#### Ejemplo de uso en JavaScript
```javascript
document.getElementById("miFormulario").onsubmit = function() {
    console.log("Formulario enviado");
};

document.getElementById("miFormulario").onreset = function() {
    console.log("Formulario reiniciado");
};
```

## Ejemplos
1. **Ejemplo básico de `onreset` en HTML:**
   ```html
   <form onreset="alert('El formulario ha sido reiniciado.')">
       <input type="text" placeholder="Ingrese su nombre">
       <button type="reset">Reiniciar</button>
   </form>
   ```

2. **Ejemplo con JavaScript:**
   ```html
   <form id="formularioEjemplo">
       <input type="text" placeholder="Nombre">
       <input type="text" placeholder="Apellido">
       <button type="reset">Reiniciar</button>
   </form>

   <script>
       document.getElementById("formularioEjemplo").onreset = function() {
           console.log("Se ha reiniciado el formulario.");
       };
   </script>
   ```

## Explicación
### Errores comunes
- **No agregar el evento correctamente:** Asegúrese de que el evento `onreset` esté correctamente asignado al formulario. Si no se establece, no se ejecutará el código deseado.
- **Ignorar el método `reset()`:** Algunos desarrolladores pueden olvidar que el evento `onreset` se activa solo a través del botón de reinicio o el método `reset()`, no por la simple eliminación de valores de los campos.

### Notas adicionales
- Recuerde que el evento `onreset` se puede utilizar para validar datos o realizar un seguimiento de las interacciones del usuario al restablecer formularios.
- En navegadores modernos, el evento `onreset` puede ser manejado también mediante `addEventListener`, lo que proporciona una forma más flexible de añadir manejadores de eventos.

## Resumen en una línea
El evento `onreset` en JavaScript permite ejecutar código específico cuando un formulario es reiniciado, mejorando la interacción del usuario con formularios en aplicaciones web.