<!--
Meta Description: # ShadowRoot en JavaScript: Creación y Manipulación de Árboles de Sombra ## Sinopsis ShadowRoot es una interfaz en JavaScript que permite crear un árb...
Meta Keywords: shadowroot, dom, que, shadow, árbol
-->

# ShadowRoot en JavaScript: Creación y Manipulación de Árboles de Sombra

## Sinopsis
ShadowRoot es una interfaz en JavaScript que permite crear un árbol de sombra (shadow tree) dentro de un elemento del DOM, proporcionando encapsulamiento para estilos y scripts, lo que mejora la modularidad y reutilización de componentes web.

## Documentación
El objeto ShadowRoot se utiliza en el contexto de la API de Shadow DOM, una característica de Web Components que permite a los desarrolladores encapsular el estilo y la estructura de un componente. Al crear un ShadowRoot, se genera un árbol de nodos que es independiente del árbol DOM principal, lo que significa que los estilos y scripts aplicados en el árbol de sombra no afectarán al resto del documento y viceversa.

### Propósito
El propósito principal de ShadowRoot es permitir la creación de componentes web más robustos y aislados, evitando conflictos de estilos y comportamientos con otros elementos de la página.

### Uso
Para crear un ShadowRoot, se debe invocar el método `attachShadow` en un elemento del DOM. Este método toma un objeto de configuración que puede especificar el modo de acceso al árbol de sombra, ya sea `open` o `closed`.

**Sintaxis:**
```javascript
const shadowRoot = element.attachShadow({ mode: 'open' | 'closed' });
```

- **element**: El elemento del DOM al cual se le adjuntará el ShadowRoot.
- **mode**: Define la accesibilidad del ShadowRoot. 
  - `open`: permite el acceso al ShadowRoot a través de la propiedad `shadowRoot`.
  - `closed`: no permite el acceso a la propiedad `shadowRoot`.

## Ejemplos
### Ejemplo Básico de Creación de ShadowRoot
```javascript
// Crear un nuevo elemento
const myElement = document.createElement('div');

// Adjuntar un ShadowRoot
const shadow = myElement.attachShadow({ mode: 'open' });

// Añadir contenido al ShadowRoot
shadow.innerHTML = `
  <style>
    p {
      color: blue;
    }
  </style>
  <p>¡Hola, Shadow DOM!</p>
`;

// Añadir el elemento al DOM
document.body.appendChild(myElement);
```

### Ejemplo con Modo Closed
```javascript
// Crear un nuevo elemento
const myElement = document.createElement('div');

// Adjuntar un ShadowRoot con modo cerrado
const shadow = myElement.attachShadow({ mode: 'closed' });

// Añadir contenido al ShadowRoot
shadow.innerHTML = `
  <style>
    p {
      color: red;
    }
  </style>
  <p>¡Hola, Shadow DOM cerrado!</p>
`;

// Añadir el elemento al DOM
document.body.appendChild(myElement);

// Intentar acceder al ShadowRoot (no funcionará)
console.log(myElement.shadowRoot); // null
```

## Explicación
Al utilizar ShadowRoot, es importante tener en cuenta que:
- Si se utiliza el modo `closed`, no se podrá acceder al árbol de sombra a través de la propiedad `shadowRoot`, lo que puede ser deseado para proteger la implementación interna del componente.
- Los estilos definidos dentro de un ShadowRoot no se filtrarán hacia el árbol DOM externo y no se verán afectados por estilos externos. Sin embargo, los estilos globales (por ejemplo, `:host`) pueden ser utilizados para aplicar estilos desde el árbol externo al componente.
- Las interacciones entre elementos en el Shadow DOM y el DOM principal pueden requerir eventos personalizados para la comunicación.

## Resumen en Una Línea
ShadowRoot en JavaScript permite la creación de componentes web encapsulados, mejorando la modularidad y evitando conflictos de estilos en el DOM.