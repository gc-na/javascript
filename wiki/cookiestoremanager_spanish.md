<!--
Meta Description: # CookieStoreManager: Gestión de Cookies en JavaScript ## Sinopsis CookieStoreManager es una interfaz moderna en JavaScript que permite a los desarrol...
Meta Keywords: cookie, error, cookies, cookiestoremanager, javascript
-->

# CookieStoreManager: Gestión de Cookies en JavaScript

## Sinopsis
CookieStoreManager es una interfaz moderna en JavaScript que permite a los desarrolladores gestionar cookies de manera eficiente y segura en aplicaciones web. Proporciona métodos para crear, leer y eliminar cookies, facilitando así la persistencia de datos en el navegador del usuario.

## Documentación

### Propósito
CookieStoreManager está diseñado para simplificar la manipulación de cookies en aplicaciones web. Con la creciente preocupación por la privacidad y la gestión de datos, esta API ayuda a los desarrolladores a seguir las mejores prácticas en el manejo de cookies.

### Uso
Para utilizar CookieStoreManager, primero asegúrate de que el entorno de ejecución de JavaScript soporte la API. Esta interfaz se encuentra disponible en la mayoría de los navegadores modernos.

#### Métodos Principales:
- **`get(name)`**: Recupera el valor de la cookie con el nombre especificado.
- **`set(name, value, options)`**: Crea o actualiza una cookie con el nombre y valor especificados, además de permitir opciones como la fecha de caducidad o el dominio.
- **`delete(name)`**: Elimina la cookie con el nombre especificado.

### Detalles
El objeto CookieStoreManager permite un enfoque más estructurado en la gestión de cookies. Incluye opciones de configuración como:
- **`expires`**: Define cuándo expira la cookie.
- **`path`**: Define la ruta en la que la cookie es accesible.
- **`secure`**: Indica si la cookie debe ser enviada solo a través de conexiones HTTPS.

## Ejemplos

### Ejemplo 1: Crear una cookie
```javascript
const cookieStore = window.cookieStore;
cookieStore.set('usuario', 'Juan', { expires: new Date('2024-01-01') })
  .then(() => {
    console.log('Cookie creada con éxito');
  })
  .catch((error) => {
    console.error('Error al crear la cookie:', error);
  });
```

### Ejemplo 2: Leer una cookie
```javascript
cookieStore.get('usuario')
  .then((cookie) => {
    if (cookie) {
      console.log('Valor de la cookie:', cookie.value);
    } else {
      console.log('La cookie no existe');
    }
  })
  .catch((error) => {
    console.error('Error al leer la cookie:', error);
  });
```

### Ejemplo 3: Eliminar una cookie
```javascript
cookieStore.delete('usuario')
  .then(() => {
    console.log('Cookie eliminada con éxito');
  })
  .catch((error) => {
    console.error('Error al eliminar la cookie:', error);
  });
```

## Explicación
Al utilizar CookieStoreManager, es importante tener en cuenta que:
- Las cookies pueden ser afectadas por restricciones de seguridad del navegador, como las políticas de SameSite.
- Las cookies de terceros pueden estar sujetas a bloqueos por parte de algunos navegadores debido a configuraciones de privacidad.
- Asegúrate de manejar correctamente los errores, especialmente al realizar operaciones asíncronas con promesas.

## Resumen en una línea
CookieStoreManager proporciona una interfaz moderna y segura para la gestión de cookies en aplicaciones JavaScript, facilitando la creación, lectura y eliminación de cookies.