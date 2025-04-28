<!--
Meta Description: # Understanding ValidityState in JavaScript: A Comprehensive Guide ## Synopsis ValidityState is an interface in JavaScript that provides properties to...
Meta Keywords: form, input, validity, value, validitystate
-->

# Understanding ValidityState in JavaScript: A Comprehensive Guide

## Synopsis
ValidityState is an interface in JavaScript that provides properties to determine the validity of form input elements. This feature is crucial for validating user input and enhancing user experience on web applications.

## Documentation

### Purpose
The ValidityState interface is part of the HTML DOM and is used to assess the validity of a form input element, such as `<input>`, `<textarea>`, or `<select>`. It contains properties that reflect the state of the input element's validity based on various constraints defined in the HTML specification, such as `required`, `pattern`, `min`, `max`, and custom validation rules.

### Usage
To access the ValidityState of an input element, you can use the `validity` property of the input element. The `validity` property returns an instance of the ValidityState interface, which includes boolean properties indicating the validity of the element.

### Properties
Some key properties of the ValidityState interface include:

- **valid**: A boolean indicating if the element is valid.
- **valueMissing**: True if the element is required but has no value.
- **typeMismatch**: True if the element's value does not match the expected type.
- **patternMismatch**: True if the element's value does not match the specified pattern.
- **tooLong**: True if the value is longer than the maximum allowed length.
- **tooShort**: True if the value is shorter than the minimum required length.
- **rangeUnderflow**: True if the value is less than the minimum specified value.
- **rangeOverflow**: True if the value is greater than the maximum specified value.
- **stepMismatch**: True if the value does not conform to the step attribute.

## Examples

### Example 1: Basic Usage
```html
<form id="myForm">
    <input type="text" id="myInput" required>
    <button type="submit">Submit</button>
</form>

<script>
    const input = document.getElementById('myInput');
    const form = document.getElementById('myForm');

    form.addEventListener('submit', function(event) {
        if (input.validity.valueMissing) {
            alert('This field is required.');
            event.preventDefault(); // Prevent form submission
        }
    });
</script>
```

### Example 2: Check for Pattern Mismatch
```html
<form id="myForm">
    <input type="text" id="emailInput" pattern="^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$" required>
    <button type="submit">Submit</button>
</form>

<script>
    const emailInput = document.getElementById('emailInput');
    const form = document.getElementById('myForm');

    form.addEventListener('submit', function(event) {
        if (emailInput.validity.patternMismatch) {
            alert('Please enter a valid email address.');
            event.preventDefault(); // Prevent form submission
        }
    });
</script>
```

## Explanation
When using the ValidityState interface, it is important to remember the following:

- The validity state is evaluated based on HTML attributes. Ensure that your elements have the necessary attributes defined (e.g., `required`, `minlength`, `maxlength`, `pattern`).
- Custom validation logic may require combining the ValidityState properties with additional JavaScript checks.
- The `validity` property is only available on input elements; it does not apply to other DOM elements.
- When implementing form validation, always provide user-friendly messages to enhance the user experience.

## One Line Summary
ValidityState is a JavaScript interface that offers properties for assessing the validity of form input elements, facilitating user input validation in web applications.