<!--
Meta Description: # Understanding GPUMapMode in JavaScript: A Comprehensive Guide ## Synopsis GPUMapMode is a crucial enumeration in the WebGPU API, which defines the a...
Meta Keywords: buffer, gpumapmode, data, gpu, writing
-->

# Understanding GPUMapMode in JavaScript: A Comprehensive Guide

## Synopsis
GPUMapMode is a crucial enumeration in the WebGPU API, which defines the accessibility modes for mapped buffer resources in JavaScript. It plays an essential role in optimizing GPU resource management for high-performance graphics and computation tasks.

## Documentation

### Purpose
GPUMapMode specifies how a buffer is accessed when it is mapped to the CPU in the WebGPU context. This is particularly important for developers working with graphics applications that leverage GPU acceleration, allowing for efficient data transfer and manipulation between the CPU and GPU.

### Usage
GPUMapMode is primarily used with the `GPUBuffer.mapAsync()` method, which allows developers to map a GPU buffer for reading or writing from the CPU. The mode you choose affects how you can interact with the mapped buffer. 

### Enum Values
GPUMapMode includes the following values:
- **GPUMapMode.READ**: Allows the mapped buffer to be read by the CPU. This is typically used when you need to retrieve data from the GPU.
- **GPUMapMode.WRITE**: Enables writing data to the mapped buffer from the CPU. This is used when you want to send new data to the GPU for processing.
- **GPUMapMode.READ_WRITE**: A combination of both read and write access. Use this mode if you need to both read from and write to the buffer.

### Syntax Example
Here’s how to use GPUMapMode in conjunction with the WebGPU API:

```javascript
// Create a GPU device and buffer
const device = await navigator.gpu.requestDevice();
const buffer = device.createBuffer({
    size: 1024,
    usage: GPUBufferUsage.STORAGE | GPUBufferUsage.COPY_DST
});

// Map the buffer to the CPU for writing
await buffer.mapAsync(GPUMapMode.WRITE);

// Access the mapped buffer
const mappedRange = new Uint8Array(buffer.getMappedRange());
mappedRange[0] = 42; // Write data to the buffer

// Unmap the buffer after writing
buffer.unmap();
```

## Examples

### Example 1: Reading Data from GPU Buffer
```javascript
// Create a buffer and map it for reading
await buffer.mapAsync(GPUMapMode.READ);
const readData = new Float32Array(buffer.getMappedRange());

// Process read data
console.log(readData);

// Unmap the buffer after reading
buffer.unmap();
```

### Example 2: Writing Data to GPU Buffer
```javascript
// Create a buffer and map it for writing
await buffer.mapAsync(GPUMapMode.WRITE);
const writeData = new Uint8Array(buffer.getMappedRange());
writeData.set([1, 2, 3, 4]);

// Unmap the buffer after writing
buffer.unmap();
```

### Example 3: Read and Write Access
```javascript
// Create a buffer and map it for both reading and writing
await buffer.mapAsync(GPUMapMode.READ_WRITE);
const data = new Float32Array(buffer.getMappedRange());

// Modify the data
data[0] = 100;

// Unmap the buffer after operations
buffer.unmap();
```

## Explanation
When working with GPUMapMode, it's essential to be aware of the following common pitfalls:

- **Mapping Modes**: Ensure you select the correct mapping mode based on your requirements. Using `GPUMapMode.WRITE` when you only need to read can lead to unexpected behavior.
- **Unmapping**: Always remember to unmap the buffer after completing operations to avoid memory leaks and ensure that changes are sent to the GPU.
- **Buffer Usage**: The buffer's usage flags must align with the map mode. For example, a buffer marked with `GPUBufferUsage.COPY_SRC` may not be suitable for writing data.

## One Line Summary
GPUMapMode is an enumeration in the WebGPU API that defines how buffers can be accessed by the CPU when mapped, impacting performance and data management in JavaScript applications.