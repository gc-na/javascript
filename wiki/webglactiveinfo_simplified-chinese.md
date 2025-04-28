<!--
Meta Description: # WebGLActiveInfo：JavaScript中的WebGL活跃信息 ## 摘要 WebGLActiveInfo是WebGL API中的一个接口，用于提供有关WebGL着色器程序中活跃属性和统一变量的信息。它帮助开发者获取变量的类型、大小及名称，进而高效地进行图形渲染。 ## 文档 Web...
Meta Keywords: const, program, info, size, name
-->

# WebGLActiveInfo：JavaScript中的WebGL活跃信息

## 摘要
WebGLActiveInfo是WebGL API中的一个接口，用于提供有关WebGL着色器程序中活跃属性和统一变量的信息。它帮助开发者获取变量的类型、大小及名称，进而高效地进行图形渲染。

## 文档
WebGLActiveInfo接口主要用于在WebGL上下文中获取关于着色器程序中活跃变量的信息。通过调用`getActiveAttrib`和`getActiveUniform`方法，开发者可以获得与特定变量相关的WebGLActiveInfo对象。

### 目的
WebGLActiveInfo的目的是提供关于活跃属性和统一变量的详细信息，使开发者能够更好地管理和使用这些变量。

### 用法
1. **获取活跃属性信息**：
   ```javascript
   const gl = canvas.getContext('webgl');
   const program = gl.createProgram();
   // ...着色器编译和程序链接...
   const activeInfo = gl.getActiveAttrib(program, index);
   ```

2. **获取活跃统一变量信息**：
   ```javascript
   const activeUniformInfo = gl.getActiveUniform(program, index);
   ```

### 详细信息
- **属性**：
  - `size`：表示变量的数量，例如一个vec3的size为3。
  - `type`：表示变量的数据类型，例如`gl.FLOAT`或`gl.INT`。
  - `name`：变量的名称，通常是着色器代码中定义的名称。

- **方法**：
  - `getActiveAttrib(program, index)`：返回指定程序中指定索引的活跃属性的WebGLActiveInfo对象。
  - `getActiveUniform(program, index)`：返回指定程序中指定索引的活跃统一变量的WebGLActiveInfo对象。

## 示例
### 示例1：获取活跃属性信息
```javascript
const gl = canvas.getContext('webgl');
const program = gl.createProgram();
// 假设已编译和链接着色器
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
    const info = gl.getActiveAttrib(program, i);
    console.log(`Name: ${info.name}, Type: ${info.type}, Size: ${info.size}`);
}
```

### 示例2：获取活跃统一变量信息
```javascript
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numUniforms; i++) {
    const info = gl.getActiveUniform(program, i);
    console.log(`Name: ${info.name}, Type: ${info.type}, Size: ${info.size}`);
}
```

## 说明
- **常见问题**：
  - 确保在程序链接完成后调用`getActiveAttrib`或`getActiveUniform`，否则将返回`null`。
  - 注意`size`属性的值，特别是对于数组类型的变量，可能需要额外处理。

- **附加说明**：
  - 在实际应用中，变量的`name`可能会受到编译优化的影响，因此在调试时最好使用调试工具查看最终的变量名称。

## 一句话总结
WebGLActiveInfo提供了WebGL着色器程序中活跃属性和统一变量的详细信息，帮助开发者优化图形渲染。