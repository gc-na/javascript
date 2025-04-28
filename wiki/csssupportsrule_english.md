<!--
Meta Description: # Understanding CSSSupportsRule in JavaScript: A Comprehensive Guide ## Synopsis The `CSSSupportsRule` interface in JavaScript provides a way to work ...
Meta Keywords: csssupportsrule, css, supports, javascript, rule
-->

# Understanding CSSSupportsRule in JavaScript: A Comprehensive Guide

## Synopsis
The `CSSSupportsRule` interface in JavaScript provides a way to work with CSS feature queries, enabling developers to conditionally apply styles based on browser support for specific CSS features.

## Documentation

### Purpose
`CSSSupportsRule` allows developers to utilize the CSS `@supports` rule within JavaScript, enabling dynamic styling based on the capabilities of the user’s browser. This is particularly useful for progressive enhancement, ensuring that users with modern browsers can take advantage of advanced CSS features without affecting users with older or less capable browsers.

### Usage
`CSSSupportsRule` is part of the CSS Object Model (CSSOM) and can be used to create, modify, or read `@supports` rules programmatically. The `CSSSupportsRule` is used in conjunction with the `CSSRule` interface and represents a conditional group of CSS rules that apply only if the specified feature is supported.

#### Syntax
To create a `CSSSupportsRule`, you can use the `CSS.supports` method:

```javascript
let supports = CSS.supports("property: value");
```

### Properties
- **conditionText**: A string representing the condition used in the `@supports` rule.
- **cssRules**: A read-only list of CSS rules contained within the `@supports` block.

### Methods
- **insertRule()**: Inserts a new rule into the `CSSSupportsRule`.
- **deleteRule()**: Deletes a rule from the `CSSSupportsRule`.

## Examples

### Example 1: Creating a CSSSupportsRule

```javascript
let supportsRule = new CSSSupportsRule("display: grid", [
    new CSSStyleRule("color: blue;"),
    new CSSStyleRule("background: yellow;")
]);

console.log(supportsRule.conditionText); // Output: "display: grid"
```

### Example 2: Checking Browser Support

```javascript
if (CSS.supports("display: grid")) {
    document.body.classList.add("grid-support");
} else {
    document.body.classList.add("no-grid-support");
}
```

### Example 3: Inserting a Rule

```javascript
let styleSheet = document.styleSheets[0];
let rule = "@supports (display: flex) { .flex-container { display: flex; } }";
styleSheet.insertRule(rule, styleSheet.cssRules.length);
```

## Explanation

### Common Pitfalls
1. **Browser Compatibility**: Not all browsers support the `CSSSupportsRule` interface. Always check compatibility before using it.
2. **CSS Syntax Errors**: When creating `CSSSupportsRule` or inserting rules, ensure that the syntax is valid to avoid runtime errors.
3. **Dynamic Stylesheets**: Changes in JavaScript may not reflect if the stylesheet is cached. Consider clearing cache or checking the updated styles in DevTools.

### Gotchas
- `CSSSupportsRule` is read-only once created; modifications to the condition or rules must be done through methods like `insertRule` and `deleteRule`.
- The `@supports` condition is evaluated at runtime, which may lead to unexpected behavior if the CSS condition changes after the rules are applied.

## One Line Summary
`CSSSupportsRule` in JavaScript allows developers to dynamically manage CSS rules based on browser feature support, enhancing the styling experience for end-users.