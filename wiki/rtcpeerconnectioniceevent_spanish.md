<!--
Meta Description: # RTCPeerConnectionIceEvent en JavaScript: Todo lo que necesitas saber ## Sinopsis El evento `RTCPeerConnectionIceEvent` en JavaScript es fundamental ...
Meta Keywords: candidatos, que, los, rtcpeerconnectioniceevent, ice
-->

# RTCPeerConnectionIceEvent en JavaScript: Todo lo que necesitas saber

## Sinopsis
El evento `RTCPeerConnectionIceEvent` en JavaScript es fundamental en la gestión de la conectividad en WebRTC, permitiendo la manipulación de los estados de ICE (Interactive Connectivity Establishment) en conexiones de pares.

## Documentación
`RTCPeerConnectionIceEvent` es un evento que se produce en el contexto de `RTCPeerConnection` cuando se recibe un cambio en el estado del proceso de recolección de candidatos ICE. Este evento proporciona información valiosa sobre los candidatos de red que se utilizan para establecer conexiones en tiempo real.

### Propósito
El propósito de `RTCPeerConnectionIceEvent` es notificar a los desarrolladores sobre los candidatos ICE que se han encontrado durante el proceso de conexión. Es crucial para aplicaciones que requieren comunicación en tiempo real, como videoconferencias y llamadas de voz.

### Uso
Para escuchar los eventos de tipo `RTCPeerConnectionIceEvent`, se debe añadir un manejador de eventos al objeto `RTCPeerConnection`. A continuación, se presenta un ejemplo básico de cómo hacerlo.

## Ejemplos
### Ejemplo Básico
```javascript
// Crear una nueva conexión de pares
const peerConnection = new RTCPeerConnection();

// Añadir un manejador para el evento ICE
peerConnection.addEventListener('icecandidate', event => {
    if (event.candidate) {
        console.log('Nuevo candidato ICE encontrado:', event.candidate);
    } else {
        console.log('Todos los candidatos han sido enviados.');
    }
});

// Crear una oferta y enviarla
peerConnection.createOffer().then(offer => {
    return peerConnection.setLocalDescription(offer);
}).then(() => {
    console.log('Oferta local establecida.');
}).catch(error => {
    console.error('Error al crear la oferta:', error);
});
```

### Ejemplo con múltiples candidatos
```javascript
peerConnection.addEventListener('icecandidate', event => {
    if (event.candidate) {
        // Aquí podrías enviar el candidato al otro par
        console.log('Candidato ICE enviado:', event.candidate);
    }
});
```

## Explicación
Al trabajar con `RTCPeerConnectionIceEvent`, es importante tener en cuenta algunos puntos:

1. **Múltiples Candidatos**: El evento puede dispararse múltiples veces, una por cada candidato encontrado. Es crucial manejar todos los candidatos de manera adecuada.
  
2. **Candidatos Nulos**: Cuando el evento se dispara sin un candidato (es decir, `event.candidate` es `null`), significa que se han enviado todos los candidatos posibles. Esto es un indicativo de que el proceso de recolección de candidatos ha finalizado.

3. **Compatibilidad**: Asegúrate de que tu aplicación maneje correctamente la compatibilidad entre navegadores, ya que la implementación de WebRTC puede variar.

## Resumen en una línea
`RTCPeerConnectionIceEvent` en JavaScript permite la gestión eficiente de candidatos ICE en conexiones WebRTC, vital para la conectividad en tiempo real.