<!--
Meta Description: # onselectionchange en JavaScript: Manejo de Cambios en Selecciones ## Sinopsis El evento `onselectionchange` en JavaScript permite detectar y manejar...
Meta Keywords: texto, onselectionchange, selección, que, document
-->

# onselectionchange en JavaScript: Manejo de Cambios en Selecciones

## Sinopsis
El evento `onselectionchange` en JavaScript permite detectar y manejar cambios en la selección de texto dentro de un documento. Este evento se desencadena cuando el usuario selecciona o deselecciona texto, lo que brinda la oportunidad de ejecutar acciones específicas en respuesta a estas interacciones.

## Documentación
### Propósito
El evento `onselectionchange` es particularmente útil en aplicaciones web donde se requiere realizar acciones en función del texto seleccionado por el usuario. Esto puede incluir la modificación de estilos, la activación de botones, o la visualización de información adicional relacionada con el texto seleccionado.

### Uso
Para utilizar `onselectionchange`, se debe agregar un listener a un objeto de tipo `document` o a un elemento específico. Este listener ejecutará una función cada vez que haya un cambio en la selección.

### Detalles
- **Sintaxis**: 
  ```javascript
  document.onselectionchange = function() {
      // Lógica a ejecutar en respuesta al cambio de selección
  };
  ```
- **Ejemplo de aplicación**: Este evento es ideal para aplicaciones de procesamiento de texto, editores de texto enriquecido, o cualquier interfaz que necesite reaccionar a la selección de texto por parte del usuario.

## Ejemplos
### Ejemplo Básico
```javascript
document.onselectionchange = function() {
    const selection = document.getSelection();
    console.log('Texto seleccionado:', selection.toString());
};
```
En este ejemplo, cada vez que el usuario cambia la selección de texto, se imprimirá en la consola el texto actualmente seleccionado.

### Ejemplo con Estilo
```javascript
document.onselectionchange = function() {
    const selection = document.getSelection();
    
    if (selection.rangeCount > 0) {
        const range = selection.getRangeAt(0);
        const selectedText = range.toString();
        
        // Aplicar estilo al texto seleccionado
        const span = document.createElement('span');
        span.style.backgroundColor = 'yellow';
        span.textContent = selectedText;
        
        range.deleteContents();
        range.insertNode(span);
    }
};
```
En este caso, el texto seleccionado se resalta con un fondo amarillo al cambiar la selección.

## Explicación
### Problemas Comunes
- **Compatibilidad**: Aunque `onselectionchange` es ampliamente soportado en navegadores modernos, no está disponible en todos los navegadores. Verifique la compatibilidad antes de implementarlo.
- **Rendimiento**: Evite ejecutar operaciones pesadas dentro del manejador del evento, ya que puede afectar el rendimiento general de la aplicación, especialmente si se producen selecciones frecuentes.

### Notas Adicionales
- Asegúrese de que el código que maneja `onselectionchange` no interfiera con otras interacciones del usuario, como la selección de múltiples elementos en una lista.
- Pruebe el comportamiento en diferentes dispositivos, ya que los métodos de selección pueden variar.

## Resumen en Una Línea
El evento `onselectionchange` en JavaScript permite detectar y reaccionar a cambios en la selección de texto, facilitando interacciones dinámicas en aplicaciones web.