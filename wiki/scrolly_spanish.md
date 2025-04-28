<!--
Meta Description: # scrollY en JavaScript: Comprendiendo la Posición Vertical de Desplazamiento ## Sinopsis `scrollY` es una propiedad de la interfaz `Window` en JavaSc...
Meta Keywords: scrolly, desplazamiento, que, javascript, posición
-->

# scrollY en JavaScript: Comprendiendo la Posición Vertical de Desplazamiento 

## Sinopsis
`scrollY` es una propiedad de la interfaz `Window` en JavaScript que permite obtener la cantidad de píxeles que el documento ha sido desplazado verticalmente desde la parte superior de la ventana de visualización.

## Documentación
La propiedad `scrollY` es un valor numérico que representa la posición vertical del desplazamiento de la página en el eje Y. Se mide desde la parte superior de la ventana de visualización hasta la parte superior del documento. Esta propiedad es especialmente útil para implementar efectos de desplazamiento, detectar el desplazamiento del usuario, y optimizar la carga de contenido en función de la posición de desplazamiento.

### Uso
Para acceder a `scrollY`, simplemente se puede utilizar el siguiente formato:

```javascript
let scrollPosition = window.scrollY;
```

### Detalles
- **Tipo de dato**: `number`
- **Valor**: El valor devuelto es en píxeles. Un valor de `0` indica que la parte superior del documento está visible en la ventana de visualización, mientras que un valor positivo indica que se ha desplazado hacia abajo.
- **Compatibilidad**: `scrollY` es compatible con la mayoría de los navegadores modernos. Sin embargo, es recomendable verificar la compatibilidad si se está desarrollando para navegadores más antiguos.

## Ejemplos
### Ejemplo 1: Obtener la posición de desplazamiento
```javascript
window.addEventListener('scroll', function() {
    console.log('Posición de desplazamiento vertical: ' + window.scrollY + 'px');
});
```

### Ejemplo 2: Cambiar el fondo según el desplazamiento
```javascript
window.addEventListener('scroll', function() {
    document.body.style.backgroundColor = `rgb(${window.scrollY / 2}, 100, 150)`;
});
```

## Explicación
Al trabajar con `scrollY`, hay algunas consideraciones a tener en cuenta:

1. **Eventos de desplazamiento**: La propiedad `scrollY` es útil en combinación con eventos de desplazamiento (`scroll`) para ejecutar acciones basadas en la posición de la página.
2. **Rendimiento**: Si se usa `scrollY` dentro de un evento de desplazamiento, puede ser necesario optimizar el rendimiento para evitar el "jitter" y mejorar la experiencia del usuario. Utilizar técnicas como 'throttling' o 'debouncing' puede ayudar a limitar la frecuencia de ejecución del evento.
3. **Compatibilidad con navegadores**: Aunque `scrollY` está bien soportado en navegadores modernos, siempre es una buena práctica realizar pruebas en diferentes navegadores para asegurar que la funcionalidad deseada se mantenga.

## Resumen en una línea
La propiedad `scrollY` en JavaScript permite acceder a la cantidad de píxeles desplazados verticalmente en la ventana de visualización.