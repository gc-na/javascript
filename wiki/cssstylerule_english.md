<!--
Meta Description: # CSSStyleRule in JavaScript: Understanding and Utilizing CSSStyleRule Interface ## Synopsis The `CSSStyleRule` interface in JavaScript represents a s...
Meta Keywords: rules, stylesheet, css, cssstylerule, rule
-->

# CSSStyleRule in JavaScript: Understanding and Utilizing CSSStyleRule Interface

## Synopsis
The `CSSStyleRule` interface in JavaScript represents a single CSS style rule, allowing developers to programmatically access and manipulate CSS properties within stylesheets.

## Documentation
### Overview
The `CSSStyleRule` interface is part of the CSS Object Model, which provides a way to interact with stylesheets in a structured manner. Each `CSSStyleRule` object corresponds to a single rule defined in a CSS stylesheet, enabling you to access its selector text and the associated style declarations.

### Purpose
The primary purpose of the `CSSStyleRule` is to allow JavaScript to read and modify CSS rules dynamically. This can be particularly useful for applications that require responsive design adjustments, theming, or real-time style changes based on user interactions.

### Usage
To utilize `CSSStyleRule`, you typically encounter it when iterating through a stylesheet's rules. You can access it via the `CSSStyleSheet` interface, which contains a list of all the rules defined in that stylesheet.

#### Properties
- **selectorText**: A string representing the selector(s) for the style rule.
- **style**: An instance of `CSSStyleDeclaration` containing the CSS properties and values.

#### Example of Accessing CSSStyleRule
```javascript
// Access the first stylesheet in the document
const stylesheet = document.styleSheets[0];

// Access the rules in the stylesheet
const rules = stylesheet.cssRules || stylesheet.rules; // For older browsers

// Example: Access the first CSS rule
if (rules.length > 0) {
    const firstRule = rules[0];
    console.log(firstRule.selectorText); // Logs the selector text
    console.log(firstRule.style.cssText); // Logs the CSS declarations
}
```

## Examples
### Modifying a CSS Rule
Here's how to modify an existing CSS rule using `CSSStyleRule`:
```javascript
const stylesheet = document.styleSheets[0];
const rules = stylesheet.cssRules;

if (rules.length > 0) {
    const firstRule = rules[0];
    // Change the color property of the first rule
    firstRule.style.color = 'blue';
}
```

### Adding a New CSS Rule
While `CSSStyleRule` itself is used for existing rules, you can add new rules by using the `insertRule` method of `CSSStyleSheet`:
```javascript
const stylesheet = document.styleSheets[0];
stylesheet.insertRule('body { background-color: lightgray; }', stylesheet.cssRules.length);
```

## Explanation
### Common Pitfalls
- **Browser Compatibility**: Be aware that browser support for the CSS Object Model can vary. Always check for the existence of properties like `cssRules` and handle cases where they may not be available.
- **Dynamic Changes**: When modifying styles through JavaScript, the changes may not take effect if the styles are overridden by more specific rules elsewhere in the stylesheet.

### Gotchas
- The `style` property of a `CSSStyleRule` reflects only the styles defined within that rule. It does not include inherited styles or styles applied via other rules.
- The `cssRules` collection is live, meaning if you modify it (e.g., by adding or removing rules), the collection will update automatically.

## One Line Summary
The `CSSStyleRule` interface in JavaScript allows developers to access and manipulate individual CSS rules within a stylesheet dynamically.