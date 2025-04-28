<!--
Meta Description: # ScrollTimeline en JavaScript: Animaciones Basadas en el Desplazamiento ## Sinopsis ScrollTimeline es una nueva API de animación en JavaScript que pe...
Meta Keywords: scrolltimeline, desplazamiento, animaciones, que, del
-->

# ScrollTimeline en JavaScript: Animaciones Basadas en el Desplazamiento

## Sinopsis
ScrollTimeline es una nueva API de animación en JavaScript que permite a los desarrolladores crear animaciones en función del desplazamiento del usuario en la página. Esta herramienta ofrece una manera intuitiva y eficiente de sincronizar animaciones con el desplazamiento de una página web, mejorando la experiencia del usuario.

## Documentación

### Propósito
ScrollTimeline permite a los desarrolladores definir animaciones que se activan y sincronizan con el movimiento de desplazamiento del usuario, ofreciendo una alternativa a las animaciones basadas en el tiempo convencional.

### Uso
Para utilizar ScrollTimeline, primero se debe crear una instancia de `ScrollTimeline` y luego se puede aplicar a un objeto de animación. La API facilita la creación de animaciones fluidas que responden directamente al desplazamiento vertical u horizontal.

#### Sintaxis básica
```javascript
const scrollTimeline = new ScrollTimeline({
  scrollSource: document.querySelector('.scroll-container'),
  // Configuración adicional
});
```

### Detalles
- **scrollSource**: Elemento del DOM que se utiliza como fuente de desplazamiento.
- **timeRange**: Intervalo de tiempo de la animación basado en el desplazamiento.
- **start** y **end**: Se definen los puntos de inicio y fin de la animación en relación con el desplazamiento del `scrollSource`.

## Ejemplos

### Ejemplo 1: Animación Simple
```javascript
const scrollTimeline = new ScrollTimeline({
  scrollSource: document.querySelector('.scroll-container'),
  timeRange: 1000, // La animación se sincroniza con 1000px de desplazamiento
});

const animation = document.querySelector('.animated-element').animate([
  { transform: 'translateY(0)' },
  { transform: 'translateY(100px)' }
], {
  timeline: scrollTimeline,
  duration: 1000
});
```

### Ejemplo 2: Animación con Efecto de Desvanecimiento
```javascript
const scrollTimeline = new ScrollTimeline({
  scrollSource: document.querySelector('.scroll-container'),
  timeRange: 500, // 500px de desplazamiento
});

const fadeInAnimation = document.querySelector('.fade-in').animate([
  { opacity: 0 },
  { opacity: 1 }
], {
  timeline: scrollTimeline,
  duration: 500
});
```

## Explicación
Al trabajar con ScrollTimeline, es crucial comprender que el rendimiento puede verse afectado si se utilizan animaciones muy complejas o si se aplican a muchos elementos a la vez. Aquí hay algunos puntos a tener en cuenta:

- **Compatibilidad**: Asegúrate de que el navegador del usuario soporte la API, ya que no todos los navegadores pueden implementarla aún.
- **Desplazamiento óptimo**: Selecciona un `scrollSource` que contenga suficiente contenido para evitar animaciones abruptas o poco fluidas.
- **Mejores prácticas**: Evita la sobrecarga de eventos de desplazamiento y considera usar `requestAnimationFrame` para mejorar el rendimiento.

## Resumen en una línea
ScrollTimeline es una API de JavaScript que permite crear animaciones vinculadas al desplazamiento del usuario, mejorando la interactividad de las páginas web.