<!--
Meta Description: # WakeLock en JavaScript: Mantén la Pantalla Activa en Aplicaciones Web ## Sinopsis WakeLock es una API de JavaScript que permite a los desarrolladore...
Meta Keywords: wakelock, que, pantalla, wake, lock
-->

# WakeLock en JavaScript: Mantén la Pantalla Activa en Aplicaciones Web

## Sinopsis
WakeLock es una API de JavaScript que permite a los desarrolladores web prevenir que la pantalla del dispositivo se apague, asegurando que el contenido sea visible para el usuario. Esta funcionalidad es especialmente útil en aplicaciones web que requieren interacción continua, como juegos o aplicaciones de presentación.

## Documentación

### Propósito
La API WakeLock está diseñada para mantener la pantalla de un dispositivo activa, evitando que entre en modo de reposo. Esto es crucial en situaciones donde los usuarios necesitan interactuar constantemente con la aplicación y no pueden permitirse que la pantalla se apague.

### Uso
Para utilizar WakeLock, se debe solicitar un "wake lock" al navegador. El proceso involucra la creación de un objeto `WakeLock`, que se puede activar y desactivar según las necesidades de la aplicación. 

#### Sintaxis Básica
```javascript
const wakeLock = await navigator.wakeLock.request('screen');
```

### Detalles
1. **Tipos de WakeLock**: Actualmente, la API admite principalmente el "screen wake lock", que mantiene la pantalla activa.
2. **Manejo de Errores**: Es importante manejar los errores, ya que el usuario puede denegar el permiso para mantener la pantalla activa.
3. **Liberar WakeLock**: Después de que la tarea que requiere el wake lock ha terminado, se debe liberar para permitir que el dispositivo vuelva a su estado normal.

## Ejemplos

### Ejemplo Básico de Uso
```javascript
async function activateWakeLock() {
    try {
        const wakeLock = await navigator.wakeLock.request('screen');
        console.log('Wake Lock activado');

        // Liberar el wake lock después de un tiempo o cuando ya no se necesite
        setTimeout(async () => {
            await wakeLock.release();
            console.log('Wake Lock liberado');
        }, 60000); // Liberar después de 60 segundos
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

activateWakeLock();
```

### Ejemplo con Manejo de Eventos
```javascript
let wakeLock = null;

async function requestWakeLock() {
    try {
        wakeLock = await navigator.wakeLock.request('screen');
        console.log('Wake Lock activado');
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

function releaseWakeLock() {
    if (wakeLock) {
        wakeLock.release();
        wakeLock = null;
        console.log('Wake Lock liberado');
    }
}

document.addEventListener('visibilitychange', async () => {
    if (document.visibilityState === 'visible') {
        await requestWakeLock();
    } else {
        releaseWakeLock();
    }
});
```

## Explicación
### Puntos Comunes a Considerar
- **Compatibilidad del Navegador**: No todos los navegadores son compatibles con la API WakeLock. Verifica la compatibilidad antes de implementar.
- **Consentimiento del Usuario**: En algunos casos, el usuario debe otorgar permiso explícito para que la aplicación mantenga la pantalla activa.
- **Desempeño de la Batería**: Mantener la pantalla encendida puede afectar la duración de la batería del dispositivo. Es recomendable utilizar esta función con moderación y liberarla cuando ya no sea necesaria.

## Resumen en Una Línea
La API WakeLock de JavaScript permite a las aplicaciones web prevenir que la pantalla se apague, mejorando la experiencia del usuario en interacciones continuas.