<!--
Meta Description: # Understanding `encodeURIComponent`: A JavaScript Essential for URL Encoding ## Synopsis `encodeURIComponent` is a built-in JavaScript function that ...
Meta Keywords: characters, encodeuricomponent, javascript, url, encoding
-->

# Understanding `encodeURIComponent`: A JavaScript Essential for URL Encoding

## Synopsis
`encodeURIComponent` is a built-in JavaScript function that encodes a Uniform Resource Identifier (URI) component by replacing each instance of certain characters with one or more escape sequences representing the UTF-8 encoding of the character.

## Documentation

### Purpose
The primary purpose of `encodeURIComponent` is to ensure that URI components are properly encoded before being transmitted over the internet. This is crucial for maintaining the integrity of the data being sent, as certain characters (like spaces, slashes, and question marks) have special meanings in URLs.

### Usage
The `encodeURIComponent` function can be called as follows:

```javascript
encodeURIComponent(uriComponent)
```

- **Parameters**: 
  - `uriComponent`: A string representing the URI component to be encoded.
  
- **Returns**: 
  - A new string representing the encoded URI component.

### Details
- `encodeURIComponent` encodes characters that are not valid in a URI component, including:
  - Reserved characters: `! * ' ( )`
  - Unsafe characters: `; : @ & = + $ , / ? #`
  - Control characters and non-ASCII characters.
  
- The function does not encode characters that are valid within a URI component, such as:
  - Alphabetic characters: `A-Z`, `a-z`
  - Numeric characters: `0-9`
  - Special characters: `- _ . ~`

## Examples

### Basic Usage
```javascript
const originalString = "Hello World!";
const encodedString = encodeURIComponent(originalString);
console.log(encodedString); // Outputs: Hello%20World%21
```

### Encoding Special Characters
```javascript
const specialChars = "This & that? Start=10&End=20";
const encodedSpecialChars = encodeURIComponent(specialChars);
console.log(encodedSpecialChars); // Outputs: This%20%26%20that%3F%20Start%3D10%26End%3D20
```

### Encoding a URL Component
```javascript
const url = "https://example.com/search?query=JavaScript & coding";
const encodedUrl = encodeURIComponent(url);
console.log(encodedUrl); // Outputs: https%3A%2F%2Fexample.com%2Fsearch%3Fquery%3DJavaScript%20%26%20coding
```

## Explanation

### Common Pitfalls
- **Not Encoding Entire URLs**: `encodeURIComponent` is meant for encoding individual components of a URL, such as query parameters. If you try to encode an entire URL, you may inadvertently encode characters that should remain intact, such as `:` and `/`.
  
- **Double Encoding**: If you call `encodeURIComponent` on an already encoded string, you will end up with double-encoded values, making the URI unusable. Always ensure that you encode only raw strings.

### Additional Notes
- For encoding entire URLs, consider using `encodeURI`, which is designed for that purpose. It encodes a URL while preserving certain characters that are necessary for the URL structure.
  
- Always test your encoded outputs to ensure they function correctly within your application context.

## One Line Summary
`encodeURIComponent` is a JavaScript function that encodes URI components by converting special characters into their UTF-8 encoded form, ensuring safe transmission over the internet.