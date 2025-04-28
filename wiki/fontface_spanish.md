<!--
Meta Description: # FontFace en JavaScript: Carga y Gestión de Fuentes Web ## Sinopsis FontFace es una interfaz de JavaScript que permite a los desarrolladores cargar y...
Meta Keywords: fuente, error, fontface, fuentes, que
-->

# FontFace en JavaScript: Carga y Gestión de Fuentes Web

## Sinopsis
FontFace es una interfaz de JavaScript que permite a los desarrolladores cargar y gestionar fuentes web de manera dinámica en aplicaciones web. Facilita la inclusión de fuentes personalizadas, mejorando la tipografía y la estética de las páginas.

## Documentación
### Propósito
La interfaz `FontFace` es utilizada para crear y manipular objetos de fuentes que pueden ser utilizadas en documentos HTML, permitiendo a los desarrolladores tener control total sobre la carga y aplicación de fuentes.

### Uso
Se puede definir una nueva fuente utilizando el constructor `FontFace`, y luego añadirla al documento utilizando el método `document.fonts.add()`. También es posible verificar si la fuente se ha cargado correctamente mediante `FontFace.load()`.

#### Sintaxis
```javascript
let fuente = new FontFace('NombreFuente', 'url(fuente.woff2)');
document.fonts.add(fuente);
fuente.load().then(function(loadedFont) {
    console.log('Fuente cargada:', loadedFont);
}).catch(function(error) {
    console.error('Error al cargar la fuente:', error);
});
```

### Detalles
- **Constructor**: `FontFace(nombre, fuente, opciones)`
  - **nombre**: El nombre de la fuente.
  - **fuente**: La URL donde se encuentra la fuente.
  - **opciones**: Objeto opcional que puede incluir propiedades como `style`, `weight`, `stretch`, entre otras.

- **Métodos**:
  - `load()`: Carga la fuente y devuelve una promesa que se resuelve una vez que la fuente está disponible.
  - `unicodeRange`: Permite especificar el rango de caracteres soportados.

## Ejemplos
### Ejemplo Básico
```javascript
let miFuente = new FontFace('Roboto', 'url(https://example.com/roboto.woff2)');
document.fonts.add(miFuente);

miFuente.load().then(() => {
    document.body.style.fontFamily = 'Roboto, sans-serif';
    console.log('Roboto ha sido cargada y aplicada.');
}).catch((error) => {
    console.error('Error al cargar la fuente:', error);
});
```

### Ejemplo con Estilo y Peso
```javascript
let fuenteNegrita = new FontFace('OpenSans', 'url(https://example.com/opensans-bold.woff2)', {
    style: 'normal',
    weight: '700'
});
document.fonts.add(fuenteNegrita);

fuenteNegrita.load().then(() => {
    document.body.style.fontFamily = 'OpenSans, sans-serif';
    console.log('OpenSans en negrita ha sido cargada.');
}).catch((error) => {
    console.error('Error al cargar la fuente:', error);
});
```

## Explicación
### Problemas Comunes
- **CORS**: Asegúrate de que las fuentes están alojadas en un servidor que permite el acceso desde tu dominio. De lo contrario, la carga fallará debido a restricciones de seguridad.
- **Formato de Fuente**: Verifica que el formato de la fuente sea compatible con los navegadores que estás utilizando. Los formatos como WOFF y WOFF2 son ampliamente soportados.
- **Promesas No Resueltas**: Siempre maneja las promesas devueltas por `load()` para evitar problemas de fuentes no cargadas.

### Notas Adicionales
- La gestión de fuentes a través de `FontFace` es especialmente útil en aplicaciones SPA (Single Page Applications) donde se requiere una carga dinámica de fuentes.
- Considera la optimización de fuentes para mejorar la velocidad de carga de tu sitio web.

## Resumen en Una Frase
La interfaz `FontFace` en JavaScript permite cargar y gestionar fuentes web de manera dinámica, mejorando la tipografía de las aplicaciones web.