<!--
Meta Description: # Evento Focus en JavaScript: Comprendiendo FocusEvent ## Sinopsis El evento Focus en JavaScript, representado por el objeto `FocusEvent`, se utiliza ...
Meta Keywords: foco, evento, focusevent, elemento, que
-->

# Evento Focus en JavaScript: Comprendiendo FocusEvent

## Sinopsis
El evento Focus en JavaScript, representado por el objeto `FocusEvent`, se utiliza para detectar cuando un elemento de la interfaz de usuario recibe el foco. Este evento es crucial para mejorar la accesibilidad y la interactividad en aplicaciones web.

## Documentación
El objeto `FocusEvent` es un tipo de evento que se activa cuando un elemento gana o pierde el foco. Existen dos eventos principales relacionados con `FocusEvent`:

- `focus`: Se dispara cuando un elemento recibe el foco.
- `blur`: Se dispara cuando un elemento pierde el foco.

### Propósito
El propósito principal de `FocusEvent` es permitir a los desarrolladores manejar la interactividad de los elementos de formularios, botones y otros componentes de la interfaz de usuario en respuesta a la acción del usuario.

### Uso
Para usar `FocusEvent`, puedes agregar un listener de eventos a un elemento HTML utilizando `addEventListener`. Aquí hay un ejemplo básico:

```javascript
const inputElement = document.getElementById('mi-input');

inputElement.addEventListener('focus', function() {
    console.log('El elemento ha recibido el foco.');
});

inputElement.addEventListener('blur', function() {
    console.log('El elemento ha perdido el foco.');
});
```

### Detalles
El objeto `FocusEvent` proporciona algunas propiedades útiles, tales como:

- `relatedTarget`: El elemento que está relacionado con el evento, es decir, el elemento que está perdiendo o ganando el foco.
- `bubbles`: Un valor booleano que indica si el evento se propaga hacia arriba a través de la jerarquía de elementos.

## Ejemplos
### Ejemplo 1: Captura de evento de enfoque
```html
<input type="text" id="nombre" placeholder="Ingrese su nombre">
<script>
    const inputNombre = document.getElementById('nombre');
    
    inputNombre.addEventListener('focus', () => {
        console.log('Campo de nombre enfocado.');
    });
</script>
```

### Ejemplo 2: Captura de evento de desenfoque
```html
<input type="text" id="email" placeholder="Ingrese su email">
<script>
    const inputEmail = document.getElementById('email');
    
    inputEmail.addEventListener('blur', () => {
        console.log('Campo de email desenfocado.');
    });
</script>
```

## Explicación
Al trabajar con `FocusEvent`, es importante considerar que:

- **No todos los elementos pueden recibir foco**: Solo elementos interactivos como `<input>`, `<button>`, y `<a>` son susceptibles de recibir foco.
- **Manejo de múltiples elementos**: Si tienes varios elementos que requieren seguimiento de enfoque, asegúrate de agregar listeners a cada uno de ellos de manera adecuada.
- **Accesibilidad**: Usar eventos de enfoque correctamente puede mejorar la accesibilidad de tu sitio web, permitiendo que los usuarios naveguen fácilmente usando el teclado.

## Resumen en una línea
El evento Focus en JavaScript, representado por `FocusEvent`, permite detectar cuando los elementos reciben o pierden el foco, mejorando la interactividad y accesibilidad en aplicaciones web.