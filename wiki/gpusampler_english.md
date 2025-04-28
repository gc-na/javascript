<!--
Meta Description: # GPUSampler in JavaScript: A Comprehensive Guide ## Synopsis GPUSampler is a JavaScript interface used in WebGPU for managing texture sampling parame...
Meta Keywords: texture, gpusampler, device, filtering, default
-->

# GPUSampler in JavaScript: A Comprehensive Guide

## Synopsis
GPUSampler is a JavaScript interface used in WebGPU for managing texture sampling parameters, enabling developers to access and manipulate textures efficiently in web applications.

## Documentation

### Purpose
GPUSampler is a crucial component in the WebGPU API, which allows developers to create high-performance graphics applications. It provides control over how textures are sampled, defining filtering methods, addressing modes, and anisotropy levels, essential for rendering 2D and 3D graphics accurately.

### Usage
To use GPUSampler, you first need to initialize a GPU device and create a GPU texture. After setting up your texture, you can create a GPUSampler object by calling the `device.createSampler()` method. This object can then be passed to your rendering pipeline to influence how textures are sampled during rendering operations.

### Details
- **Filtering**: GPUSampler supports various filtering modes, including:
  - `minFilter`: The filter used when the texture is minified.
  - `magFilter`: The filter used when the texture is magnified.
  
- **Address Modes**: Specifies how texture coordinates outside the [0, 1] range are treated:
  - `clamp-to-edge`
  - `repeat`
  - `mirror-repeat`

- **Anisotropy**: The degree of anisotropic filtering, which can improve texture quality when viewed at sharp angles.

### GPUSampler Properties
- `minFilter`: Defines the filter used for minification (default is `nearest`).
- `magFilter`: Defines the filter used for magnification (default is `nearest`).
- `mipmapFilter`: The filter used for mipmap selection (default is `nearest`).
- `addressModeU`: Addressing mode for the U coordinate (default is `clamp-to-edge`).
- `addressModeV`: Addressing mode for the V coordinate (default is `clamp-to-edge`).
- `addressModeW`: Addressing mode for the W coordinate (default is `clamp-to-edge`).
- `maxAnisotropy`: Maximum anisotropic filtering level (default is 1).

## Examples

### Basic Usage Example
```javascript
// Create a GPU device
const adapter = await navigator.gpu.requestAdapter();
const device = await adapter.requestDevice();

// Create a texture
const texture = device.createTexture({
    size: [512, 512],
    format: 'rgba8unorm',
    usage: GPUTextureUsage.TEXTURE_BINDING | GPUTextureUsage.COPY_DST
});

// Create a GPUSampler
const sampler = device.createSampler({
    minFilter: 'linear',
    magFilter: 'linear',
    addressModeU: 'repeat',
    addressModeV: 'repeat',
    maxAnisotropy: 4
});

// Use the sampler in a render pass
const renderPassDescriptor = {
    colorAttachments: [{
        view: /* your texture view */,
        loadOp: 'clear',
        storeOp: 'store',
        clearValue: { r: 0, g: 0, b: 0, a: 1 }
    }]
};

// Render with the sampler
const commandEncoder = device.createCommandEncoder();
const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);
passEncoder.setPipeline(/* your pipeline */);
passEncoder.setBindGroup(0, /* your bind group with texture and sampler */);
passEncoder.draw(/* your draw call parameters */);
passEncoder.endPass();
device.queue.submit([commandEncoder.finish()]);
```

## Explanation
When working with GPUSampler, developers should be aware of the following common pitfalls:
- **Filtering Mismatch**: Ensure that the filtering modes selected for minification and magnification are suitable for the intended visual output to avoid poor quality textures.
- **Address Mode Confusion**: Understand the implications of each addressing mode, especially when dealing with textures that may be sampled outside their normalized range.
- **Performance Considerations**: High anisotropy levels can improve visual fidelity but may incur performance costs; balance quality and performance based on the target device capabilities.

## One Line Summary
GPUSampler is an essential WebGPU interface in JavaScript that manages texture sampling parameters for high-quality graphics rendering.