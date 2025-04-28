<!--
Meta Description: # onkeypress en JavaScript: Manejo de Eventos de Teclado ## Sinopsis El evento `onkeypress` en JavaScript permite detectar cuando una tecla es presion...
Meta Keywords: onkeypress, event, que, evento, del
-->

# onkeypress en JavaScript: Manejo de Eventos de Teclado

## Sinopsis
El evento `onkeypress` en JavaScript permite detectar cuando una tecla es presionada en un elemento interactivo del DOM, como un campo de texto. Este evento es útil para implementar funcionalidades que dependen de la entrada del usuario a través del teclado.

## Documentación
El evento `onkeypress` se utiliza para capturar el momento exacto en que una tecla es presionada mientras se está enfocado en un elemento. Este evento se puede asignar a cualquier elemento HTML que soporte la entrada del usuario, como `<input>`, `<textarea>` o incluso `<div>`.

### Propósito
La principal finalidad del evento `onkeypress` es permitir a los desarrolladores responder a la entrada del usuario, facilitando la creación de interfaces más interactivas y dinámicas.

### Uso
Para utilizar `onkeypress`, se puede asignar el evento directamente en el HTML o mediante JavaScript. Aquí hay un ejemplo de cómo se puede implementar:

#### HTML
```html
<input type="text" id="miInput" onkeypress="miFuncion(event)">
```

#### JavaScript
```javascript
function miFuncion(event) {
    console.log('Tecla presionada: ' + String.fromCharCode(event.which));
}
```

### Detalles
- `event.which` devuelve el código de la tecla que fue presionada.
- El evento `onkeypress` solo se activa con teclas que generan un carácter, lo que significa que no se disparará para teclas como `Shift`, `Ctrl` o `Alt`.
- Para teclas que no generan caracteres, se recomienda usar `onkeydown` o `onkeyup`.

## Ejemplos
### Ejemplo 1: Captura de caracteres
```html
<input type="text" id="inputTexto" onkeypress="mostrarCaracter(event)">
<script>
function mostrarCaracter(event) {
    console.log('Carácter ingresado: ' + String.fromCharCode(event.which));
}
</script>
```

### Ejemplo 2: Validación de entrada
```html
<input type="text" id="inputNumero" onkeypress="validarNumero(event)">
<script>
function validarNumero(event) {
    if (event.which < 48 || event.which > 57) {
        event.preventDefault(); // Evita que se ingresen caracteres que no sean números
    }
}
</script>
```

## Explicación
### Errores comunes y notas
- **Uso inadecuado de `onkeypress`**: Recuerda que `onkeypress` no se ejecuta para teclas de control. Para detectar la pulsación de cualquier tecla, es mejor utilizar `onkeydown` o `onkeyup`.
- **Compatibilidad**: `onkeypress` es un evento obsoleto en algunos navegadores modernos. Se recomienda utilizar `onkeydown` o `onkeyup` para asegurar la compatibilidad en el futuro.
- **Prevención de eventos**: Para evitar que la acción predeterminada del evento se ejecute, se puede utilizar `event.preventDefault()`.

## Resumen en una línea
El evento `onkeypress` de JavaScript permite detectar la pulsación de teclas en elementos del DOM, facilitando la interacción del usuario con aplicaciones web.