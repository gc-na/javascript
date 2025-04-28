<!--
Meta Description: # BackgroundFetchRecord: Manejo de Descargas en Segundo Plano con JavaScript ## Sinopsis `BackgroundFetchRecord` es una interfaz de la API de Backgrou...
Meta Keywords: que, descarga, los, backgroundfetchrecord, descargas
-->

# BackgroundFetchRecord: Manejo de Descargas en Segundo Plano con JavaScript

## Sinopsis
`BackgroundFetchRecord` es una interfaz de la API de Background Fetch en JavaScript que permite a los desarrolladores gestionar y almacenar descargas en segundo plano, mejorando la experiencia del usuario al permitir que las aplicaciones web realicen descargas incluso cuando no están abiertas.

## Documentación

### Propósito
`BackgroundFetchRecord` permite a los desarrolladores acceder a la información sobre las descargas en segundo plano que se han iniciado a través de la API de Background Fetch. Esta interfaz proporciona métodos y propiedades que permiten monitorear el progreso de las descargas, así como gestionar los datos descargados.

### Uso
La API de Background Fetch es especialmente útil para aplicaciones que requieren la descarga de archivos grandes, como imágenes o documentos, sin interrumpir la experiencia del usuario. `BackgroundFetchRecord` es una parte integral de esta API, proporcionando un manejo eficiente de estas operaciones.

### Detalles
- **Propiedades**:
  - `id`: Un identificador único para la descarga.
  - `upload`: Información sobre cualquier archivo que se esté subiendo.
  - `downloads`: Una colección de archivos que se están descargando.
  - `state`: El estado actual de la descarga (e.g., "en curso", "completada").

- **Métodos**:
  - `abort()`: Cancela la descarga en curso.
  - `getFiles()`: Devuelve los archivos que se están descargando.

## Ejemplos

### Ejemplo Básico de Uso
```javascript
async function iniciarDescarga() {
    const registration = await navigator.serviceWorker.ready;
    const fetchRecord = await registration.backgroundFetch.fetch("descargaEjemplo", [
        new Request("https://ejemplo.com/archivo.zip"),
    ]);

    console.log(`Descarga iniciada: ${fetchRecord.id}`);
    
    fetchRecord.onprogress = (event) => {
        console.log(`Progreso: ${event.done} de ${event.total} bytes descargados.`);
    };
    
    fetchRecord.onsuccess = () => {
        console.log("Descarga completada exitosamente.");
    };
    
    fetchRecord.onerror = () => {
        console.error("Error en la descarga.");
    };
}
```

## Explicación
Un error común al trabajar con `BackgroundFetchRecord` es no manejar adecuadamente los estados de la descarga. Es crucial implementar controladores de eventos como `onprogress`, `onsuccess`, y `onerror` para reaccionar a los diferentes estados de la descarga. Además, es importante verificar la compatibilidad del navegador, ya que no todos los navegadores soportan la API de Background Fetch.

## Resumen en una Línea
`BackgroundFetchRecord` es una interfaz de JavaScript que permite gestionar de manera eficiente las descargas en segundo plano en aplicaciones web.