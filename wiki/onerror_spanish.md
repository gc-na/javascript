<!--
Meta Description: # Uso de onerror en JavaScript: Manejo de Errores en el Navegador ## Sinopsis El evento `onerror` en JavaScript es una herramienta fundamental para la...
Meta Keywords: onerror, error, errores, que, script
-->

# Uso de onerror en JavaScript: Manejo de Errores en el Navegador

## Sinopsis
El evento `onerror` en JavaScript es una herramienta fundamental para la gestión de errores en aplicaciones web. Permite a los desarrolladores capturar y manejar errores de carga de recursos y errores de ejecución, mejorando la experiencia del usuario al proporcionar retroalimentación adecuada.

## Documentación
### Propósito
El evento `onerror` se utiliza para detectar y manejar errores que ocurren durante la carga de recursos, como imágenes, scripts o estilos, así como errores en la ejecución de scripts JavaScript. Esto es especialmente útil para evitar que errores no controlados interrumpan la funcionalidad de una aplicación web.

### Uso
El evento `onerror` se puede asignar a diferentes elementos HTML o a la ventana global. Su sintaxis básica es la siguiente:

```javascript
element.onerror = function(event) {
    // Código para manejar el error
};
```

### Detalles
- **Contexto de uso**: Se puede usar en elementos `<img>`, `<script>`, `<link>` y en el objeto `window`.
- **Parámetros**: La función que maneja el error recibe un objeto `event` que contiene información sobre el error ocurrido.
- **Retorno**: No se espera que la función `onerror` devuelva un valor; su propósito es ejecutar código específico en respuesta al error.

## Ejemplos
### Ejemplo 1: Captura de error en una imagen
```html
<img src="imagen-inexistente.jpg" onerror="this.onerror=null; this.src='imagen-default.jpg';">
```
En este ejemplo, si la imagen no se carga, se reemplaza por una imagen predeterminada.

### Ejemplo 2: Manejo de errores en un script
```html
<script src="script-inexistente.js" onerror="console.error('Error al cargar el script');"></script>
```
Este script genera un mensaje de error en la consola si falla al cargar.

### Ejemplo 3: Manejo de errores en la ventana
```javascript
window.onerror = function(message, source, lineno, colno, error) {
    alert(`Se ha producido un error: ${message} en ${source}:${lineno}:${colno}`);
    return true; // Evita que el error se propague
};
```
En este caso, se muestra una alerta con información sobre el error capturado.

## Explicación
Al usar `onerror`, es importante tener en cuenta que:
- **Errores en tiempo de carga**: `onerror` no se disparará si el script o recurso se carga correctamente.
- **Propagación de errores**: Si se retorna `true` en el manejador de `window.onerror`, se evita que el error se muestre en la consola del navegador.
- **Compatibilidad**: Asegúrate de probar el soporte en diferentes navegadores, ya que el comportamiento puede variar.

## Resumen en una línea
El evento `onerror` en JavaScript permite manejar errores de carga y ejecución, mejorando la robustez de las aplicaciones web.