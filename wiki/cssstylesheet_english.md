<!--
Meta Description: # CSSStyleSheet in JavaScript: Manipulating Stylesheets Programmatically ## Synopsis The `CSSStyleSheet` interface in JavaScript allows developers to ...
Meta Keywords: stylesheets, stylesheet, cssstylesheet, document, sheet
-->

# CSSStyleSheet in JavaScript: Manipulating Stylesheets Programmatically

## Synopsis
The `CSSStyleSheet` interface in JavaScript allows developers to programmatically interact with and manipulate stylesheets, enabling dynamic styling of web pages.

## Documentation
The `CSSStyleSheet` interface represents a single stylesheet, which can be linked via a `<link>` tag or embedded in a `<style>` tag within an HTML document. This interface provides properties and methods to access and modify the styles defined in the stylesheet.

### Purpose
The primary purpose of `CSSStyleSheet` is to provide a way to manipulate CSS rules and styles through JavaScript. This capability allows for dynamic changes to the presentation of a webpage based on user interactions or other conditions.

### Usage
You can access a `CSSStyleSheet` using the `document.styleSheets` property, which returns a list of all stylesheets associated with the document. The `CSSStyleSheet` interface exposes properties such as `cssRules`, `insertRule()`, and `deleteRule()` to manage CSS rules.

### Properties and Methods
- **cssRules**: Returns a list of all CSS rules in the stylesheet.
- **insertRule(rule, index)**: Inserts a new CSS rule at the specified index.
- **deleteRule(index)**: Deletes a CSS rule at the specified index.
- **href**: The URL of the stylesheet.
- **media**: Represents the media type of the stylesheet, such as 'screen' or 'print'.

## Examples
### Accessing Stylesheets
```javascript
const stylesheets = document.styleSheets;
console.log(stylesheets.length); // Logs the number of stylesheets
```

### Inserting a New CSS Rule
```javascript
const sheet = document.styleSheets[0]; // Access the first stylesheet
sheet.insertRule('body { background-color: lightblue; }', sheet.cssRules.length);
```

### Deleting a CSS Rule
```javascript
const sheet = document.styleSheets[0]; // Access the first stylesheet
if (sheet.cssRules.length > 0) {
    sheet.deleteRule(0); // Deletes the first rule
}
```

### Modifying Existing Rules
```javascript
const sheet = document.styleSheets[0]; // Access the first stylesheet
if (sheet.cssRules.length > 0) {
    sheet.cssRules[0].style.color = 'red'; // Change the color of the first rule
}
```

## Explanation
While working with `CSSStyleSheet`, there are a few common pitfalls to be aware of:

- **Cross-Origin Restrictions**: If a stylesheet is loaded from a different origin, modifying its rules may be restricted due to CORS (Cross-Origin Resource Sharing) policies. Ensure that the stylesheet is served with appropriate headers if you need to manipulate it.
- **Dynamic Stylesheets**: Newly created stylesheets may not immediately reflect in the `document.styleSheets` collection until they are appended to the document.
- **Browser Compatibility**: Always check for compatibility, as some older browsers may not support all methods or properties of the `CSSStyleSheet` interface.

## One Line Summary
The `CSSStyleSheet` interface in JavaScript provides a powerful way to dynamically manipulate CSS rules and stylesheets within a webpage.