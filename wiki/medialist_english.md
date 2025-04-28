<!--
Meta Description: # Understanding MediaList in JavaScript: Managing CSS Media Queries ## Synopsis The `MediaList` interface in JavaScript provides a way to manipulate a...
Meta Keywords: media, medialist, stylesheet, queries, stylesheets
-->

# Understanding MediaList in JavaScript: Managing CSS Media Queries

## Synopsis
The `MediaList` interface in JavaScript provides a way to manipulate and access a list of media queries associated with a stylesheet, enabling developers to dynamically manage styles based on media conditions.

## Documentation
The `MediaList` interface is part of the CSS Object Model (CSSOM) and is primarily used to manage the media types and conditions for stylesheets linked to documents. Each `MediaList` object contains a collection of media queries that determine when a stylesheet should be applied, based on the current viewport or device characteristics.

### Purpose
The primary purpose of the `MediaList` interface is to allow developers to interact programmatically with the media queries of a stylesheet. This is particularly useful in responsive web design, where styles need to adapt according to the device's characteristics (e.g., screen width, resolution).

### Usage
To access the `MediaList`, you typically retrieve it from a stylesheet object. Here's how you can interact with it:

1. **Accessing MediaList**: You can obtain the `MediaList` from a stylesheet using the `media` property.
   
   ```javascript
   const stylesheets = document.styleSheets; // Retrieve all stylesheets
   const mediaList = stylesheets[0].media; // Access the media list of the first stylesheet
   ```

2. **Reading Media Queries**: You can read the individual media queries using the `mediaText` property.

   ```javascript
   const mediaText = mediaList.mediaText; // Get the media query text
   ```

3. **Modifying Media Queries**: You can modify the media queries by using methods like `appendMedium()` and `deleteMedium()`.
   
   ```javascript
   mediaList.appendMedium("screen and (max-width: 600px)"); // Add a media query
   mediaList.deleteMedium("screen"); // Remove a media query
   ```

### Methods
- **appendMedium(medium)**: Adds a new media query to the list.
- **deleteMedium(medium)**: Removes a specific media query from the list.

### Properties
- **mediaText**: A string representing the media query text.

## Examples
### Example 1: Accessing MediaList
```javascript
const styleSheet = document.styleSheets[0]; // Get the first stylesheet
const mediaList = styleSheet.media; // Access its MediaList
console.log(mediaList.mediaText); // Output the media query text
```

### Example 2: Modifying MediaList
```javascript
const styleSheet = document.styleSheets[0];
const mediaList = styleSheet.media;

// Add a new media query
mediaList.appendMedium("screen and (min-width: 800px)");

// Remove an existing media query
mediaList.deleteMedium("screen");
```

## Explanation
### Common Pitfalls
- **Cross-Origin Stylesheets**: If the stylesheet is loaded from a different origin and does not have the appropriate CORS settings, accessing its `media` property may throw a security error.
  
- **Browser Compatibility**: While modern browsers support the `MediaList` interface, some older browsers may not fully implement all its features. Always check compatibility if you intend to support a wide range of browsers.

- **Synchronous Updates**: Changes to the `MediaList` may not be reflected immediately in the rendered styles, especially if multiple scripts are modifying styles concurrently.

### Additional Notes
- The `MediaList` is read-only for certain properties depending on the stylesheet's origin and mode.
- Ensure to manage media queries carefully to prevent conflicts, especially in highly dynamic applications.

## One Line Summary
The `MediaList` interface in JavaScript allows developers to programmatically manage media queries associated with stylesheets, enabling responsive design adjustments.