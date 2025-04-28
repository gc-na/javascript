<!--
Meta Description: # SubtleCrypto en JavaScript: Una Guía Completa para la Criptografía Segura ## Sinopsis SubtleCrypto es una interfaz de programación en JavaScript que...
Meta Keywords: data, datos, crypto, const, subtlecrypto
-->

# SubtleCrypto en JavaScript: Una Guía Completa para la Criptografía Segura

## Sinopsis
SubtleCrypto es una interfaz de programación en JavaScript que proporciona funciones criptográficas de bajo nivel para el manejo seguro de datos a través de algoritmos como el hashing, la encriptación y la firma digital, permitiendo a los desarrolladores implementar soluciones de seguridad robustas en sus aplicaciones web.

## Documentación
### Propósito
SubtleCrypto es parte de la API Web Cryptography, diseñada para ofrecer un acceso seguro y eficiente a las operaciones criptográficas. Su principal objetivo es ayudar a los desarrolladores a proteger datos sensibles y garantizar la integridad y autenticidad de la información.

### Uso
Para utilizar SubtleCrypto, es necesario acceder a su instancia a través de la propiedad `crypto.subtle` del objeto `window.crypto`. Esta API es asincrónica, lo que significa que muchas de sus funciones devuelven promesas. Aquí están algunas de las operaciones más comunes que se pueden realizar con SubtleCrypto:

- **Hashing**: Crear un resumen (hash) de datos.
- **Firmas digitales**: Firmar datos y verificar la firma.
- **Encriptación y desencriptación**: Proteger datos sensibles mediante algoritmos de cifrado.

### Detalles
SubtleCrypto ofrece varios métodos, incluyendo:

- `digest(algorithm, data)`: Calcula el hash de los datos utilizando un algoritmo especificado.
- `encrypt(algorithm, key, data)`: Encripta datos utilizando una clave y un algoritmo.
- `decrypt(algorithm, key, data)`: Desencripta datos encriptados.
- `sign(algorithm, key, data)`: Crea una firma digital de los datos.
- `verify(algorithm, key, signature, data)`: Verifica una firma digital.

## Ejemplos
### Ejemplo de Hashing
```javascript
const data = new TextEncoder().encode("Hola, mundo!");
crypto.subtle.digest("SHA-256", data)
    .then(hash => {
        console.log(new Uint8Array(hash));
    });
```

### Ejemplo de Encriptación y Desencriptación
```javascript
const data = new TextEncoder().encode("Datos sensibles");
const keyMaterial = await crypto.subtle.importKey("raw", new Uint8Array([/* bytes de clave */]), "AES-GCM", true, ["encrypt", "decrypt"]);

const iv = window.crypto.getRandomValues(new Uint8Array(12)); // Vector de inicialización

const encrypted = await crypto.subtle.encrypt({ name: "AES-GCM", iv }, keyMaterial, data);
const decrypted = await crypto.subtle.decrypt({ name: "AES-GCM", iv }, keyMaterial, encrypted);
```

### Ejemplo de Firma Digital
```javascript
const keyPair = await crypto.subtle.generateKey({ name: "RSA-PSS", modulusLength: 2048, publicExponent: new Uint8Array([1, 0, 1]), hash: "SHA-256" }, true, ["sign", "verify"]);

const data = new TextEncoder().encode("Mensaje a firmar");
const signature = await crypto.subtle.sign({ name: "RSA-PSS", saltLength: 32 }, keyPair.privateKey, data);

const isValid = await crypto.subtle.verify({ name: "RSA-PSS", saltLength: 32 }, keyPair.publicKey, signature, data);
console.log(`La firma es válida: ${isValid}`);
```

## Explicación
Al trabajar con SubtleCrypto, es importante tener en cuenta que:

- **Asincronía**: La mayoría de las funciones son asincrónicas, lo que significa que debes manejar promesas adecuadamente.
- **Compatibilidad del navegador**: No todos los navegadores pueden soportar todas las funciones de SubtleCrypto. Asegúrate de comprobar la compatibilidad antes de implementar.
- **Seguridad**: La gestión de claves es fundamental; asegúrate de manejar las claves privadas con extremo cuidado y nunca exponerlas en el cliente.

## Resumen en una línea
SubtleCrypto es una interfaz en JavaScript que permite realizar operaciones criptográficas seguras, como hashing, encriptación y firma digital, facilitando así la protección de datos en aplicaciones web.