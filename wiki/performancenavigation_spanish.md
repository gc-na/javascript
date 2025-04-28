<!--
Meta Description: # PerformanceNavigation en JavaScript: Optimización del Rendimiento de Navegación ## Sinopsis PerformanceNavigation es una interfaz JavaScript que per...
Meta Keywords: que, navigation, página, javascript, navegación
-->

# PerformanceNavigation en JavaScript: Optimización del Rendimiento de Navegación

## Sinopsis
PerformanceNavigation es una interfaz JavaScript que permite a los desarrolladores acceder a datos sobre cómo se ha navegado a la página actual. Esta información es crucial para optimizar el rendimiento y la experiencia del usuario en aplicaciones web.

## Documentación
### Propósito
La interfaz `PerformanceNavigation` proporciona información sobre el tipo de carga de la página, permitiendo a los desarrolladores entender si un usuario ha accedido a la página a través de un enlace, una recarga, o si es la primera vez que se carga.

### Uso
Para acceder a la información de navegación, se utiliza el objeto `performance` que es parte de la API de rendimiento en JavaScript. A continuación, se presenta cómo se puede acceder a la información de navegación:

```javascript
const navigation = performance.navigation;
```

### Detalles
- `navigation.type`: Este atributo indica el tipo de navegación. Puede tener los siguientes valores:
  - `0` (TYPE_NAVIGATE): La página fue cargada de forma estándar.
  - `1` (TYPE_RELOAD): La página fue recargada.
  - `2` (TYPE_RESERVED): Este valor se utiliza para navegaciones que no son estándar y normalmente no se utiliza.

- `navigation.redirectCount`: Este atributo indica el número de redireccionamientos que ocurrieron antes de que la página se cargara.

## Ejemplos
### Ejemplo 1: Verificar el tipo de navegación

```javascript
const navigation = performance.navigation;

if (navigation.type === 1) {
    console.log("La página fue recargada.");
} else if (navigation.type === 0) {
    console.log("La página fue cargada normalmente.");
}
```

### Ejemplo 2: Contar redireccionamientos

```javascript
const navigation = performance.navigation;

console.log(`Número de redireccionamientos: ${navigation.redirectCount}`);
```

## Explicación
Algunos errores comunes al utilizar `PerformanceNavigation` incluyen:
- No comprobar si el objeto `performance` está disponible en el navegador, lo que puede llevar a errores en navegadores que no soporten esta API.
- Asumir que `navigation.redirectCount` siempre será mayor que cero, ya que esto solo ocurre si hay redireccionamientos previos.

Adicionalmente, es importante mencionar que la API `PerformanceNavigation` ha sido obsoleta en navegadores modernos y se recomienda utilizar la API de `PerformanceNavigationTiming` para obtener información más detallada sobre el rendimiento de la navegación.

## Resumen en una línea
PerformanceNavigation en JavaScript permite a los desarrolladores obtener información sobre el tipo y la cantidad de redireccionamientos en la navegación de la página actual.