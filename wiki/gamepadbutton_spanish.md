<!--
Meta Description: # GamepadButton en JavaScript: Interacción con Controladores de Videojuegos ## Sinopsis `GamepadButton` es una interfaz en JavaScript que permite a lo...
Meta Keywords: gamepad, botones, que, los, gamepads
-->

# GamepadButton en JavaScript: Interacción con Controladores de Videojuegos

## Sinopsis
`GamepadButton` es una interfaz en JavaScript que permite a los desarrolladores acceder y manejar los botones de un gamepad conectado al navegador, facilitando la creación de experiencias de juego interactivas en la web.

## Documentación
La interfaz `GamepadButton` forma parte de la API Gamepad, que se utiliza para detectar y responder a las entradas de los controladores de videojuegos. Cada objeto `GamepadButton` representa un botón específico en el gamepad y proporciona información sobre su estado, como si está presionado o no, y su nivel de presión.

### Propiedades Principales
- **pressed**: Un booleano que indica si el botón está actualmente presionado.
- **value**: Un número entre 0 y 1 que indica el nivel de presión del botón, aplicable principalmente a los botones analógicos.

### Uso
Para utilizar `GamepadButton`, primero debes acceder a la lista de gamepads conectados utilizando `navigator.getGamepads()`. Luego, puedes iterar a través de los gamepads y sus botones para detectar presiones y acciones.

```javascript
window.addEventListener("gamepadconnected", (event) => {
    console.log("Gamepad conectado:", event.gamepad);
});

function checkGamepadStatus() {
    const gamepads = navigator.getGamepads();
    for (let i = 0; i < gamepads.length; i++) {
        if (gamepads[i]) {
            const buttons = gamepads[i].buttons;
            buttons.forEach((button, index) => {
                if (button.pressed) {
                    console.log(`Botón ${index} presionado: ${button.value}`);
                }
            });
        }
    }
}

setInterval(checkGamepadStatus, 100);
```

## Ejemplos
### Ejemplo Básico de Detección de Botones
```javascript
window.addEventListener("gamepadconnected", (event) => {
    console.log("Gamepad conectado:", event.gamepad);
    const gamepad = event.gamepad;
    
    // Verificar el estado de los botones
    setInterval(() => {
        const buttons = gamepad.buttons;
        buttons.forEach((button, index) => {
            if (button.pressed) {
                console.log(`Botón ${index} está presionado.`);
            }
        });
    }, 100);
});
```

### Ejemplo de Uso del Valor de Presión
```javascript
window.addEventListener("gamepadconnected", (event) => {
    const gamepad = event.gamepad;

    setInterval(() => {
        const button = gamepad.buttons[0]; // Primer botón
        if (button.pressed) {
            console.log(`Botón 0 presionado con fuerza: ${button.value}`);
        }
    }, 100);
});
```

## Explicación
Al trabajar con `GamepadButton`, es importante recordar que la detección de gamepads y botones puede no ser instantánea. Asegúrate de manejar correctamente la conexión y desconexión de gamepads. Además, ten en cuenta que algunos navegadores pueden tener diferentes niveles de soporte para la API Gamepad, por lo que es recomendable probar en varios entornos.

### Errores Comunes
- **No verificar la conexión del gamepad**: Asegúrate de que un gamepad esté conectado antes de intentar acceder a sus botones.
- **Ignorar el valor de presión**: No todos los botones reportan un valor de presión. Asegúrate de manejar correctamente los botones que solo devuelven un estado booleano.

## Resumen en una Línea
`GamepadButton` permite acceder y gestionar los botones de un gamepad en JavaScript, facilitando interacciones en experiencias de juego en la web.