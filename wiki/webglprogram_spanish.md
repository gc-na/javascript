<!--
Meta Description: # WebGLProgram en JavaScript: Guía Completa ## Sinopsis WebGLProgram es un objeto en WebGL que representa un programa de sombreado, compuesto por un v...
Meta Keywords: const, shader, programa, program, javascript
-->

# WebGLProgram en JavaScript: Guía Completa

## Sinopsis
WebGLProgram es un objeto en WebGL que representa un programa de sombreado, compuesto por un vertex shader y un fragment shader, utilizado para renderizar gráficos 2D y 3D en aplicaciones web.

## Documentación
### Propósito
WebGLProgram permite a los desarrolladores de JavaScript crear y gestionar shaders que son esenciales para el procesamiento gráfico en la web. Los shaders son pequeños programas que se ejecutan en la GPU y permiten realizar cálculos complejos de forma eficiente.

### Uso
Para utilizar WebGLProgram, primero se debe crear un contexto WebGL, compilar los shaders y luego enlazarlos en un programa. El programa se activa mediante el método `useProgram()` del contexto WebGL.

### Detalles

1. **Creación de un Contexto WebGL**:
   ```javascript
   const canvas = document.getElementById('miCanvas');
   const gl = canvas.getContext('webgl');
   ```

2. **Compilación de Shaders**:
   Los shaders se deben compilar individualmente antes de crear el programa.
   ```javascript
   function crearShader(gl, tipo, fuente) {
       const shader = gl.createShader(tipo);
       gl.shaderSource(shader, fuente);
       gl.compileShader(shader);
       const exito = gl.getShaderParameter(shader, gl.COMPILE_STATUS);
       if (!exito) {
           console.error(gl.getShaderInfoLog(shader));
           gl.deleteShader(shader);
           return null;
       }
       return shader;
   }
   ```

3. **Creación del Programa**:
   Después de compilar los shaders, se pueden enlazar en un programa.
   ```javascript
   const vertexShader = crearShader(gl, gl.VERTEX_SHADER, vertexShaderSource);
   const fragmentShader = crearShader(gl, gl.FRAGMENT_SHADER, fragmentShaderSource);
   const program = gl.createProgram();
   gl.attachShader(program, vertexShader);
   gl.attachShader(program, fragmentShader);
   gl.linkProgram(program);
   ```

4. **Activación del Programa**:
   El programa se activa para que sus shaders se utilicen en el renderizado.
   ```javascript
   gl.useProgram(program);
   ```

## Ejemplos
### Ejemplo Básico
```javascript
const canvas = document.getElementById('miCanvas');
const gl = canvas.getContext('webgl');

const vertexShaderSource = `
    attribute vec4 a_Position;
    void main() {
        gl_Position = a_Position;
    }
`;

const fragmentShaderSource = `
    void main() {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // Color rojo
    }
`;

const vertexShader = crearShader(gl, gl.VERTEX_SHADER, vertexShaderSource);
const fragmentShader = crearShader(gl, gl.FRAGMENT_SHADER, fragmentShaderSource);
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);
gl.useProgram(program);
```

## Explicación
### Problemas Comunes
- **Error en la Compilación del Shader**: Asegúrate de revisar los logs de error después de intentar compilar un shader, ya que un error en la sintaxis puede causar que el programa no funcione.
- **Uso de `useProgram()`**: Asegúrate de llamar a `useProgram()` antes de intentar dibujar cualquier objeto con el programa. De lo contrario, no se aplicarán los shaders correctamente.
- **Asignación de Atributos**: Antes de dibujar, los atributos del shader deben ser correctamente asignados con `gl.getAttribLocation()` y habilitados con `gl.enableVertexAttribArray()`.

## Resumen en Una Línea
WebGLProgram es un objeto clave en WebGL que permite la creación y gestión de programas de sombreado para renderizar gráficos en aplicaciones JavaScript.