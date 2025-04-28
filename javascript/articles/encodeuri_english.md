<!--
Meta Description: # Understanding `encodeURI` in JavaScript: A Comprehensive Guide ## Synopsis The `encodeURI` function in JavaScript is essential for encoding Uniform ...
Meta Keywords: uri, encodeuri, characters, javascript, encoding
-->

# Understanding `encodeURI` in JavaScript: A Comprehensive Guide

## Synopsis
The `encodeURI` function in JavaScript is essential for encoding Uniform Resource Identifiers (URIs) by converting characters into a format that can be transmitted over the Internet without confusion or errors.

## Documentation

### Purpose
The `encodeURI` function is used to encode a URI by replacing each instance of certain characters with one or more escape sequences representing the UTF-8 encoding of the character. This ensures that the URI is valid and can be safely transmitted over HTTP.

### Usage
The syntax for `encodeURI` is as follows:

```javascript
encodeURI(uri);
```

- **Parameters**: 
  - `uri`: A string representing the URI that you want to encode.
  
- **Returns**: 
  - A new string representing the encoded URI.

### Details
`encodeURI` is particularly useful for encoding URIs that may contain special characters, such as spaces, punctuation, or other symbols that have special meanings in a URI context. It preserves characters that have specific meanings in URIs (like `:`, `/`, `?`, `&`, and `=`), ensuring that the structure and semantics of the URI remain intact.

## Examples

### Basic Usage
1. **Encoding a Simple URI**
   ```javascript
   const uri = "https://example.com/search?q=Hello World!";
   const encodedURI = encodeURI(uri);
   console.log(encodedURI); // Output: "https://example.com/search?q=Hello%20World!"
   ```

2. **Encoding a URI with Special Characters**
   ```javascript
   const uri = "https://example.com/path/to/file?name=John Doe&age=30";
   const encodedURI = encodeURI(uri);
   console.log(encodedURI); // Output: "https://example.com/path/to/file?name=John%20Doe&age=30"
   ```

3. **Using with URL parameters**
   ```javascript
   const baseURL = "https://example.com/api";
   const params = "search=JavaScript & encoding";
   const fullURL = `${baseURL}?${encodeURI(params)}`;
   console.log(fullURL); // Output: "https://example.com/api?search=JavaScript%20%26%20encoding"
   ```

## Explanation
### Common Pitfalls
- **Using `encodeURI` vs `encodeURIComponent`**: It's important to differentiate between `encodeURI` and `encodeURIComponent`. While `encodeURI` is used for entire URIs, `encodeURIComponent` is intended for encoding individual URI components (such as query strings). `encodeURIComponent` encodes all characters, including those that have special meanings in a URI.

- **Over-encoding**: Sometimes developers may mistakenly call `encodeURI` multiple times on the same string, leading to double encoding. This can result in incorrect URIs.

### Additional Notes
- `encodeURI` does not encode characters like `#`, `?`, `&`, and `=` because these characters are integral to the structure of a URI. If you need to encode these characters, consider using `encodeURIComponent`.

## One Line Summary
`encodeURI` is a JavaScript function that encodes a URI by converting special characters into a valid format for transmission over the web.