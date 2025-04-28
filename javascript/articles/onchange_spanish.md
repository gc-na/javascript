<!--
Meta Description: # Evento onchange en JavaScript: Guía Completa ## Sinopsis El evento `onchange` en JavaScript se utiliza para detectar y gestionar cambios en los elem...
Meta Keywords: onchange, evento, html, javascript, para
-->

# Evento onchange en JavaScript: Guía Completa

## Sinopsis
El evento `onchange` en JavaScript se utiliza para detectar y gestionar cambios en los elementos de formulario, como `<input>`, `<select>` y `<textarea>`. Este evento se activa cuando el valor de un elemento ha cambiado y el enfoque ha sido perdido.

## Documentación
El evento `onchange` se asocia a los elementos de un formulario y permite ejecutar código JavaScript cuando el usuario realiza un cambio en el valor de dicho elemento. Es especialmente útil en formularios interactivos, donde se desea responder a la entrada del usuario inmediatamente después de que hayan completado un campo.

### Propósito
El propósito del evento `onchange` es proporcionar una forma de gestionar las interacciones del usuario y actualizar la interfaz de usuario o realizar cálculos en función de la entrada del usuario.

### Uso
Para utilizar el evento `onchange`, se puede agregar directamente en el HTML mediante el atributo `onchange`, o mediante JavaScript utilizando `addEventListener`. Aquí hay un ejemplo de ambos métodos:

#### En HTML
```html
<input type="text" onchange="miFuncion()" />
```

#### En JavaScript
```javascript
document.getElementById('miInput').addEventListener('change', miFuncion);
```

### Detalles
- El evento `onchange` solo se activa cuando el campo pierde el enfoque (por ejemplo, al hacer clic en otro elemento).
- Para elementos `<input>` de tipo `checkbox` y `radio`, el evento se activa al cambiar su estado.
- No se activa para cambios programáticos en el valor del elemento; solo para cambios hechos directamente por el usuario.

## Ejemplos
### Ejemplo 1: Uso básico con un campo de texto
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo onchange</title>
</head>
<body>
    <input type="text" id="miInput" onchange="alert('El valor ha cambiado a: ' + this.value)" />
</body>
</html>
```

### Ejemplo 2: Uso con un elemento select
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Ejemplo onchange</title>
</head>
<body>
    <select id="miSelect" onchange="alert('Seleccionaste: ' + this.value)">
        <option value="opcion1">Opción 1</option>
        <option value="opcion2">Opción 2</option>
    </select>
</body>
</html>
```

## Explicación
### Problemas Comunes
- **No se activa en tiempo real**: A diferencia de otros eventos como `oninput`, `onchange` no se activa mientras se escribe. Solo se activa al perder el enfoque.
- **Elementos no soportados**: Algunos elementos, como `<div>` o `<span>`, no soportan el evento `onchange`, ya que no son interactivos de la misma manera que los formularios.

### Notas Adicionales
- Para un comportamiento más dinámico, considera usar el evento `oninput`, que se activa inmediatamente al cambiar el valor.
- Asegúrate de que tu código JavaScript esté correctamente vinculado y no haya errores de sintaxis para que el evento funcione como se espera.

## Resumen en Una Línea
El evento `onchange` en JavaScript se utiliza para gestionar cambios en los elementos de formularios, activándose al perder el enfoque después de que el usuario ha modificado un valor.