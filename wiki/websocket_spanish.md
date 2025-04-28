<!--
Meta Description: # WebSocket en JavaScript: Comunicación en Tiempo Real ## Sinopsis WebSocket es un protocolo que permite la comunicación bidireccional en tiempo real ...
Meta Keywords: websocket, socket, conexión, javascript, que
-->

# WebSocket en JavaScript: Comunicación en Tiempo Real

## Sinopsis
WebSocket es un protocolo que permite la comunicación bidireccional en tiempo real entre un cliente y un servidor a través de una única conexión TCP. En el contexto de JavaScript, WebSocket permite a los desarrolladores crear aplicaciones web interactivas y receptivas, como chats en línea y juegos multijugador.

## Documentación
### Propósito
El propósito de WebSocket es proporcionar un medio eficiente para la comunicación en tiempo real. A diferencia de las técnicas tradicionales como AJAX (que requieren múltiples solicitudes HTTP), WebSocket establece una conexión persistente que permite el intercambio de datos en ambas direcciones.

### Uso
Para utilizar WebSocket en JavaScript, se utiliza la clase `WebSocket`. A continuación se describen los pasos básicos:

1. **Crear una nueva instancia de WebSocket**:
   ```javascript
   const socket = new WebSocket('ws://servidor.com:puerto');
   ```

2. **Manejar eventos**:
   - `onopen`: Se activa cuando se establece la conexión.
   - `onmessage`: Se activa cuando se recibe un mensaje.
   - `onerror`: Se activa en caso de error.
   - `onclose`: Se activa cuando se cierra la conexión.

3. **Enviar mensajes**:
   ```javascript
   socket.send('Mensaje a enviar');
   ```

4. **Cerrar la conexión**:
   ```javascript
   socket.close();
   ```

### Detalles
- **Protocolo**: WebSocket opera sobre el protocolo TCP y utiliza el puerto 80 para conexiones sin cifrar o el puerto 443 para conexiones seguras (WSS).
- **Manejo de mensajes**: Los mensajes pueden ser texto (UTF-8) o binarios (ArrayBuffer o Blob).
- **Seguridad**: Al usar WSS, se deben considerar las mismas políticas de seguridad que HTTPS.

## Ejemplos
### Ejemplo básico de WebSocket
```javascript
const socket = new WebSocket('ws://servidor.com:puerto');

socket.onopen = () => {
    console.log('Conexión establecida');
    socket.send('Hola, servidor!');
};

socket.onmessage = (event) => {
    console.log('Mensaje recibido:', event.data);
};

socket.onerror = (error) => {
    console.error('Error en WebSocket:', error);
};

socket.onclose = () => {
    console.log('Conexión cerrada');
};
```

### Ejemplo de manejo de mensajes binarios
```javascript
const socket = new WebSocket('ws://servidor.com:puerto');

socket.binaryType = 'arraybuffer';

socket.onmessage = (event) => {
    const arrayBuffer = event.data;
    console.log('Datos binarios recibidos:', arrayBuffer);
};
```

## Explicación
### Errores comunes
- **Cierre inesperado**: Es común que la conexión WebSocket se cierre inesperadamente, por lo que es recomendable implementar lógica de reconexión.
- **Problemas de CORS**: Si el servidor no está configurado para permitir conexiones desde el origen del cliente, la conexión fallará.
- **Manejo de mensajes**: Asegúrate de manejar correctamente los tipos de datos enviados y recibidos, ya que el mal manejo puede llevar a errores en la aplicación.

### Notas adicionales
- Los navegadores modernos soportan WebSocket, pero es importante verificar la compatibilidad si se planea soportar navegadores más antiguos.
- Considera utilizar bibliotecas como Socket.IO para facilitar el trabajo con WebSocket y proporcionar funciones adicionales como la reconexión automática.

## Resumen en una línea
WebSocket en JavaScript permite establecer una conexión bidireccional eficiente para la comunicación en tiempo real entre clientes y servidores.