<!--
Meta Description: # WebGLActiveInfo: Understanding Active Info in WebGL with JavaScript ## Synopsis `WebGLActiveInfo` is an object in the WebGL API that provides detail...
Meta Keywords: program, active, const, webglactiveinfo, attributes
-->

# WebGLActiveInfo: Understanding Active Info in WebGL with JavaScript

## Synopsis
`WebGLActiveInfo` is an object in the WebGL API that provides detailed information about active attributes and uniforms in a WebGL program, essential for rendering 3D graphics using JavaScript.

## Documentation
`WebGLActiveInfo` is a built-in JavaScript object that plays a critical role in the WebGL API. It is returned by the `getActiveAttrib` and `getActiveUniform` methods of the `WebGLProgram` interface. This object contains vital information about the attributes and uniforms used within a WebGL shader program, allowing developers to better manage and optimize their rendering processes.

### Purpose
The primary purpose of `WebGLActiveInfo` is to give developers insights into the properties of the active variables (attributes and uniforms) in a shader, which can help in correctly binding data to these variables and managing shader state.

### Usage
To use `WebGLActiveInfo`, you first need to compile and link a shader program. After that, you can retrieve information about its attributes and uniforms:

1. **Get Program Reference**: Obtain a reference to your compiled and linked `WebGLProgram`.
2. **Access Active Attributes/Uniforms**: Use the `getProgramParameter` method with `gl.ACTIVE_ATTRIBUTES` or `gl.ACTIVE_UNIFORMS` to get the count of active variables.
3. **Loop Through Active Variables**: Use `getActiveAttrib` or `getActiveUniform` to retrieve `WebGLActiveInfo` objects, which contain the properties of each active variable.

### Properties
A `WebGLActiveInfo` object contains the following key properties:

- **size**: Indicates the number of elements in the variable (1 for scalars, 2 for vectors, etc.).
- **type**: Specifies the data type of the variable (e.g., `gl.FLOAT`, `gl.INT`, etc.).
- **name**: The name of the active variable as defined in the shader source code.

## Examples
Here’s a simple example that demonstrates how to use `WebGLActiveInfo` in a WebGL context:

```javascript
// Initialize WebGL context
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// Create and compile shaders (vertex and fragment)
const vertexShaderSource = `...`;
const fragmentShaderSource = `...`;
// Assume compileShader() is a function that compiles shaders

const vertexShader = compileShader(gl, gl.VERTEX_SHADER, vertexShaderSource);
const fragmentShader = compileShader(gl, gl.FRAGMENT_SHADER, fragmentShaderSource);

// Link the program
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// Use the program
gl.useProgram(program);

// Get active attributes
const numActiveAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numActiveAttributes; i++) {
    const activeInfo = gl.getActiveAttrib(program, i);
    console.log(`Attribute Name: ${activeInfo.name}, Size: ${activeInfo.size}, Type: ${activeInfo.type}`);
}

// Get active uniforms
const numActiveUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numActiveUniforms; i++) {
    const activeInfo = gl.getActiveUniform(program, i);
    console.log(`Uniform Name: ${activeInfo.name}, Size: ${activeInfo.size}, Type: ${activeInfo.type}`);
}
```

## Explanation
### Common Pitfalls
- **Not Checking Program Status**: Always ensure that your shader program is successfully linked before attempting to retrieve active attributes or uniforms.
- **Incorrect Variable Names**: If the names of attributes or uniforms in JavaScript do not match those in the shader code, you may not retrieve the expected results.
- **Data Type Mismatch**: Be aware of the data types of your attributes and uniforms. Mismatches can lead to rendering issues or runtime errors.

### Additional Notes
- `WebGLActiveInfo` does not provide information about inactive attributes or uniforms.
- The `size` property can be particularly useful when dealing with vectors or matrices, as it helps you understand how to bind data correctly.

## One Line Summary
`WebGLActiveInfo` is a crucial object in the WebGL API that provides essential details about active shader program variables, aiding in the effective rendering of 3D graphics with JavaScript.