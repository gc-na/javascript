<!--
Meta Description: # showSaveFilePicker: Cómo utilizar el Selector de Archivos en JavaScript ## Sinopsis El método `showSaveFilePicker` permite a los desarrolladores web...
Meta Keywords: del, showsavefilepicker, para, await, método
-->

# showSaveFilePicker: Cómo utilizar el Selector de Archivos en JavaScript

## Sinopsis
El método `showSaveFilePicker` permite a los desarrolladores web abrir un cuadro de diálogo que permite a los usuarios seleccionar la ubicación y el nombre de un archivo para guardar. Esta función es parte de la API de Archivos del navegador y ofrece una forma sencilla y eficiente de manejar descargas de archivos en aplicaciones web.

## Documentación
### Propósito
El método `showSaveFilePicker` es utilizado para facilitar la interacción del usuario con el sistema de archivos, permitiendo guardar contenido generado por la aplicación directamente en la máquina del usuario.

### Uso
El método `showSaveFilePicker` se invoca como parte de la API de File System Access, que proporciona una interfaz moderna para interactuar con archivos y directorios en el sistema de archivos del usuario. 

#### Sintaxis
```javascript
const fileHandle = await window.showSaveFilePicker(options);
```

#### Parámetros
- **options** (opcional): Un objeto con las opciones para personalizar el cuadro de diálogo. Puede incluir propiedades como:
  - `suggestedName`: Un nombre de archivo sugerido.
  - `types`: Una lista de tipos MIME permitidos para el archivo.

### Detalles
- Este método devuelve un `FileSystemFileHandle`, que se puede utilizar para escribir datos en el archivo seleccionado.
- Es importante que este método se ejecute en respuesta a una acción del usuario, como un clic de botón, para cumplir con las políticas de seguridad del navegador.

## Ejemplos
### Ejemplo básico
```javascript
async function guardarArchivo() {
    const opts = {
        suggestedName: 'miArchivo.txt',
        types: [
            {
                description: 'Texto Plano',
                accept: {
                    'text/plain': ['.txt'],
                },
            },
        ],
    };

    try {
        const fileHandle = await window.showSaveFilePicker(opts);
        const writable = await fileHandle.createWritable();
        await writable.write('Hola, mundo!');
        await writable.close();
    } catch (err) {
        console.error('Error al guardar el archivo:', err);
    }
}
```

### Ejemplo con múltiples tipos
```javascript
async function guardarImagen() {
    const opts = {
        suggestedName: 'imagen.png',
        types: [
            {
                description: 'Imágenes PNG',
                accept: {
                    'image/png': ['.png'],
                },
            },
            {
                description: 'Imágenes JPEG',
                accept: {
                    'image/jpeg': ['.jpeg', '.jpg'],
                },
            },
        ],
    };

    try {
        const fileHandle = await window.showSaveFilePicker(opts);
        const writable = await fileHandle.createWritable();
        // Suponiendo que "data" es un Blob que contiene los datos de la imagen
        await writable.write(data);
        await writable.close();
    } catch (err) {
        console.error('Error al guardar la imagen:', err);
    }
}
```

## Explicación
### Errores comunes
1. **No ejecutar en respuesta a una acción del usuario**: Si `showSaveFilePicker` se llama fuera del contexto de un evento de usuario, el navegador lanzará un error.
2. **Compatibilidad del navegador**: No todos los navegadores admiten la API de File System Access. Asegúrate de verificar la compatibilidad antes de implementar esta función.

### Consideraciones de seguridad
El uso del método `showSaveFilePicker` está restringido por motivos de seguridad, y es esencial que los desarrolladores manejen adecuadamente las excepciones y errores para mejorar la experiencia del usuario.

## Resumen en una línea
El método `showSaveFilePicker` en JavaScript permite a los usuarios seleccionar la ubicación y el nombre de un archivo para guardar contenido generado por la aplicación de manera sencilla y eficiente.