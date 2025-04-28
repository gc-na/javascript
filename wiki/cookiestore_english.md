<!--
Meta Description: # CookieStore: Managing Cookies in JavaScript ## Synopsis `CookieStore` is a JavaScript API that provides a simple and efficient way to access and man...
Meta Keywords: cookie, cookies, cookiestore, error, promise
-->

# CookieStore: Managing Cookies in JavaScript

## Synopsis
`CookieStore` is a JavaScript API that provides a simple and efficient way to access and manipulate cookies within the browser. It allows developers to read, write, and delete cookies using a modern promise-based interface.

## Documentation
### Purpose
The `CookieStore` API is designed to streamline cookie management in web applications. It enhances the functionality of traditional cookie handling and improves security by providing a standardized way to interact with cookies.

### Usage
The `CookieStore` API is accessed via the `window.cookieStore` object:

- **Reading Cookies**: Use the `get()` method to retrieve specific cookies.
- **Writing Cookies**: Use the `set()` method to create or update cookies.
- **Deleting Cookies**: Use the `delete()` method to remove cookies.

### Methods
1. **`cookieStore.get(name: string): Promise<Cookie>`**
   - Retrieves a cookie by its name.
   - Returns a promise that resolves to a `Cookie` object or `undefined` if the cookie does not exist.

2. **`cookieStore.set(cookie: Cookie): Promise<void>`**
   - Sets a cookie with the specified attributes.
   - Returns a promise that resolves once the operation is complete.

3. **`cookieStore.delete(name: string): Promise<void>`**
   - Deletes a cookie by its name.
   - Returns a promise that resolves once the operation is complete.

### Cookie Object Structure
A cookie object typically includes:
- `name`: The name of the cookie.
- `value`: The value of the cookie.
- `expires`: The expiration date of the cookie (optional).
- `path`: The path within the site the cookie is valid for (optional).
- `domain`: The domain the cookie is associated with (optional).
- `secure`: A boolean indicating if the cookie should only be transmitted over secure protocols (optional).
- `httpOnly`: A boolean indicating if the cookie is accessible only via HTTP(S) (optional).

## Examples
### Basic Usage Example: Set a Cookie
```javascript
const cookie = {
    name: "user",
    value: "JohnDoe",
    expires: new Date(Date.now() + 86400e3), // Expires in 1 day
    path: "/",
};

cookieStore.set(cookie).then(() => {
    console.log("Cookie set successfully!");
}).catch(error => {
    console.error("Error setting cookie:", error);
});
```

### Basic Usage Example: Get a Cookie
```javascript
cookieStore.get("user").then(cookie => {
    if (cookie) {
        console.log(`Cookie value: ${cookie.value}`);
    } else {
        console.log("Cookie not found.");
    }
}).catch(error => {
    console.error("Error retrieving cookie:", error);
});
```

### Basic Usage Example: Delete a Cookie
```javascript
cookieStore.delete("user").then(() => {
    console.log("Cookie deleted successfully!");
}).catch(error => {
    console.error("Error deleting cookie:", error);
});
```

## Explanation
### Common Pitfalls
- **Browser Support**: The `CookieStore` API may not be supported in all browsers. Ensure to check compatibility before using it in production.
- **Secure Cookies**: If a cookie is set with the `secure` attribute, it will only be transmitted over HTTPS, which can lead to unexpected behavior in development environments running on HTTP.
- **Promise Handling**: As the API is promise-based, failing to handle promises correctly may result in unhandled rejections. Always use `.then()` and `.catch()` to manage outcomes.

### Additional Notes
- Cookies set with `httpOnly` cannot be accessed via JavaScript, providing an additional layer of security against XSS attacks.
- The `expires` attribute is crucial for managing cookie lifetime; cookies without an expiration date will be treated as session cookies and deleted when the browser is closed.

## One Line Summary
The `CookieStore` API in JavaScript simplifies cookie management by providing a promise-based interface for reading, writing, and deleting cookies.