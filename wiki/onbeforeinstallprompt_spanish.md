<!--
Meta Description: # onbeforeinstallprompt: Manejo de la Instalación de Aplicaciones Web Progresivas en JavaScript ## Sinopsis El evento `onbeforeinstallprompt` es parte...
Meta Keywords: instalación, evento, que, banner, usuario
-->

# onbeforeinstallprompt: Manejo de la Instalación de Aplicaciones Web Progresivas en JavaScript

## Sinopsis
El evento `onbeforeinstallprompt` es parte de la API de Instalación de Aplicaciones Web Progresivas (PWA) en JavaScript. Permite a los desarrolladores controlar cuándo y cómo se muestra el mensaje para instalar una PWA, mejorando así la experiencia del usuario.

## Documentación
El evento `onbeforeinstallprompt` se dispara cuando el navegador está a punto de mostrar el banner que invita al usuario a instalar la aplicación web progresiva. Este evento proporciona una oportunidad para personalizar la experiencia de instalación y decidir si y cuándo mostrar el banner.

### Propósito
El propósito principal del evento `onbeforeinstallprompt` es dar a los desarrolladores un control más granular sobre el proceso de instalación de su PWA. Permite a los desarrolladores retrasar la aparición del banner hasta que el usuario esté listo para instalar la aplicación.

### Uso
Para utilizar el evento `onbeforeinstallprompt`, se debe agregar un event listener al objeto `window`. Este listener capturará el evento y permitirá a los desarrolladores manejarlo adecuadamente.

### Detalles
- **Evento**: `beforeinstallprompt`
- **Propiedades**:
  - `prompt()`: Método que muestra el banner de instalación.
  - `userChoice`: Propiedad que devuelve una promesa que se resuelve cuando el usuario elige aceptar o rechazar la instalación.

## Ejemplos

### Ejemplo Básico
```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
    // Previene que el banner de instalación se muestre automáticamente
    e.preventDefault();
    // Guarda el evento para usarlo más tarde
    deferredPrompt = e;
    
    // Muestra un botón personalizado para solicitar la instalación
    const installButton = document.getElementById('installButton');
    installButton.style.display = 'block';

    installButton.addEventListener('click', () => {
        // Muestra el banner de instalación
        deferredPrompt.prompt();
        
        // Espera la respuesta del usuario
        deferredPrompt.userChoice.then((choiceResult) => {
            if (choiceResult.outcome === 'accepted') {
                console.log('El usuario aceptó la instalación');
            } else {
                console.log('El usuario rechazó la instalación');
            }
            deferredPrompt = null; // Resetea el evento
        });
    });
});
```

## Explicación
Es importante tener en cuenta que el evento `onbeforeinstallprompt` solo se dispara en ciertas condiciones, como cuando la PWA cumple con los requisitos de instalación y se accede a través de un contexto seguro (HTTPS). 

### Errores Comunes
1. **No manejar el evento**: No agregar un listener para `beforeinstallprompt` resultará en que el banner se muestre automáticamente, lo que puede no ser deseado.
2. **Usar HTTP en lugar de HTTPS**: Las PWAs deben servirse a través de HTTPS para que el evento se dispare.
3. **No mostrar el banner en el momento adecuado**: Es recomendable esperar a que el usuario haya interactuado con la aplicación antes de mostrar el banner de instalación.

## Resumen en Una Línea
El evento `onbeforeinstallprompt` permite a los desarrolladores controlar cuándo mostrar el banner de instalación de una PWA, mejorando la experiencia del usuario en JavaScript.