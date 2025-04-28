<!--
Meta Description: # decodeURI in JavaScript: A Comprehensive Guide ## Synopsis The `decodeURI` function in JavaScript is used to decode Uniform Resource Identifiers (UR...
Meta Keywords: decodeuri, uri, javascript, encoded, characters
-->

# decodeURI in JavaScript: A Comprehensive Guide

## Synopsis
The `decodeURI` function in JavaScript is used to decode Uniform Resource Identifiers (URIs) that have been encoded using the `encodeURI` function, allowing developers to retrieve the original string from its encoded format.

## Documentation
### Purpose
`decodeURI` is a built-in JavaScript function that decodes a URI previously encoded by `encodeURI`. It converts percent-encoded characters back to their original representation, making it easier to work with URIs in a readable format.

### Usage
The syntax for `decodeURI` is as follows:

```javascript
decodeURI(encodedURI);
```

- **encodedURI**: A string representing the encoded URI that you want to decode.

### Details
- `decodeURI` does **not** decode characters that have special meanings in URIs, such as `#`, `?`, `&`, and `=`. These characters are preserved to maintain the structure of the URI.
- If the input string is not a valid encoded URI, `decodeURI` will throw a `URIError`.
- This function is commonly used in web applications where URIs are passed through URLs and need to be converted back to their standard form for processing or display.

## Examples
### Basic Usage
1. **Decoding a Simple URI:**

```javascript
const encodedURI = 'https%3A%2F%2Fexample.com%2Fpage%3Fid%3D10';
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // Output: https://example.com/page?id=10
```

2. **Decoding a URI with Special Characters:**

```javascript
const encodedURI = 'hello%20world%21%20%40JavaScript';
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // Output: hello world! @JavaScript
```

3. **Handling Invalid Encoded URIs:**

```javascript
try {
    const invalidURI = 'https%3A%2F%2Fexample.com%2Fpage%3Did%3D10%20%zz';
    const result = decodeURI(invalidURI);
} catch (e) {
    console.error(e.message); // Output: URI malformed
}
```

## Explanation
### Common Pitfalls
- **URI Malformation**: If the encoded URI is not properly formatted, `decodeURI` will throw a `URIError`. Developers should validate URIs before attempting to decode them.
- **Preserved Special Characters**: Remember that certain characters will not be decoded, which can lead to confusion if you expect those characters to be interpreted differently.

### Additional Notes
- Use `decodeURIComponent` instead if you need to decode individual components of a URI, as it handles a wider range of characters (including `#`, `?`, etc.).
- When working with user-generated input, always ensure that URIs are sanitized to prevent injection attacks or malformed requests.

## One Line Summary
The `decodeURI` function in JavaScript decodes an encoded URI, returning it to its original format while preserving certain special characters.