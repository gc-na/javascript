<!--
Meta Description: # XMLHttpRequest en JavaScript: Guía Completa ## Sinopsis XMLHttpRequest es un objeto en JavaScript que permite realizar solicitudes HTTP a un servido...
Meta Keywords: xhr, solicitud, que, xmlhttprequest, una
-->

# XMLHttpRequest en JavaScript: Guía Completa

## Sinopsis
XMLHttpRequest es un objeto en JavaScript que permite realizar solicitudes HTTP a un servidor web, facilitando la comunicación asincrónica y la carga dinámica de contenido en páginas web sin necesidad de recargar la página completa.

## Documentación
### Propósito
XMLHttpRequest se utiliza para interactuar con servidores web de manera asincrónica. Permite a los desarrolladores enviar y recibir datos en formatos como texto, JSON, XML, etc., lo que es crucial para crear aplicaciones web dinámicas y receptivas.

### Uso
Para utilizar XMLHttpRequest, se crea una instancia del objeto y se utilizan sus métodos y propiedades para realizar una solicitud HTTP. 

#### Pasos básicos:
1. Crear una instancia de XMLHttpRequest.
2. Configurar la solicitud con `open()`.
3. Enviar la solicitud con `send()`.
4. Manejar la respuesta en el evento `onreadystatechange`.

### Detalles
- **Métodos principales**:
  - `open(method, url, async)`: Prepara la solicitud. `method` puede ser "GET" o "POST", `url` es la dirección del recurso, y `async` indica si la solicitud es asincrónica (true) o sincrónica (false).
  - `send(data)`: Envía la solicitud. Si es una solicitud POST, `data` puede ser un objeto o una cadena que se envía al servidor.
  
- **Propiedades importantes**:
  - `readyState`: Representa el estado de la solicitud. Los valores posibles son 0 (UNSENT), 1 (OPENED), 2 (HEADERS_RECEIVED), 3 (LOADING), 4 (DONE).
  - `status`: Devuelve el código de estado HTTP de la respuesta (por ejemplo, 200 para éxito).
  - `responseText`: Contiene la respuesta del servidor en forma de texto.

## Ejemplos
### Ejemplo básico de una solicitud GET
```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

### Ejemplo de una solicitud POST
```javascript
var xhr = new XMLHttpRequest();
xhr.open("POST", "https://api.example.com/submit", true);
xhr.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 201) {
        console.log("Datos enviados correctamente");
    }
};
xhr.send(JSON.stringify({name: "Juan", age: 30}));
```

## Explicación
### Problemas comunes
- **CORS (Cross-Origin Resource Sharing)**: Al hacer solicitudes a un dominio diferente, es posible que se enfrente a restricciones de CORS, que impiden que el navegador permita la solicitud. Asegúrese de que el servidor permita solicitudes desde su origen.
- **Estado `readyState`**: Es crucial revisar el estado de `readyState` antes de manejar la respuesta para evitar errores. Asegúrese de que sea 4 antes de acceder a `responseText`.
- **Manejo de errores**: Siempre es recomendable manejar posibles errores utilizando el evento `onerror` para capturar fallos en la solicitud.

## Resumen en una frase
XMLHttpRequest es un objeto en JavaScript que permite realizar solicitudes HTTP de manera asincrónica, facilitando la carga dinámica de contenido en aplicaciones web.