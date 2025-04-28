<!--
Meta Description: # HTMLFrameSetElement en JavaScript: Guía Completa ## Sinopsis El `HTMLFrameSetElement` es una interfaz de JavaScript que representa un conjunto de ma...
Meta Keywords: html, uso, que, frameset, frame
-->

# HTMLFrameSetElement en JavaScript: Guía Completa

## Sinopsis
El `HTMLFrameSetElement` es una interfaz de JavaScript que representa un conjunto de marcos en un documento HTML, permitiendo dividir la ventana del navegador en varias secciones independientes. Aunque su uso ha disminuido con la llegada de HTML5, sigue siendo relevante para entender la estructura de documentos HTML antiguos.

## Documentación
El `HTMLFrameSetElement` se utiliza para definir un conjunto de marcos dentro de un documento HTML. Es parte de la especificación de HTML 4.01 y se emplea principalmente en la creación de diseños de páginas web que requieren múltiples vistas simultáneas.

### Propósito
- Permite dividir la ventana del navegador en varias áreas que pueden cargar diferentes documentos HTML.
- Facilita la navegación y organización de contenido en aplicaciones web más antiguas.

### Uso
La sintaxis básica para utilizar `HTMLFrameSetElement` es la siguiente:

```html
<frameset rows="50%,50%">
    <frame src="pagina1.html" />
    <frame src="pagina2.html" />
</frameset>
```

### Detalles
- **Atributos**: Los marcos pueden configurarse con varios atributos como `rows` y `cols` para definir su tamaño, así como `src` para especificar el contenido que se cargará en cada marco.
- **Obsolescencia**: Es importante considerar que `HTMLFrameSetElement` está obsoleto en HTML5 y se recomienda utilizar CSS y JavaScript para lograr efectos similares.

## Ejemplos
### Ejemplo 1: Uso Básico de `frameset`
```html
<!DOCTYPE html>
<html>
<head>
    <title>Ejemplo de FrameSet</title>
</head>
<frameset cols="25%,75%">
    <frame src="menu.html" />
    <frame src="contenido.html" />
</frameset>
</html>
```

### Ejemplo 2: Uso de `frame` con atributos
```html
<!DOCTYPE html>
<html>
<head>
    <title>Ejemplo de Frame con Atributos</title>
</head>
<frameset rows="100, *">
    <frame src="header.html" name="header" />
    <frame src="main.html" name="main" />
</frameset>
</html>
```

## Explicación
- **Obsolescencia y Alternativas**: Con la llegada de HTML5, el uso de `frames` y `framesets` ha caído en desuso debido a problemas de accesibilidad y SEO. Se recomienda el uso de técnicas modernas como el diseño responsivo y el uso de `<iframe>` o elementos de diseño CSS Grid o Flexbox.
- **Compatibilidad**: Asegúrate de que el uso de `HTMLFrameSetElement` no afecte la compatibilidad de tu sitio con navegadores modernos, ya que muchos de ellos pueden no soportar completamente esta técnica.

## Resumen en una Línea
`HTMLFrameSetElement` es una interfaz obsoleta en JavaScript que permite dividir la ventana del navegador en múltiples marcos, aunque su uso no es recomendado en HTML5.