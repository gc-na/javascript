<!--
Meta Description: # CanvasGradient en JavaScript: Creación de Gradientes en el Canvas ## Sinopsis `CanvasGradient` es un objeto en JavaScript utilizado para crear gradi...
Meta Keywords: gradiente, canvas, ctx, canvasgradient, para
-->

# CanvasGradient en JavaScript: Creación de Gradientes en el Canvas

## Sinopsis
`CanvasGradient` es un objeto en JavaScript utilizado para crear gradientes de color en un elemento `<canvas>`. Permite a los desarrolladores aplicar transiciones suaves entre diferentes colores, mejorando la estética de gráficos y visualizaciones.

## Documentación
### Propósito
El objeto `CanvasGradient` se utiliza junto con la API Canvas de HTML5 para definir y aplicar gradientes lineales o radiales en las formas dibujadas en el canvas. Los gradientes son esenciales para crear efectos visuales atractivos y dinámicos en aplicaciones web.

### Uso
Para crear un `CanvasGradient`, se debe utilizar el método `createLinearGradient()` o `createRadialGradient()` del contexto de dibujo del canvas. 

- **createLinearGradient(x0, y0, x1, y1)**: Crea un gradiente lineal que va desde el punto (x0, y0) hasta el punto (x1, y1).
- **createRadialGradient(x0, y0, r0, x1, y1, r1)**: Crea un gradiente radial que se extiende desde el círculo definido por (x0, y0, r0) hasta el círculo definido por (x1, y1, r1).

#### Métodos Clave
- **addColorStop(offset, color)**: Agrega un color al gradiente en una posición específica (offset) entre 0 y 1.

### Ejemplo
```javascript
// Obtener el contexto del canvas
const canvas = document.getElementById('miCanvas');
const ctx = canvas.getContext('2d');

// Crear un gradiente lineal
const gradiente = ctx.createLinearGradient(0, 0, 200, 0);
gradiente.addColorStop(0, 'red');
gradiente.addColorStop(1, 'blue');

// Usar el gradiente como relleno
ctx.fillStyle = gradiente;
ctx.fillRect(10, 10, 200, 100);
```

```javascript
// Crear un gradiente radial
const gradienteRadial = ctx.createRadialGradient(150, 75, 50, 150, 75, 100);
gradienteRadial.addColorStop(0, 'yellow');
gradienteRadial.addColorStop(1, 'green');

// Usar el gradiente radial como relleno
ctx.fillStyle = gradienteRadial;
ctx.fillRect(50, 50, 200, 200);
```

## Explicación
Al trabajar con `CanvasGradient`, es importante tener en cuenta algunos errores comunes:

1. **No agregar color stops**: Si no se añaden paradas de color (`addColorStop`), el gradiente resultante puede no mostrarse como se espera.
2. **Offset fuera de rango**: El valor de offset debe estar entre 0 y 1. Valores fuera de este rango no tendrán efecto.
3. **Recargar el canvas sin limpiar**: Al dibujar múltiples elementos, asegúrate de limpiar el canvas si es necesario para evitar superposiciones no deseadas.

## Resumen en una línea
`CanvasGradient` en JavaScript permite crear gradientes de color sofisticados para mejorar la presentación visual en elementos canvas.