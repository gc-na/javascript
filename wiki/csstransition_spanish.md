<!--
Meta Description: # CSSTransition: Transiciones CSS en JavaScript ## Sinopsis `CSSTransition` es una herramienta en React que permite gestionar transiciones CSS de mane...
Meta Keywords: csstransition, css, react, transiciones, que
-->

# CSSTransition: Transiciones CSS en JavaScript

## Sinopsis
`CSSTransition` es una herramienta en React que permite gestionar transiciones CSS de manera sencilla y eficiente en aplicaciones web, mejorando la experiencia visual y la usabilidad.

## Documentación
`CSSTransition` es un componente de la biblioteca `react-transition-group` que facilita la implementación de transiciones para elementos DOM. Su propósito principal es permitir que los desarrolladores apliquen clases CSS específicas en momentos clave de la transición, como al entrar o salir de la vista.

### Propósito
El objetivo de `CSSTransition` es proporcionar una forma controlada de aplicar transiciones a los elementos, asegurando que las animaciones se gestionen adecuadamente durante el ciclo de vida del componente.

### Uso
Para utilizar `CSSTransition`, primero necesitas instalar `react-transition-group` en tu proyecto:

```bash
npm install react-transition-group
```

Una vez instalado, puedes importar `CSSTransition` en tu componente React:

```javascript
import { CSSTransition } from 'react-transition-group';
```

### Propiedades Principales
- **in**: Booleano que indica si el componente debe estar presente en el DOM.
- **timeout**: Duración de la transición en milisegundos.
- **classNames**: Nombre base de la clase CSS a aplicar durante las transiciones.
- **onEnter**: Callback que se ejecuta cuando el componente entra.
- **onExit**: Callback que se ejecuta cuando el componente sale.

## Ejemplos

### Ejemplo Básico de Uso

Aquí tienes un ejemplo simple de cómo usar `CSSTransition` para animar un componente de texto:

```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css'; // Asegúrate de tener las clases CSS definidas aquí

const Example = () => {
  const [show, setShow] = useState(false);

  return (
    <div>
      <button onClick={() => setShow(!show)}>
        {show ? 'Ocultar' : 'Mostrar'}
      </button>
      <CSSTransition
        in={show}
        timeout={300}
        classNames="fade"
        unmountOnExit
      >
        <div className="fade">¡Hola, mundo!</div>
      </CSSTransition>
    </div>
  );
};

export default Example;
```

### Clases CSS de Ejemplo

```css
.fade-enter {
  opacity: 0;
}
.fade-enter-active {
  opacity: 1;
  transition: opacity 300ms;
}
.fade-exit {
  opacity: 1;
}
.fade-exit-active {
  opacity: 0;
  transition: opacity 300ms;
}
```

## Explicación
### Errores Comunes y Notas Adicionales
- **No Olvides las Clases CSS**: Asegúrate de definir las clases CSS correspondientes para las transiciones. Si no se definen, no habrá animaciones visibles.
- **Timeout Incorrecto**: El valor de `timeout` debe coincidir con la duración de tus transiciones CSS. Un desajuste puede causar comportamientos inesperados.
- **Re-renderizado**: Cambios en el estado que causan re-renderizados pueden interrumpir las transiciones. Usa `unmountOnExit` para evitar esto.

## Resumen en Una Línea
`CSSTransition` es un componente de React que simplifica la gestión de transiciones CSS, mejorando la apariencia y la dinámica de las aplicaciones web.