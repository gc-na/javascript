<!--
Meta Description: # queryLocalFonts: Accessing Local Fonts in JavaScript ## Synopsis `queryLocalFonts` is a JavaScript API that allows developers to retrieve a list of ...
Meta Keywords: fonts, querylocalfonts, local, font, error
-->

# queryLocalFonts: Accessing Local Fonts in JavaScript

## Synopsis
`queryLocalFonts` is a JavaScript API that allows developers to retrieve a list of fonts installed on a user's local system. This feature is particularly useful for web applications that aim to customize typography based on the user's available fonts.

## Documentation

### Purpose
The `queryLocalFonts` function is designed to enhance web applications by enabling the detection of local fonts. This capability allows developers to create more personalized user experiences through font selection that aligns with the user’s environment.

### Usage
The `queryLocalFonts` function is part of the Font API in JavaScript and can be called to return a promise that resolves to an array of `FontFace` objects representing the local fonts.

### Syntax
```javascript
queryLocalFonts()
  .then((fonts) => {
    // Process the fonts array
  })
  .catch((error) => {
    // Handle errors
  });
```

### Parameters
- **None**: The function does not take any parameters.

### Return Value
- Returns a `Promise` that resolves to an array of `FontFace` objects, each representing a local font.

### Compatibility
As of October 2023, `queryLocalFonts` is supported in modern browsers, but may not be available in older versions. Always check for feature support when developing web applications.

## Examples

### Example 1: Basic Usage
```javascript
queryLocalFonts()
  .then((fonts) => {
    fonts.forEach((font) => {
      console.log(`Font Family: ${font.family}, Style: ${font.style}`);
    });
  })
  .catch((error) => {
    console.error('Error retrieving local fonts:', error);
  });
```

### Example 2: Displaying Local Fonts in a Dropdown
```html
<select id="fontSelector"></select>

<script>
  queryLocalFonts()
    .then((fonts) => {
      const fontSelector = document.getElementById('fontSelector');
      fonts.forEach((font) => {
        const option = document.createElement('option');
        option.textContent = font.family;
        fontSelector.appendChild(option);
      });
    })
    .catch((error) => {
      console.error('Error retrieving local fonts:', error);
    });
</script>
```

## Explanation

### Common Pitfalls
- **Browser Compatibility**: Not all browsers may support `queryLocalFonts`. Always check for browser compatibility and consider providing fallbacks or alternatives.
- **Promise Handling**: Ensure proper error handling in your promise chain to manage any potential issues when accessing local fonts.
- **Security Concerns**: Some privacy restrictions may limit access to certain local fonts, which can affect the results returned by the function.

### Gotchas
- The list of fonts returned may vary depending on the operating system and installed font types on the user's device.
- When using the fonts in CSS, ensure that they are loaded and available before applying styles to avoid rendering issues.

## One Line Summary
`queryLocalFonts` is a JavaScript API that retrieves a list of fonts installed locally on the user's system, enabling personalized typography in web applications.