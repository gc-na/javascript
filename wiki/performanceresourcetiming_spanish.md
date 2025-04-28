<!--
Meta Description: # PerformanceResourceTiming: Medición del Rendimiento de Recursos en JavaScript ## Sinopsis `PerformanceResourceTiming` es una interfaz de JavaScript ...
Meta Keywords: que, recurso, recursos, los, del
-->

# PerformanceResourceTiming: Medición del Rendimiento de Recursos en JavaScript

## Sinopsis
`PerformanceResourceTiming` es una interfaz de JavaScript que permite a los desarrolladores medir el rendimiento de los recursos cargados en una página web, proporcionando detalles sobre el tiempo de carga, la duración de las solicitudes y otros parámetros críticos para la optimización del rendimiento.

## Documentación
La interfaz `PerformanceResourceTiming` es parte de la API de Performance del navegador y proporciona información detallada sobre los recursos que se han cargado a través de la red. Esta interfaz se utiliza principalmente para el análisis de rendimiento y la optimización de aplicaciones web.

### Propósito
El propósito de `PerformanceResourceTiming` es permitir a los desarrolladores monitorear y analizar el tiempo que toma cargar diferentes recursos (como imágenes, scripts y hojas de estilo) en sus aplicaciones web. Esto es crucial para mejorar la experiencia del usuario y optimizar el rendimiento de la página.

### Uso
Para acceder a los objetos `PerformanceResourceTiming`, se utiliza la propiedad `performance.getEntriesByType("resource")`, que devuelve una lista de todos los recursos que han sido cargados en la página. Cada objeto de esta lista contiene propiedades que describen los tiempos de inicio y finalización de la carga del recurso, así como otros detalles importantes.

### Detalles de la Interfaz
Algunas de las propiedades más importantes de `PerformanceResourceTiming` incluyen:
- `startTime`: El tiempo en milisegundos desde que comenzó la navegación hasta que se inició la solicitud del recurso.
- `duration`: El tiempo total en milisegundos que tardó en completarse la carga del recurso.
- `fetchStart`: El momento en que la solicitud de red fue iniciada.
- `responseEnd`: El momento en que se completó la recepción de la respuesta.

## Ejemplos
### Ejemplo Básico de Uso
```javascript
// Obtener recursos de rendimiento
const recursos = performance.getEntriesByType("resource");

// Mostrar detalles de cada recurso
recursos.forEach(recurso => {
    console.log(`Recurso: ${recurso.name}`);
    console.log(`Duración: ${recurso.duration} ms`);
    console.log(`Inicio de la solicitud: ${recurso.fetchStart} ms`);
});
```

### Ejemplo de Análisis de Rendimiento
```javascript
// Filtrar recursos que tardan más de 100ms en cargarse
const recursosLentos = performance.getEntriesByType("resource").filter(recurso => recurso.duration > 100);

recursosLentos.forEach(recurso => {
    console.warn(`El recurso ${recurso.name} está tardando más de 100ms en cargar.`);
});
```

## Explicación
Al utilizar `PerformanceResourceTiming`, es importante tener en cuenta algunos aspectos:
- **Precisión del Tiempo**: Los tiempos medidos pueden variar según la conexión de red y el estado del servidor. Por lo tanto, siempre es recomendable realizar múltiples pruebas para obtener promedios más precisos.
- **Compatibilidad**: Aunque la mayoría de los navegadores modernos soportan esta interfaz, siempre es útil verificar la compatibilidad con el navegador específico que están utilizando los usuarios de tu aplicación.
- **Carga de Recursos Dinámicos**: Ten en cuenta que los recursos que se cargan dinámicamente (por ejemplo, mediante AJAX) pueden no aparecer en la lista inicial y podrían requerir seguimiento adicional.

## Resumen en una Línea
`PerformanceResourceTiming` es una herramienta fundamental en JavaScript para medir y optimizar el rendimiento de los recursos cargados en aplicaciones web.