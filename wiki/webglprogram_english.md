<!--
Meta Description: # WebGLProgram: The Essential JavaScript Object for Rendering Shaders ## Synopsis `WebGLProgram` is a JavaScript object in the WebGL API that represen...
Meta Keywords: program, shaders, webglprogram, shader, const
-->

# WebGLProgram: The Essential JavaScript Object for Rendering Shaders

## Synopsis
`WebGLProgram` is a JavaScript object in the WebGL API that represents a compiled shader program, enabling developers to utilize vertex and fragment shaders for rendering 2D and 3D graphics in web applications.

## Documentation

### Purpose
`WebGLProgram` is an integral part of the WebGL API, which provides a way to interact with the GPU for rendering graphics directly in the browser. It allows developers to load and compile shaders written in GLSL (OpenGL Shading Language), link them together, and use them to render graphics efficiently.

### Usage
To create a `WebGLProgram`, you typically follow these steps:

1. **Obtain a WebGL Rendering Context**: This is done through a `<canvas>` element.
2. **Compile Shader Sources**: Create and compile vertex and fragment shaders.
3. **Link Shaders into a Program**: Use the `linkProgram` method to create a `WebGLProgram`.
4. **Use the Program**: Activate the program for rendering using `useProgram`.

### Details
- **Constructor**: The `WebGLProgram` object does not have a constructor; it is created via the `linkProgram` method of a `WebGLRenderingContext`.
- **Methods**: You cannot directly manipulate a `WebGLProgram` after it has been created. Instead, you use it in conjunction with WebGL methods such as `useProgram`, `getAttribLocation`, and `getUniformLocation`.
- **Status**: You can check the link status of a program using `getProgramParameter` with `gl.LINK_STATUS`.

## Examples

### Basic Example of Creating a WebGLProgram
```javascript
// Get the canvas element
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// Vertex shader source
const vertexShaderSource = `
  attribute vec4 position;
  void main() {
    gl_Position = position;
  }
`;

// Fragment shader source
const fragmentShaderSource = `
  void main() {
    gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // Red color
  }
`;

// Create and compile shaders
function createShader(gl, source, type) {
    const shader = gl.createShader(type);
    gl.shaderSource(shader, source);
    gl.compileShader(shader);
    return shader;
}

const vertexShader = createShader(gl, vertexShaderSource, gl.VERTEX_SHADER);
const fragmentShader = createShader(gl, fragmentShaderSource, gl.FRAGMENT_SHADER);

// Create a program and link shaders
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// Use the program
gl.useProgram(program);
```

## Explanation

### Common Pitfalls
- **Shader Compilation Errors**: If shaders fail to compile, the program may not link correctly. Always check for compilation errors using `getShaderInfoLog`.
- **Linking Issues**: Ensure that all attributes and uniforms you intend to use are properly defined in the shaders and linked to the program.
- **State Management**: Remember to call `useProgram` before rendering; otherwise, the GPU will not know which shaders to execute.

### Additional Notes
- The `WebGLProgram` object is not directly manipulable after creation. Changes to shaders require re-linking.
- Debugging WebGL programs can be challenging. Utilize browser developer tools and check logs for detailed errors.

## One Line Summary
`WebGLProgram` is a JavaScript object that links compiled vertex and fragment shaders for rendering graphics using WebGL in web applications.