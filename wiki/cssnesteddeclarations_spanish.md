<!--
Meta Description: # Declaraciones CSS Anidadas (CSSNestedDeclarations) en JavaScript ## Sinopsis Las Declaraciones CSS Anidadas son una característica que permite organ...
Meta Keywords: css, styled, que, declaraciones, anidadas
-->

# Declaraciones CSS Anidadas (CSSNestedDeclarations) en JavaScript

## Sinopsis
Las Declaraciones CSS Anidadas son una característica que permite organizar y estructurar el código CSS de manera más jerárquica y legible en proyectos JavaScript, facilitando la gestión de estilos en aplicaciones web modernas.

## Documentación
Las Declaraciones CSS Anidadas permiten definir estilos CSS de manera que se agrupan dentro de otros selectores, lo que mejora la claridad y el mantenimiento del código. Esta técnica es especialmente útil en bibliotecas y frameworks que soportan CSS en sus componentes, como Styled Components en React o SASS en proyectos más amplios.

### Propósito
El propósito principal de las Declaraciones CSS Anidadas es hacer que el código CSS sea más legible y organizado. Esto se logra al permitir que las reglas de estilo se aniden dentro de otros selectores, reflejando la jerarquía del HTML y haciendo que los estilos se apliquen de manera más intuitiva.

### Uso
Para utilizar las Declaraciones CSS Anidadas en JavaScript, se suele emplear un preprocesador CSS como SASS o herramientas de CSS-in-JS. A continuación se muestra un ejemplo básico utilizando Styled Components:

```javascript
import styled from 'styled-components';

const Botón = styled.button`
  background-color: blue;
  color: white;
  
  &:hover {
    background-color: darkblue;
  }
  
  .icono {
    margin-right: 8px;
  }
`;
```

En el ejemplo anterior, las declaraciones CSS para el botón se anidan, lo que permite definir un estilo de hover y un estilo para un elemento interno (icono) de manera clara y organizada.

## Ejemplos
### Ejemplo 1: Uso básico de Declaraciones Anidadas

```javascript
import styled from 'styled-components';

const Tarjeta = styled.div`
  border: 1px solid #ccc;
  padding: 16px;

  h1 {
    font-size: 24px;
  }

  p {
    color: gray;
  }
`;
```

### Ejemplo 2: Anidación con pseudoclases

```javascript
import styled from 'styled-components';

const Enlace = styled.a`
  color: blue;
  
  &:hover {
    text-decoration: underline;
  }
  
  &.activo {
    color: red;
  }
`;
```

## Explicación
Al trabajar con Declaraciones CSS Anidadas, es importante tener en cuenta algunos puntos:

- **Compatibilidad**: No todos los navegadores soportan CSS anidado de forma nativa. Por ello, el uso de preprocesadores es recomendado.
- **Mantenimiento**: Aunque la anidación puede hacer que el código sea más legible, un uso excesivo puede llevar a un CSS complicado y difícil de depurar.
- **Especificidad**: La anidación puede aumentar la especificidad de los selectores, lo que puede causar problemas si no se gestiona adecuadamente.

## Resumen en una línea
Las Declaraciones CSS Anidadas permiten estructurar el CSS de manera jerárquica en proyectos JavaScript, mejorando la legibilidad y el mantenimiento del código.