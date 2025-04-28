<!--
Meta Description: # FileList en JavaScript: Comprendiendo la Manipulación de Archivos ## Sinopsis El objeto `FileList` en JavaScript permite a los desarrolladores gesti...
Meta Keywords: archivos, filelist, que, input, los
-->

# FileList en JavaScript: Comprendiendo la Manipulación de Archivos

## Sinopsis
El objeto `FileList` en JavaScript permite a los desarrolladores gestionar y manipular colecciones de archivos seleccionados por el usuario a través de un input de tipo archivo. Este objeto es fundamental para aplicaciones web que requieren la carga y gestión de archivos.

## Documentación

### ¿Qué es FileList?
`FileList` es un objeto que representa una lista de archivos seleccionados en un elemento `<input>` de tipo `file`. Se utiliza principalmente en el contexto de la API de archivos de HTML5, lo que permite a los desarrolladores acceder a los archivos que los usuarios han elegido cargar.

### Propósito
El propósito de `FileList` es proporcionar una forma de acceder y manipular archivos de manera estructurada. Esto es especialmente útil en aplicaciones web que permiten la subida de archivos, como imágenes, documentos, etc.

### Uso
Para acceder a un objeto `FileList`, debes utilizar el elemento de entrada de archivos en tu HTML. A continuación, se muestra un ejemplo básico:

```html
<input type="file" id="fileInput" multiple>
```

En JavaScript, puedes acceder a la lista de archivos seleccionados de la siguiente manera:

```javascript
const input = document.getElementById('fileInput');
const fileList = input.files; // fileList es un objeto FileList
```

### Detalles
- **Propiedades**: `FileList` no tiene métodos, pero sí posee la propiedad `length`, que indica el número de archivos seleccionados.
- **Índices**: Puedes acceder a cada archivo individualmente usando la notación de corchetes, `fileList[index]`, donde `index` es un número que va desde `0` hasta `fileList.length - 1`.
- **Interacción con File**: Cada archivo dentro de un `FileList` es un objeto `File`, que contiene información sobre el archivo, como su nombre, tipo y tamaño.

## Ejemplos

### Ejemplo 1: Accediendo a archivos seleccionados
```javascript
document.getElementById('fileInput').addEventListener('change', function() {
    const files = this.files;
    for (let i = 0; i < files.length; i++) {
        console.log(`Archivo ${i + 1}: ${files[i].name}`);
    }
});
```

### Ejemplo 2: Comprobando el número de archivos
```javascript
const input = document.getElementById('fileInput');

if (input.files.length > 0) {
    console.log(`Se han seleccionado ${input.files.length} archivos.`);
} else {
    console.log('No se han seleccionado archivos.');
}
```

## Explicación
### Errores Comunes
1. **No soportar múltiples archivos**: Al no especificar el atributo `multiple`, solo se permitirá seleccionar un archivo, lo que puede ser confuso para los usuarios.
2. **No validar tipos de archivos**: Es importante verificar el tipo de archivo antes de procesarlo para evitar errores en la carga.
3. **Olvidar manejar eventos**: No agregar un evento `change` puede llevar a que no se procesen los archivos seleccionados correctamente.

### Notas Adicionales
- Los navegadores deben ser compatibles con HTML5 para que `FileList` funcione correctamente.
- Se recomienda siempre proporcionar retroalimentación al usuario sobre los archivos seleccionados, especialmente si se permiten múltiples selecciones.

## Resumen en Una Línea
`FileList` es un objeto en JavaScript que permite acceder y gestionar colecciones de archivos seleccionados por el usuario en un input de tipo archivo.