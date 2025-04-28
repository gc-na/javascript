<!--
Meta Description: # Uso de alert en JavaScript: Cómo mostrar mensajes emergentes ## Sinopsis El comando `alert` en JavaScript permite mostrar un cuadro de diálogo modal...
Meta Keywords: alert, usuario, que, javascript, del
-->

# Uso de alert en JavaScript: Cómo mostrar mensajes emergentes

## Sinopsis
El comando `alert` en JavaScript permite mostrar un cuadro de diálogo modal con un mensaje y un botón de aceptar. Es una herramienta útil para proporcionar retroalimentación al usuario, advertencias o información importante de manera sencilla y rápida.

## Documentación
El método `alert` es parte del objeto global `window` en JavaScript. Su propósito principal es mostrar un mensaje al usuario en una ventana emergente. Este cuadro de diálogo detiene la ejecución del código hasta que el usuario hace clic en el botón "Aceptar".

### Sintaxis
```javascript
alert(mensaje);
```

### Parámetros
- **mensaje**: (String) El texto que se desea mostrar en el cuadro de diálogo. Este puede ser texto simple o cualquier expresión que devuelva una cadena.

### Uso
El método `alert` se utiliza comúnmente en situaciones donde se necesita informar al usuario sobre un evento, como errores o confirmaciones. A pesar de su simplicidad, su uso debe ser moderado, ya que puede interrumpir la experiencia del usuario.

## Ejemplos
### Ejemplo básico
```javascript
alert("¡Bienvenido a nuestra página web!");
```

### Ejemplo con una variable
```javascript
let nombre = "Juan";
alert("Hola, " + nombre + "!");
```

### Ejemplo con un número
```javascript
let edad = 25;
alert("Tienes " + edad + " años.");
```

## Explicación
Aunque `alert` es fácil de usar, puede presentar algunos inconvenientes:

- **Interrupción de la experiencia del usuario**: El cuadro de diálogo modal bloquea la interacción con la página hasta que el usuario lo cierre, lo que puede ser molesto si se usa en exceso.
- **Limitaciones de diseño**: No se puede personalizar el estilo del cuadro de diálogo, lo que puede no coincidir con la estética de la aplicación.
- **Incompatibilidad en dispositivos móviles**: En algunos navegadores móviles, la aparición de una ventana emergente puede variar y afectar la interacción del usuario.

Es recomendable utilizar `alert` para mensajes importantes que realmente requieran la atención del usuario. Para notificaciones menos intrusivas, se pueden considerar alternativas como notificaciones en la página o bibliotecas de terceros.

## Resumen en una frase
El método `alert` en JavaScript permite mostrar mensajes emergentes al usuario de forma sencilla, interrumpiendo la ejecución del código hasta que se confirme la alerta.