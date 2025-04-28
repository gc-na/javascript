<!--
Meta Description: # innerHeight en JavaScript: Comprendiendo la Altura Interna de la Ventana del Navegador ## Sinopsis `innerHeight` es una propiedad de la interfaz `Wi...
Meta Keywords: altura, ventana, innerheight, del, para
-->

# innerHeight en JavaScript: Comprendiendo la Altura Interna de la Ventana del Navegador

## Sinopsis
`innerHeight` es una propiedad de la interfaz `Window` en JavaScript que devuelve la altura interior de la ventana del navegador, medida en píxeles. Esta propiedad es útil para diseñar aplicaciones web responsivas y para controlar la disposición del contenido en función del tamaño de la ventana.

## Documentación
La propiedad `window.innerHeight` proporciona la altura interna de la ventana del navegador, excluyendo barras de desplazamiento y bordes. Su uso es fundamental para adaptar el diseño y la funcionalidad de aplicaciones web dinámicas según el tamaño de la ventana.

### Uso
Para acceder a `innerHeight`, simplemente se utiliza `window.innerHeight` en el contexto de un script JavaScript. Esta propiedad se puede utilizar en eventos como `resize` para ajustar el contenido de la página cuando el usuario cambia el tamaño de la ventana.

```javascript
const alturaVentana = window.innerHeight;
console.log(`La altura de la ventana es: ${alturaVentana}px`);
```

### Detalles
- **Tipo de dato:** Número (en píxeles).
- **Lectura:** Solo se puede leer, no se puede establecer.
- **Compatibilidad:** Compatible con todos los navegadores modernos.

## Ejemplos
### Ejemplo 1: Obtener la altura de la ventana
```javascript
document.addEventListener("DOMContentLoaded", () => {
    const altura = window.innerHeight;
    console.log(`La altura de la ventana es: ${altura}px`);
});
```

### Ejemplo 2: Ajustar un elemento según la altura de la ventana
```javascript
const elemento = document.getElementById("miElemento");

function ajustarAltura() {
    elemento.style.height = `${window.innerHeight}px`;
}

window.addEventListener("resize", ajustarAltura);
ajustarAltura(); // Llamar a la función inicialmente para establecer la altura.
```

## Explicación
Al utilizar `innerHeight`, es importante tener en cuenta que:

- **Cálculos Incorrectos:** Si se necesita la altura total de la ventana, considera que `innerHeight` no incluye elementos como la barra de herramientas del navegador.
- **Eventos de Redimensionamiento:** Al usar `innerHeight` en un evento de `resize`, puede haber un rendimiento impactado si se realizan cálculos intensivos. Se recomienda implementar técnicas de optimización como el "debounce" para limitar la frecuencia de ejecución del código.
- **Viewport vs. Document:** `innerHeight` se refiere a la ventana visible del navegador, no a la altura total del documento. Para obtener la altura total del documento, se puede usar `document.documentElement.scrollHeight`.

## Resumen en una línea
`innerHeight` es una propiedad que devuelve la altura interna de la ventana del navegador, permitiendo adaptar el contenido de las aplicaciones web según el tamaño de la ventana.