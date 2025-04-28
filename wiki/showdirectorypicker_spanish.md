<!--
Meta Description: # showDirectoryPicker: Selección de Directorios en JavaScript ## Sinopsis `showDirectoryPicker` es una API de JavaScript que permite a los desarrollad...
Meta Keywords: directorio, showdirectorypicker, error, una, que
-->

# showDirectoryPicker: Selección de Directorios en JavaScript

## Sinopsis
`showDirectoryPicker` es una API de JavaScript que permite a los desarrolladores abrir un cuadro de diálogo para que los usuarios seleccionen un directorio del sistema de archivos. Esta funcionalidad es parte de la API de File System Access, que ofrece una forma más directa y segura de interactuar con el sistema de archivos del usuario.

## Documentación
### Propósito
El método `showDirectoryPicker` se utiliza para facilitar la selección de directorios por parte de los usuarios, permitiendo a las aplicaciones web acceder a archivos y carpetas de manera más intuitiva y controlada. Esto es especialmente útil en aplicaciones que requieren la carga o manejo de múltiples archivos.

### Uso
La función `showDirectoryPicker` se invoca en un contexto asíncrono y retorna un objeto `FileSystemDirectoryHandle`, que representa la carpeta seleccionada por el usuario. La función debe ser llamada en respuesta a una acción del usuario (por ejemplo, un clic en un botón) debido a las restricciones de seguridad del navegador.

### Detalles
- **Sintaxis**: 
  ```javascript
  async function seleccionarDirectorio() {
      const directorio = await window.showDirectoryPicker();
      // Aquí puedes realizar operaciones con el directorio seleccionado
  }
  ```

- **Parámetros**: No acepta parámetros.
- **Retorno**: Devuelve una promesa que se resuelve en un `FileSystemDirectoryHandle`.

## Ejemplos
### Ejemplo Básico
```javascript
document.getElementById('btnSeleccionarDirectorio').addEventListener('click', async () => {
    try {
        const directorio = await window.showDirectoryPicker();
        console.log(`Directorio seleccionado: ${directorio.name}`);
    } catch (error) {
        console.error('Error al seleccionar el directorio:', error);
    }
});
```

### Ejemplo de Acceso a Archivos en el Directorio Seleccionado
```javascript
document.getElementById('btnSeleccionarDirectorio').addEventListener('click', async () => {
    try {
        const directorio = await window.showDirectoryPicker();
        for await (const entrada of directorio.values()) {
            console.log(`Archivo o carpeta: ${entrada.name}`);
        }
    } catch (error) {
        console.error('Error al acceder al directorio:', error);
    }
});
```

## Explicación
Al utilizar `showDirectoryPicker`, es importante tener en cuenta las siguientes consideraciones:
- **Permisos**: La API solo se puede utilizar en un contexto seguro (HTTPS) o en localhost, debido a preocupaciones de seguridad.
- **Interacción del Usuario**: Debe ser invocada como resultado de una acción del usuario para evitar bloqueos por parte del navegador.
- **Compatibilidad**: No todos los navegadores pueden soportar esta API, por lo que es recomendable verificar la compatibilidad en [MDN](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API).

## Resumen en Una Línea
`showDirectoryPicker` permite a los usuarios seleccionar un directorio en su sistema de archivos a través de una interfaz sencilla y segura en aplicaciones web.