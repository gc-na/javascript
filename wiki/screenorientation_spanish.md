<!--
Meta Description: # ScreenOrientation en JavaScript: Controla la Orientación de la Pantalla en Navegadores Web ## Sinopsis `ScreenOrientation` es una API de JavaScript ...
Meta Keywords: orientación, screen, orientation, pantalla, actual
-->

# ScreenOrientation en JavaScript: Controla la Orientación de la Pantalla en Navegadores Web

## Sinopsis
`ScreenOrientation` es una API de JavaScript que permite a los desarrolladores web controlar y gestionar la orientación de la pantalla de los dispositivos móviles y tablets, mejorando así la experiencia del usuario en aplicaciones web.

## Documentación
### Propósito
La API `ScreenOrientation` proporciona información sobre la orientación actual de la pantalla y permite a los desarrolladores cambiar la orientación en tiempo real. Esto es especialmente útil en aplicaciones que requieren una visualización específica, como juegos o aplicaciones multimedia.

### Uso
Para utilizar la API `ScreenOrientation`, primero debes acceder a ella a través del objeto `screen` en el navegador. La propiedad `screen.orientation` te permite obtener información sobre la orientación actual y cambiarla si es necesario.

### Métodos Principales
- **`screen.orientation.lock(orientation)`**: Bloquea la orientación de la pantalla en el modo especificado (por ejemplo, "portrait" o "landscape").
- **`screen.orientation.unlock()`**: Libera la orientación de la pantalla, permitiendo que el dispositivo cambie entre las orientaciones permitidas.

### Propiedades Clave
- **`screen.orientation.type`**: Devuelve el tipo de orientación actual (por ejemplo, "portrait-primary", "landscape-secondary").
- **`screen.orientation.angle`**: Devuelve el ángulo actual de la pantalla en grados.

## Ejemplos
### Ejemplo 1: Bloquear la Orientación
```javascript
if (screen.orientation && screen.orientation.lock) {
    screen.orientation.lock('portrait').then(function() {
        console.log('Orientación bloqueada en modo retrato');
    }).catch(function(error) {
        console.log('Error al bloquear la orientación: ', error);
    });
}
```

### Ejemplo 2: Desbloquear la Orientación
```javascript
if (screen.orientation && screen.orientation.unlock) {
    screen.orientation.unlock();
    console.log('Orientación desbloqueada');
}
```

### Ejemplo 3: Obtener la Orientación Actual
```javascript
if (screen.orientation) {
    console.log('Orientación actual: ', screen.orientation.type);
    console.log('Ángulo actual: ', screen.orientation.angle);
}
```

## Explicación
Al usar la API `ScreenOrientation`, es importante tener en cuenta los siguientes puntos:
- No todos los navegadores soportan esta API, por lo que es recomendable verificar su disponibilidad antes de utilizarla.
- La función `lock` puede fallar si el dispositivo ya está en la orientación solicitada o si no se permite la orientación especificada.
- Al desbloquear la orientación, el dispositivo regresará a su comportamiento predeterminado, lo que puede no ser siempre lo deseado por el usuario.

## Resumen en Una Frase
`ScreenOrientation` es una API de JavaScript que permite controlar y gestionar la orientación de la pantalla en dispositivos móviles para mejorar la experiencia del usuario en aplicaciones web.