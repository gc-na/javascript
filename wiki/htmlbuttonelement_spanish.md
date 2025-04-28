<!--
Meta Description: # HTMLButtonElement: Elemento de Botón en JavaScript ## Sinopsis HTMLButtonElement es una interfaz que representa los elementos `<button>` en un docum...
Meta Keywords: botón, formulario, button, que, script
-->

# HTMLButtonElement: Elemento de Botón en JavaScript

## Sinopsis
HTMLButtonElement es una interfaz que representa los elementos `<button>` en un documento HTML y permite interactuar con ellos mediante JavaScript. Proporciona propiedades y métodos para manipular el comportamiento y estilo de los botones en aplicaciones web.

## Documentación
HTMLButtonElement es parte del DOM (Document Object Model) y se utiliza para crear botones interactivos en aplicaciones web. Los botones pueden ser utilizados para enviar formularios, ejecutar scripts de JavaScript, o como elementos de control en interfaces de usuario.

### Propiedades Principales
- **disabled**: Indica si el botón está deshabilitado. 
- **form**: Devuelve el elemento `<form>` al que pertenece el botón.
- **name**: El nombre del botón, utilizado en el envío de formularios.
- **type**: Especifica el tipo de botón, como "button", "submit", o "reset".
- **value**: El valor asignado al botón que se envía con el formulario.

### Métodos Comunes
- **click()**: Simula un clic en el botón.
- **setCustomValidity()**: Establece un mensaje de error personalizado para la validación de formularios.

## Ejemplos
### Ejemplo 1: Creación de un botón básico
```html
<button id="miBoton">Haz clic aquí</button>
<script>
  const boton = document.getElementById('miBoton');
  boton.addEventListener('click', () => {
      alert('¡Botón clicado!');
  });
</script>
```

### Ejemplo 2: Deshabilitar un botón
```html
<button id="miBoton" disabled>Botón Deshabilitado</button>
<script>
  const boton = document.getElementById('miBoton');
  setTimeout(() => {
      boton.disabled = false; // Habilita el botón después de 3 segundos
      boton.textContent = 'Ahora puedes clicarlo';
  }, 3000);
</script>
```

### Ejemplo 3: Envío de formulario
```html
<form id="miFormulario">
  <button type="submit">Enviar</button>
</form>
<script>
  const formulario = document.getElementById('miFormulario');
  formulario.addEventListener('submit', (event) => {
      event.preventDefault(); // Previene el envío del formulario
      alert('Formulario enviado.');
  });
</script>
```

## Explicación
Al trabajar con HTMLButtonElement, es importante tener en cuenta que:
- Los botones de tipo "submit" envían el formulario al que pertenecen, lo que puede llevar a un comportamiento inesperado si no se maneja adecuadamente.
- Utilizar la propiedad `disabled` no solo cambia la apariencia del botón, sino que también afecta su funcionalidad. Un botón deshabilitado no enviará datos en un formulario.
- Al utilizar `setCustomValidity()`, asegúrate de llamar a `reportValidity()` para mostrar el mensaje de error en el formulario.

## Resumen en una sola línea
HTMLButtonElement permite la creación y manipulación de botones en HTML a través de JavaScript, facilitando la interacción del usuario en aplicaciones web.