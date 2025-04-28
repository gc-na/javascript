<!--
Meta Description: # WebGLActiveInfo en JavaScript: Entendiendo la Información Activa de WebGL ## Sinopsis WebGLActiveInfo es un objeto en el contexto de WebGL que propo...
Meta Keywords: const, program, info, que, programa
-->

# WebGLActiveInfo en JavaScript: Entendiendo la Información Activa de WebGL

## Sinopsis
WebGLActiveInfo es un objeto en el contexto de WebGL que proporciona información sobre las variables activas en un programa de sombreado. Incluye detalles como el tipo y el tamaño de las variables, lo que permite a los desarrolladores gestionar eficientemente los atributos y uniformes en sus shaders.

## Documentación
### Propósito
WebGLActiveInfo se utiliza para obtener detalles sobre las variables activas en un programa de sombreado, que son esenciales para comprender cómo se pueden utilizar en la programación gráfica con WebGL.

### Uso
Para acceder a un objeto WebGLActiveInfo, se utiliza el método `gl.getActiveAttrib()` o `gl.getActiveUniform()`. Estos métodos devuelven información sobre los atributos y uniformes activos de un programa WebGL.

### Detalles
- **Tipo**: El tipo de variable (ej: FLOAT, INT, BOOL, etc.).
- **Tamaño**: El número de elementos que contiene la variable (puede ser 1 para tipos simples o más para vectores/matrices).
- **Nombre**: El nombre de la variable según se definió en el shader.

Ejemplo de uso:
```javascript
const program = gl.createProgram();
// Suponiendo que se han adjuntado shaders y se ha linkeado el programa
const numAttribs = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);

for (let i = 0; i < numAttribs; i++) {
    const info = gl.getActiveAttrib(program, i);
    console.log(`Nombre: ${info.name}, Tipo: ${info.type}, Tamaño: ${info.size}`);
}
```

## Ejemplos
### Ejemplo básico de uso con atributos
```javascript
const canvas = document.getElementById('miCanvas');
const gl = canvas.getContext('webgl');

// Creación y enlace de shaders
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
// Código del shader...
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);
const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
// Código del shader...
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

// Creación del programa
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);
gl.useProgram(program);

// Obtener información de atributos
const numAttribs = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttribs; i++) {
    const info = gl.getActiveAttrib(program, i);
    console.log(`Atributo: ${info.name}, Tipo: ${info.type}, Tamaño: ${info.size}`);
}
```

### Ejemplo básico de uso con uniformes
```javascript
// Obtener información de uniformes
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numUniforms; i++) {
    const info = gl.getActiveUniform(program, i);
    console.log(`Uniforme: ${info.name}, Tipo: ${info.type}, Tamaño: ${info.size}`);
}
```

## Explicación
Un error común al trabajar con WebGLActiveInfo es no verificar si el programa se ha vinculado correctamente antes de intentar obtener información sobre sus atributos y uniformes. Asegúrate de que el programa esté en estado `LINKED` antes de llamar a `getActiveAttrib()` o `getActiveUniform()`. Además, recuerda que WebGL es sensible a la capitalización, así que los nombres de las variables deben coincidir exactamente con los definidos en los shaders.

## Resumen en una línea
WebGLActiveInfo es un objeto que proporciona información sobre los atributos y uniformes activos en un programa de sombreado en WebGL, facilitando la gestión de variables en la programación gráfica.