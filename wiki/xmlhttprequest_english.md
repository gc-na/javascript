<!--
Meta Description: # XMLHttpRequest: A Comprehensive Guide to Asynchronous JavaScript Requests ## Synopsis XMLHttpRequest (XHR) is a JavaScript API used to interact with...
Meta Keywords: xhr, data, request, xmlhttprequest, requests
-->

# XMLHttpRequest: A Comprehensive Guide to Asynchronous JavaScript Requests

## Synopsis
XMLHttpRequest (XHR) is a JavaScript API used to interact with servers via HTTP requests. It enables asynchronous data fetching, allowing web applications to retrieve and send data without reloading the page.

## Documentation

### Purpose
XMLHttpRequest allows developers to create dynamic web applications by enabling client-side scripts to communicate with remote servers. This is essential for tasks such as fetching data from an API, submitting forms, and updating the content of a web page without requiring a full page reload.

### Usage
To use XMLHttpRequest, you create an instance of the object, configure it with the desired HTTP method (GET, POST, etc.), specify the URL, and send the request. The response can then be processed asynchronously.

### Key Methods
- `open(method, url, async)`: Initializes a request. The `async` parameter is optional and defaults to `true`.
- `send(data)`: Sends the request. The `data` parameter is optional and is used for sending data in POST requests.
- `setRequestHeader(header, value)`: Sets the value of an HTTP request header.
- `abort()`: Aborts the request if it has already been sent.

### Properties
- `readyState`: Holds the current state of the request (0-4).
- `status`: Contains the HTTP status code of the response (e.g., 200 for success).
- `responseText`: Contains the response data as a string.

### Event Handlers
- `onreadystatechange`: A function that is called when the `readyState` changes.
- `onload`: A function that is called when the request completes successfully.
- `onerror`: A function that is called when a network error occurs.

## Examples

### Basic GET Request
```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function () {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(JSON.parse(xhr.responseText));
    }
};
xhr.send();
```

### Basic POST Request
```javascript
var xhr = new XMLHttpRequest();
xhr.open("POST", "https://api.example.com/submit", true);
xhr.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
xhr.onreadystatechange = function () {
    if (xhr.readyState === 4 && xhr.status === 201) {
        console.log("Data submitted successfully!");
    }
};
xhr.send(JSON.stringify({ name: "John Doe", age: 30 }));
```

## Explanation

### Common Pitfalls
1. **CORS Issues**: Be aware of Cross-Origin Resource Sharing (CORS) policies when making requests to different domains. Ensure the server supports CORS to avoid blocking requests.
2. **Asynchronous Behavior**: The `send()` method is asynchronous by default. Ensure that your code handles the asynchronous nature properly, especially when relying on the response data.
3. **Error Handling**: Always implement error handling using `onerror` or check the `status` property to manage failed requests.

### Additional Notes
- The `XMLHttpRequest` API is widely supported across all major browsers, but the Fetch API is becoming the preferred method for making HTTP requests due to its simpler syntax and better promise support.
- Consider using libraries like Axios or jQuery's AJAX methods for more complex scenarios or to simplify your code.

## One Line Summary
XMLHttpRequest is a JavaScript API that enables asynchronous communication with servers, allowing web applications to fetch and send data without reloading the page.