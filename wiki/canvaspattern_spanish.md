<!--
Meta Description: # CanvasPattern en JavaScript: Todo lo que Necesitas Saber ## Sinopsis CanvasPattern es un objeto en JavaScript utilizado para aplicar patrones de rel...
Meta Keywords: context, que, canvas, const, img
-->

# CanvasPattern en JavaScript: Todo lo que Necesitas Saber

## Sinopsis
CanvasPattern es un objeto en JavaScript utilizado para aplicar patrones de relleno a formas en un lienzo (canvas) HTML5. Permite crear texturas y gráficos complejos de manera eficiente.

## Documentación
### Propósito
CanvasPattern se utiliza en el contexto del elemento `<canvas>` para crear patrones repetitivos que pueden ser aplicados como relleno a formas dibujadas en el lienzo. Esto es especialmente útil para agregar texturas, imágenes o diseños complejos a gráficos sin necesidad de crear manualmente cada detalle.

### Uso
Para crear un CanvasPattern, primero se debe crear un contexto de lienzo y luego utilizar el método `createPattern(image, repetition)`. El objeto resultante puede ser utilizado como valor para la propiedad `fillStyle` de un contexto de dibujo.

### Detalles
- **Sintaxis**: 
  ```javascript
  let pattern = context.createPattern(image, repetition);
  ```
- **Parámetros**:
  - `image`: Puede ser un objeto `HTMLImageElement`, `HTMLCanvasElement`, o `HTMLVideoElement`.
  - `repetition`: Una cadena que especifica cómo se debe repetir el patrón. Puede ser:
    - `'repeat'`: Repite el patrón en ambas direcciones.
    - `'repeat-x'`: Repite el patrón solo en la dirección horizontal.
    - `'repeat-y'`: Repite el patrón solo en la dirección vertical.
    - `'no-repeat'`: No repite el patrón.

- **Retorno**: Devuelve un objeto CanvasPattern que puede ser asignado a `fillStyle`.

## Ejemplos

### Ejemplo 1: Relleno con una imagen
```javascript
const canvas = document.getElementById('miCanvas');
const context = canvas.getContext('2d');
const img = new Image();
img.src = 'ruta/a/mi-imagen.png';

img.onload = () => {
  const pattern = context.createPattern(img, 'repeat');
  context.fillStyle = pattern;
  context.fillRect(0, 0, canvas.width, canvas.height);
};
```

### Ejemplo 2: Relleno sin repetición
```javascript
const canvas = document.getElementById('miCanvas');
const context = canvas.getContext('2d');
const img = new Image();
img.src = 'ruta/a/otra-imagen.png';

img.onload = () => {
  const pattern = context.createPattern(img, 'no-repeat');
  context.fillStyle = pattern;
  context.fillRect(50, 50, 100, 100);
};
```

## Explicación
- **Problemas comunes**: Asegúrate de que la imagen esté completamente cargada antes de intentar crear el patrón. Si intentas usar una imagen que no ha sido cargada aún, no se mostrará correctamente.
- **Rendimiento**: Usar patrones puede ser más eficiente que dibujar múltiples imágenes manualmente, pero ten en cuenta que patrones complejos pueden afectar el rendimiento de renderizado si no se manejan adecuadamente.
- **Compatibilidad**: CanvasPattern es compatible con todos los navegadores modernos, pero verifica la compatibilidad si estás desarrollando para navegadores más antiguos.

## Resumen en una línea
CanvasPattern permite crear patrones de relleno en un lienzo HTML5, proporcionando una forma eficiente de aplicar texturas y gráficos complejos en JavaScript.