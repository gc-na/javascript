<!--
Meta Description: # Trusted Types in JavaScript: Enhancing Security Against Cross-Site Scripting (XSS) ## Synopsis Trusted Types is a security feature in JavaScript des...
Meta Keywords: trusted, types, policy, input, script
-->

# Trusted Types in JavaScript: Enhancing Security Against Cross-Site Scripting (XSS)

## Synopsis
Trusted Types is a security feature in JavaScript designed to mitigate Cross-Site Scripting (XSS) vulnerabilities by enforcing a policy that restricts the creation of potentially dangerous strings, particularly those used in DOM manipulation.

## Documentation
### Purpose
Trusted Types provides a way to prevent XSS attacks by enabling developers to specify how and where potentially unsafe strings can be used within their applications. It introduces a mechanism for creating "trusted" values that can be safely used in APIs that manipulate the DOM, such as `innerHTML` or `document.write`.

### Usage
To use Trusted Types, developers need to implement a policy that defines how to create trusted types. The following steps outline the usage:

1. **Defining a Policy**: Create a Trusted Types policy using `TrustedTypes.createPolicy()`. This policy will define how to handle untrusted inputs and convert them into trusted types.

   ```javascript
   const policy = TrustedTypes.createPolicy('default', {
       createHTML: (input) => {
           // Sanitize input to ensure it's safe
           return input; // Return trusted HTML
       },
       createScriptURL: (input) => {
           // Validate input for script URLs
           return input; // Return trusted script URL
       }
   });
   ```

2. **Using Trusted Types**: Once a policy is created, use it to generate trusted values. For example, use the `createHTML` method to produce trusted HTML content.

   ```javascript
   const safeHTML = policy.createHTML('<p>Hello, World!</p>');
   document.body.innerHTML = safeHTML; // Safe to use
   ```

### Details
- Trusted Types is supported in modern browsers, but it's essential to check compatibility for specific versions.
- If the `TrustedTypes` feature is not enabled in a browser, any attempt to create or use a trusted type will throw a `TypeError`.
- Developers can set the `trusted-types` attribute in the `Content Security Policy (CSP)` header to enforce the use of Trusted Types.

## Examples
### Basic Example of Trusted Types
```javascript
// Create a Trusted Types policy
const policy = TrustedTypes.createPolicy('examplePolicy', {
    createHTML: (input) => {
        // Only allow certain tags
        return input.replace(/<\/?script.*?>/g, ''); // Simple sanitization
    }
});

// Use the policy to create trusted HTML
const trustedHTML = policy.createHTML('<div>Hello, World!</div>');
document.body.innerHTML = trustedHTML; // Safe insertion
```

### Using Trusted Types with Script URLs
```javascript
// Create a Trusted Types policy for script URLs
const scriptPolicy = TrustedTypes.createPolicy('scriptPolicy', {
    createScriptURL: (input) => {
        // Basic validation for script URLs
        if (input.startsWith('https://')) {
            return input; // Allow only secure URLs
        }
        throw new Error('Invalid script URL');
    }
});

// Use the policy to create a trusted script URL
const trustedScriptURL = scriptPolicy.createScriptURL('https://example.com/my-script.js');
const scriptElement = document.createElement('script');
scriptElement.src = trustedScriptURL;
document.head.appendChild(scriptElement); // Safe to append
```

## Explanation
While Trusted Types significantly enhance security, developers must be cautious when defining policies. Some common pitfalls include:

- **Overly Permissive Policies**: Avoid creating policies that allow too much flexibility, as this can lead to security vulnerabilities.
- **Not Validating Input**: Always validate and sanitize input before trusting it, even within a policy.
- **Browser Compatibility**: Ensure to check browser support for Trusted Types, as older browsers may not support this feature.

## One Line Summary
Trusted Types in JavaScript is a security feature that helps prevent XSS vulnerabilities by enforcing strict policies for creating trusted strings used in DOM manipulations.