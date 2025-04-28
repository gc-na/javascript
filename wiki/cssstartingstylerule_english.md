<!--
Meta Description: # Understanding CSSStyleRule in JavaScript: A Comprehensive Guide ## Synopsis CSSStyleRule is a JavaScript interface that represents a single CSS styl...
Meta Keywords: rule, stylesheet, cssstylerule, stylesheets, javascript
-->

# Understanding CSSStyleRule in JavaScript: A Comprehensive Guide

## Synopsis
CSSStyleRule is a JavaScript interface that represents a single CSS style rule within a CSS stylesheet. It provides a way to manipulate styles programmatically, allowing developers to dynamically change the appearance of web pages.

## Documentation

### What is CSSStyleRule?
CSSStyleRule is part of the CSS Object Model (CSSOM) and provides an interface for accessing and modifying styles defined in CSS rules. It is commonly used when working with stylesheets through the Document Object Model (DOM) in JavaScript.

### Purpose
The primary purpose of CSSStyleRule is to allow developers to read and modify CSS rules directly from JavaScript. This can be particularly useful for creating dynamic styles based on user interactions or application states.

### Usage
To use CSSStyleRule, you typically access it via the stylesheets of a document. Each stylesheet can contain multiple rules, and each rule can be an instance of CSSStyleRule. You can retrieve it using the `cssRules` property of a stylesheet.

### Key Properties and Methods
- **selectorText**: A string representing the selector for the rule.
- **style**: A CSSStyleDeclaration object representing the style properties of the rule.
- **cssText**: A string representing the entire CSS rule, which can be modified.
- **deleteRule()**: A method to remove the rule from the stylesheet.
- **insertRule()**: A method to add a new rule to the stylesheet.

## Examples

### Example 1: Accessing a CSSStyleRule
```javascript
// Access the first stylesheet
let stylesheet = document.styleSheets[0];

// Access the first rule in the stylesheet
let rule = stylesheet.cssRules[0];

// Log the selector text and styles
console.log(rule.selectorText); // e.g., ".example-class"
console.log(rule.style.cssText); // e.g., "color: red; font-size: 14px;"
```

### Example 2: Modifying a CSSStyleRule
```javascript
// Access the stylesheet and rule
let stylesheet = document.styleSheets[0];
let rule = stylesheet.cssRules[0];

// Change the color property of the rule
rule.style.color = 'blue';

// Log the updated cssText
console.log(rule.cssText); // e.g., ".example-class { color: blue; font-size: 14px; }"
```

### Example 3: Deleting a CSSStyleRule
```javascript
// Access the stylesheet
let stylesheet = document.styleSheets[0];

// Remove the first rule from the stylesheet
stylesheet.deleteRule(0);

// Confirm deletion
console.log(stylesheet.cssRules.length); // Should be one less than before
```

## Explanation
While working with CSSStyleRule, developers should be aware of certain pitfalls:
- **Cross-Origin Stylesheets**: Accessing stylesheets from different origins may lead to security errors due to the Same-Origin Policy. Ensure stylesheets are from the same origin or properly configured with CORS.
- **Browser Compatibility**: Not all browsers may support all CSS properties or methods. Always check for compatibility in older browsers if targeting a wide audience.
- **Dynamic Changes**: Modifications to CSSStyleRule will not affect elements that have styles applied inline or through higher specificity rules.

## One Line Summary
CSSStyleRule allows JavaScript developers to access and manipulate CSS rules within stylesheets, enabling dynamic styling of web pages.