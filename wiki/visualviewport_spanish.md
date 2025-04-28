<!--
Meta Description: # visualViewport: Comprendiendo la API de VisualViewport en JavaScript ## Sinopsis La API `visualViewport` en JavaScript permite a los desarrolladores...
Meta Keywords: visualviewport, ventana, del, visual, window
-->

# visualViewport: Comprendiendo la API de VisualViewport en JavaScript

## Sinopsis
La API `visualViewport` en JavaScript permite a los desarrolladores acceder a información sobre la ventana de visualización actual en dispositivos móviles, facilitando la adaptación de la interfaz de usuario a diferentes situaciones de visualización, como la aparición del teclado virtual.

## Documentación
La propiedad `visualViewport` proporciona un objeto que representa la ventana de visualización visual actual del navegador. Este objeto ofrece propiedades y eventos que permiten a los desarrolladores obtener información sobre el tamaño y la posición del área visible, así como responder a cambios en la visualización.

### Propiedades Principales
- **width**: Devuelve el ancho de la ventana visual en píxeles.
- **height**: Devuelve la altura de la ventana visual en píxeles.
- **offsetLeft**: Devuelve la posición horizontal del área visible respecto al borde izquierdo de la ventana de visualización.
- **offsetTop**: Devuelve la posición vertical del área visible respecto al borde superior de la ventana de visualización.
- **scale**: Proporciona el factor de escala de la ventana visual.

### Eventos
- **resize**: Se activa cuando el tamaño de la ventana visual cambia.
- **scroll**: Se activa cuando se desplaza el contenido dentro de la ventana visual.

### Uso
Para acceder a la API `visualViewport`, simplemente usa `window.visualViewport`. Es importante verificar la compatibilidad del navegador, ya que no todos los navegadores pueden soportar esta API.

## Ejemplos
A continuación se presentan algunos ejemplos básicos de cómo utilizar la API `visualViewport`:

### Ejemplo 1: Obtener dimensiones de la ventana visual
```javascript
if (window.visualViewport) {
    console.log(`Ancho: ${window.visualViewport.width}`);
    console.log(`Altura: ${window.visualViewport.height}`);
}
```

### Ejemplo 2: Escuchar cambios en el tamaño de la ventana visual
```javascript
if (window.visualViewport) {
    window.visualViewport.addEventListener('resize', () => {
        console.log('La ventana visual ha cambiado de tamaño.');
        console.log(`Nuevo ancho: ${window.visualViewport.width}`);
        console.log(`Nueva altura: ${window.visualViewport.height}`);
    });
}
```

### Ejemplo 3: Obtener desplazamiento de la ventana visual
```javascript
if (window.visualViewport) {
    console.log(`Desplazamiento Horizontal: ${window.visualViewport.offsetLeft}`);
    console.log(`Desplazamiento Vertical: ${window.visualViewport.offsetTop}`);
}
```

## Explicación
Es importante tener en cuenta que la API `visualViewport` está diseñada principalmente para dispositivos móviles. Algunos navegadores de escritorio pueden no soportar esta API, lo que puede resultar en un comportamiento inconsistente. Además, el uso adecuado de la API puede ayudar a mejorar la experiencia del usuario al manejar eventos como la aparición del teclado virtual o cambios en la orientación del dispositivo. 

Otro punto a considerar es que los cambios en el tamaño de la ventana visual pueden no corresponder directamente a los cambios en el tamaño de la ventana del navegador en sí, debido a la naturaleza del contenido móvil y cómo se renderiza.

## Resumen en una línea
La API `visualViewport` en JavaScript permite acceder y reaccionar a la información sobre el área visible del navegador en dispositivos móviles, mejorando así la experiencia del usuario.