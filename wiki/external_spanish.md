<!--
Meta Description: # Uso de "external" en JavaScript: Importación y Exportación de Módulos ## Sinopsis El término "external" en JavaScript se refiere a la práctica de im...
Meta Keywords: que, módulos, javascript, código, export
-->

# Uso de "external" en JavaScript: Importación y Exportación de Módulos

## Sinopsis
El término "external" en JavaScript se refiere a la práctica de importar y exportar módulos que permiten organizar y reutilizar el código de manera eficiente en aplicaciones web. Este artículo explora cómo utilizar la palabra clave `export` y `import`, así como su relación con módulos externos.

## Documentación
### Propósito
JavaScript permite la modularización del código mediante la creación de módulos. Los módulos son bloques de código que se pueden importar y exportar entre diferentes archivos, lo que facilita la gestión, prueba y mantenimiento del código. La importación y exportación de módulos "externos" permite que diferentes partes de una aplicación web interactúen de manera efectiva.

### Uso
Para utilizar módulos externos en JavaScript, se emplean las palabras clave `export` para exportar funciones, objetos o variables de un módulo y `import` para traer esos elementos a otro módulo.

#### Sintaxis básica
- **Exportar un módulo:**
  ```javascript
  // archivo.js
  export const miVariable = 42;
  
  export function miFuncion() {
      console.log('Hola desde miFuncion');
  }
  ```

- **Importar un módulo:**
  ```javascript
  // otroArchivo.js
  import { miVariable, miFuncion } from './archivo.js';
  
  console.log(miVariable); // 42
  miFuncion(); // 'Hola desde miFuncion'
  ```

### Detalles
1. **Exportaciones por defecto**: Un módulo puede tener una exportación por defecto, que se puede importar sin usar llaves.
   ```javascript
   // archivo.js
   const miVariable = 42;
   export default miVariable;
   ```
   ```javascript
   // otroArchivo.js
   import miVariable from './archivo.js';
   ```

2. **Módulos en el navegador**: Para utilizar módulos en el navegador, es necesario que el archivo HTML tenga el atributo `type="module"` en la etiqueta `<script>`.
   ```html
   <script type="module" src="otroArchivo.js"></script>
   ```

## Ejemplos
### Ejemplo 1: Exportación e Importación de Variables
```javascript
// variables.js
export const nombre = 'Juan';
export const edad = 30;

// main.js
import { nombre, edad } from './variables.js';
console.log(`Nombre: ${nombre}, Edad: ${edad}`);
```

### Ejemplo 2: Exportación por Defecto
```javascript
// saludo.js
const saludo = () => 'Hola Mundo';
export default saludo;

// main.js
import saludo from './saludo.js';
console.log(saludo()); // 'Hola Mundo'
```

## Explicación
### Errores Comunes
- **Rutas Incorrectas**: Asegúrate de que las rutas de los módulos sean correctas; de lo contrario, se generará un error de carga.
- **No Usar el Atributo type="module"**: Si se omite este atributo en la etiqueta `<script>`, el código del módulo no se ejecutará correctamente.
- **Exportaciones No Encontradas**: Importar elementos que no han sido exportados causará un error. Verifica que los nombres coincidan.

### Notas Adicionales
- Los módulos en JavaScript son de ámbito estricto por defecto, lo que significa que no se pueden utilizar variables no declaradas. Esto ayuda a evitar errores comunes en el código.
- La carga de módulos es asíncrona, lo que significa que el código se ejecuta en el orden en que se carga.

## Resumen en una Línea
El uso de "external" en JavaScript se refiere a la importación y exportación de módulos, lo que facilita la organización y reutilización del código en aplicaciones web.