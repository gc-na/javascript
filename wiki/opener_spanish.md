<!--
Meta Description: # Opener en JavaScript: Uso y Funcionalidades ## Sinopsis El término "opener" en JavaScript se refiere a la propiedad `opener` del objeto `window`, qu...
Meta Keywords: ventana, opener, window, que, padre
-->

# Opener en JavaScript: Uso y Funcionalidades

## Sinopsis

El término "opener" en JavaScript se refiere a la propiedad `opener` del objeto `window`, que permite acceder a la ventana que abrió la ventana actual. Esta propiedad es útil en situaciones donde se trabaja con ventanas emergentes o múltiples pestañas.

## Documentación

### Propósito

La propiedad `window.opener` se utiliza para referirse a la ventana que ha creado la ventana actual. Esto es especialmente relevante cuando se abren nuevas ventanas mediante el método `window.open()`, permitiendo la comunicación entre la ventana padre y la ventana hija.

### Uso

La propiedad `opener` se puede acceder de la siguiente manera:

```javascript
let ventanaHija = window.open('url.html', 'nombreVentana');
```

En la ventana hija, puedes acceder a la ventana que la abrió mediante:

```javascript
let ventanaPadre = window.opener;
```

Esto te permite manipular el DOM de la ventana padre desde la ventana hija, siempre y cuando ambas ventanas estén en el mismo dominio debido a las políticas de seguridad del navegador.

### Detalles

- **Tipo de Valor**: `opener` devuelve una referencia al objeto `window` de la ventana que abrió la ventana actual, o `null` si no hay ninguna ventana que la haya abierto.
- **Seguridad**: Los navegadores modernos restringen el acceso a `opener` en ciertos contextos (por ejemplo, si la ventana fue abierta a través de un enlace que especifica `rel="noopener"`) para prevenir ataques de tipo "reverse tabnabbing".

## Ejemplos

### Ejemplo Básico

**Ventana Padre**: Abriendo una nueva ventana.

```javascript
// Ventana Padre
function abrirVentana() {
    window.open('hija.html', 'ventanaHija');
}
```

**Ventana Hija**: Accediendo a la ventana padre.

```javascript
// Ventana Hija (hija.html)
if (window.opener) {
    window.opener.document.body.style.backgroundColor = 'lightblue'; // Cambia el color de fondo de la ventana padre
}
```

### Ejemplo con Condición de Seguridad

```javascript
// Ventana Hija (hija.html)
if (window.opener && !window.opener.closed) {
    console.log('La ventana padre está abierta.');
} else {
    console.log('La ventana padre no está disponible.');
}
```

## Explicación

Al trabajar con `window.opener`, es importante tener en cuenta lo siguiente:

- **Políticas de Seguridad**: Asegúrate de que ambas ventanas estén en el mismo dominio para evitar problemas de acceso.
- **Uso responsable**: Evita realizar cambios inesperados en la ventana padre, ya que esto puede afectar la experiencia del usuario.
- **Cierre de Ventanas**: Verifica si la ventana padre está abierta (`!window.opener.closed`) antes de intentar acceder a ella, para evitar errores en tiempo de ejecución.

## Resumen en una línea

La propiedad `opener` en JavaScript permite a las ventanas hijas acceder a la ventana que las abrió, facilitando la comunicación entre ellas en el mismo dominio.