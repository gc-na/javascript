<!--
Meta Description: # ValidityState en JavaScript: Comprendiendo la Validación de Formularios ## Sinopsis `ValidityState` es una interfaz en JavaScript que proporciona in...
Meta Keywords: validity, que, email, indica, valor
-->

# ValidityState en JavaScript: Comprendiendo la Validación de Formularios

## Sinopsis
`ValidityState` es una interfaz en JavaScript que proporciona información sobre el estado de validez de un elemento de formulario, permitiendo a los desarrolladores verificar si los campos del formulario cumplen con las restricciones definidas por el HTML5.

## Documentación
La interfaz `ValidityState` es utilizada principalmente en el contexto de formularios HTML, específicamente a través de elementos de entrada (input). Cada campo de entrada tiene un objeto `ValidityState` que representa su estado de validez, proporcionando propiedades que indican si el campo es válido y si no cumple con ciertas condiciones.

### Propiedades Principales
- **valid**: Indica si el elemento es válido.
- **badInput**: Indica si el valor del campo no se puede convertir a un tipo adecuado.
- **customError**: Indica si hay un error personalizado en la validación.
- **patternMismatch**: Indica si el valor del campo no coincide con el patrón especificado.
- **rangeOverflow**: Indica si el valor es mayor que el valor máximo especificado.
- **rangeUnderflow**: Indica si el valor es menor que el valor mínimo especificado.
- **tooLong**: Indica si el valor es más largo que la longitud máxima permitida.
- **tooShort**: Indica si el valor es más corto que la longitud mínima permitida.
- **typeMismatch**: Indica si el valor no coincide con el tipo esperado (por ejemplo, un correo electrónico).

### Uso
Para utilizar `ValidityState`, debes acceder a la propiedad `validity` de un elemento de formulario. A continuación se muestra un ejemplo básico de su uso:

```javascript
const emailInput = document.querySelector('#email');

emailInput.addEventListener('input', () => {
    const validity = emailInput.validity;

    if (validity.valid) {
        console.log('El email es válido.');
    } else if (validity.typeMismatch) {
        console.log('El formato del email es incorrecto.');
    }
});
```

## Ejemplos
### Ejemplo 1: Verificación de un campo de correo electrónico

```html
<form>
    <label for="email">Email:</label>
    <input type="email" id="email" required>
    <button type="submit">Enviar</button>
</form>
<script>
    const emailInput = document.querySelector('#email');

    emailInput.addEventListener('input', () => {
        const validity = emailInput.validity;

        if (validity.valid) {
            console.log('Email válido.');
        } else if (validity.typeMismatch) {
            console.log('Por favor, introduce un email válido.');
        }
    });
</script>
```

### Ejemplo 2: Validación de longitud de texto

```html
<form>
    <label for="username">Nombre de usuario:</label>
    <input type="text" id="username" minlength="5" required>
    <button type="submit">Enviar</button>
</form>
<script>
    const usernameInput = document.querySelector('#username');

    usernameInput.addEventListener('input', () => {
        const validity = usernameInput.validity;

        if (validity.tooShort) {
            console.log('El nombre de usuario es demasiado corto.');
        }
    });
</script>
```

## Explicación
Al trabajar con `ValidityState`, es importante tener en cuenta que:
- La validación se realiza automáticamente cuando se envían los formularios, pero también puedes implementarla manualmente en eventos como `input` o `change`.
- La propiedad `validity` es solo de solo lectura; no puedes modificarla directamente.
- Asegúrate de que los atributos HTML como `required`, `minlength`, `maxlength`, y `pattern` estén correctamente establecidos para que la validación funcione como se espera.

## Resumen en Una Línea
`ValidityState` en JavaScript permite verificar el estado de validez de los campos de formulario, facilitando la validación de datos del usuario en aplicaciones web.