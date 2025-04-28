<!--
Meta Description: # createImageBitmap: A Comprehensive Guide to JavaScript's Image Bitmap Creation ## Synopsis The `createImageBitmap` function in JavaScript provides d...
Meta Keywords: image, createimagebitmap, imagebitmap, error, bitmap
-->

# createImageBitmap: A Comprehensive Guide to JavaScript's Image Bitmap Creation

## Synopsis
The `createImageBitmap` function in JavaScript provides developers with a way to asynchronously create `ImageBitmap` objects from various image sources, enhancing performance for image manipulation and rendering in web applications.

## Documentation
### Purpose
`createImageBitmap` is a method that allows developers to create a bitmap representation of an image. This is particularly useful in scenarios involving the `<canvas>` element or when working with WebGL, as it offers a more efficient way to manipulate images.

### Usage
The `createImageBitmap` function can be called with the following syntax:

```javascript
createImageBitmap(imageSource[, options])
```

#### Parameters
- **imageSource**: This can be an `HTMLImageElement`, `HTMLCanvasElement`, `HTMLVideoElement`, `ImageBitmap`, or an `ImageData` object.
- **options** (optional): An object that can specify additional options for the image creation:
  - **resizeWidth**: The width to resize the image to.
  - **resizeHeight**: The height to resize the image to.
  - **imageOrientation**: A string indicating the image orientation (e.g., "flipY").

#### Return Value
The method returns a `Promise` that resolves to an `ImageBitmap` object.

### Example
Here are some basic usage examples demonstrating how to utilize `createImageBitmap`.

#### Example 1: Creating an ImageBitmap from an HTMLImageElement
```javascript
const img = new Image();
img.src = 'path/to/image.jpg';

img.onload = async () => {
    try {
        const bitmap = await createImageBitmap(img);
        console.log(bitmap); // Logs the ImageBitmap object
    } catch (error) {
        console.error('Error creating ImageBitmap:', error);
    }
};
```

#### Example 2: Creating an ImageBitmap from an HTMLCanvasElement
```javascript
const canvas = document.createElement('canvas');
const context = canvas.getContext('2d');

// Draw something on the canvas
context.fillStyle = 'red';
context.fillRect(0, 0, 100, 100);

createImageBitmap(canvas).then(bitmap => {
    console.log(bitmap); // Logs the ImageBitmap object
}).catch(error => {
    console.error('Error creating ImageBitmap:', error);
});
```

#### Example 3: Resizing an ImageBitmap
```javascript
const img = new Image();
img.src = 'path/to/image.jpg';

img.onload = async () => {
    try {
        const bitmap = await createImageBitmap(img, { resizeWidth: 50, resizeHeight: 50 });
        console.log(bitmap); // Logs the resized ImageBitmap object
    } catch (error) {
        console.error('Error creating ImageBitmap:', error);
    }
};
```

## Explanation
### Common Pitfalls and Gotchas
- **Asynchronous Nature**: Remember that `createImageBitmap` is asynchronous and returns a `Promise`. Ensure that you handle the promise correctly using `await` or `.then()`.
- **Image Loading**: Always wait for the image source to load before calling `createImageBitmap`. Failing to do so may lead to errors as the image might not be available yet.
- **Cross-Origin Images**: When using images from a different origin, ensure that CORS headers are set appropriately. Otherwise, you may encounter security errors.
- **Browser Compatibility**: While `createImageBitmap` is widely supported in modern browsers, always check for compatibility if you plan to support older browsers.

## One Line Summary
The `createImageBitmap` function in JavaScript enables efficient, asynchronous creation of `ImageBitmap` objects from various image sources, optimizing image processing in web applications.