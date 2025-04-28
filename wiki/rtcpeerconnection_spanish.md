<!--
Meta Description: # RTCPeerConnection en JavaScript: Guía Completa sobre la Conectividad en Tiempo Real ## Sinopsis RTCPeerConnection es una interfaz clave de la API We...
Meta Keywords: rtcpeerconnection, javascript, una, los, ice
-->

# RTCPeerConnection en JavaScript: Guía Completa sobre la Conectividad en Tiempo Real

## Sinopsis
RTCPeerConnection es una interfaz clave de la API WebRTC en JavaScript, diseñada para facilitar la comunicación de audio, video y datos en tiempo real entre navegadores.

## Documentación
### Propósito
RTCPeerConnection es fundamental para establecer conexiones peer-to-peer en aplicaciones web que requieren comunicación en tiempo real. Permite a los navegadores intercambiar medios y datos de manera eficiente y segura.

### Uso
Para utilizar RTCPeerConnection, primero se debe crear una instancia de esta clase. Posteriormente, se pueden agregar flujos de medios, manejar ICE candidates, y establecer conexiones con otros pares.

```javascript
const peerConnection = new RTCPeerConnection(configuration);
```

#### Parámetros:
- `configuration`: Un objeto que contiene la configuración del servidor STUN/TURN, por ejemplo:
  ```javascript
  const configuration = {
      iceServers: [
          { urls: 'stun:stun.l.google.com:19302' },
          { urls: 'turn:turnserver.example.com', username: 'user', credential: 'pass' }
      ]
  };
  ```

### Métodos Clave
- **addTrack(track, stream)**: Añade una pista de medios a la conexión.
- **createOffer()**: Crea una oferta SDP para establecer la conexión.
- **setLocalDescription(description)**: Establece la descripción local (oferta o respuesta).
- **setRemoteDescription(description)**: Establece la descripción remota.
- **onicecandidate**: Maneja el evento de candidatos ICE.

## Ejemplos
### Ejemplo Básico de Conexión
```javascript
const configuration = {
    iceServers: [{ urls: 'stun:stun.l.google.com:19302' }]
};

const peerConnection = new RTCPeerConnection(configuration);

// Manejo de candidatos ICE
peerConnection.onicecandidate = (event) => {
    if (event.candidate) {
        console.log('Nuevo candidato ICE:', event.candidate);
    }
};

// Crear y establecer una oferta
async function startConnection() {
    const offer = await peerConnection.createOffer();
    await peerConnection.setLocalDescription(offer);
}
startConnection();
```

### Ejemplo de Agregar una Pista de Audio
```javascript
navigator.mediaDevices.getUserMedia({ audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    })
    .catch(error => console.error('Error al acceder a los medios:', error));
```

## Explicación
### Errores Comunes
- **Configuración Incorrecta de ICE Servers**: Asegúrate de que los servidores STUN/TURN estén correctamente configurados y accesibles.
- **Olvidar Manejar Candidatos ICE**: No manejar adecuadamente el evento `onicecandidate` puede llevar a fallos en la conexión.
- **Problemas de Seguridad**: WebRTC requiere HTTPS para funcionar en la mayoría de los navegadores. Asegúrate de que tu sitio esté servido de forma segura.

### Notas Adicionales
- RTCPeerConnection es compatible con la mayoría de los navegadores modernos, pero se recomienda verificar la compatibilidad en entornos específicos.
- La API WebRTC es compleja y puede requerir un manejo cuidadoso de los estados y eventos.

## Resumen en Una Línea
RTCPeerConnection es la interfaz de JavaScript que permite establecer conexiones de comunicación en tiempo real entre navegadores utilizando WebRTC.