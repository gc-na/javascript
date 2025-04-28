<!--
Meta Description: # PaymentRequest: A JavaScript API for Simplifying Online Payments ## Synopsis The `PaymentRequest` API is a JavaScript interface that simplifies the ...
Meta Keywords: payment, paymentrequest, api, shipping, paymentresponse
-->

# PaymentRequest: A JavaScript API for Simplifying Online Payments

## Synopsis
The `PaymentRequest` API is a JavaScript interface that simplifies the process of online payments by providing a standardized way to collect payment information from users, enhancing the checkout experience across web applications.

## Documentation

### Purpose
The `PaymentRequest` API aims to streamline the checkout process by allowing developers to create a consistent and secure way for users to make payments through web applications. It enhances user experience by minimizing the amount of information users need to enter manually and supports various payment methods.

### Usage
To utilize the `PaymentRequest` API, developers instantiate a `PaymentRequest` object with the necessary parameters, including payment method details, transaction details, and optional shipping options. The process typically includes the following steps:

1. **Creating a PaymentRequest Object**:
   ```javascript
   const request = new PaymentRequest(
       ['basic-card', 'paypal'], // Payment methods
       {
           country: 'US',
           currency: 'USD',
           total: {
               label: 'Total',
               amount: '50.00'
           }
       }, // Payment details
       {
           requestShipping: true // Optional shipping request
       }
   );
   ```

2. **Showing the Payment Request UI**:
   ```javascript
   request.show().then(function(paymentResponse) {
       // Handle the payment response
       console.log(paymentResponse);
       // Complete the payment process
       paymentResponse.complete('success');
   }).catch(function(err) {
       console.error('Payment request failed:', err);
   });
   ```

3. **Handling the Payment Response**:
   After the user completes the payment, the response can be processed to finalize the transaction.

### Details
- **Supported Payment Methods**: You can specify multiple payment methods, including credit cards, digital wallets, and others. The browser decides which payment methods to display based on user configuration and the specified methods.
- **Payment Details Object**: This object must include at least a total amount and label. Additional options like taxes, shipping costs, and line items can also be included for more complex transactions.
- **Shipping Address**: If `requestShipping` is set to true, the API will prompt users for their shipping address, which can be processed as needed.

## Examples

### Basic Example
Here’s a simple example of using the `PaymentRequest` API to create a payment request for a total of $50.00:

```javascript
const paymentRequest = new PaymentRequest(
    ['basic-card'], // Accepting basic credit card payments
    {
        country: 'US',
        currency: 'USD',
        total: {
            label: 'Your Purchase',
            amount: '50.00'
        }
    }
);

paymentRequest.show().then(function(paymentResponse) {
    console.log('Payment successful:', paymentResponse);
    paymentResponse.complete('success');
}).catch(function(error) {
    console.error('Payment failed:', error);
});
```

### Example with Shipping
This example includes a shipping address request:

```javascript
const paymentRequestWithShipping = new PaymentRequest(
    ['basic-card'], 
    {
        country: 'US',
        currency: 'USD',
        total: {
            label: 'Total Amount',
            amount: '75.00'
        },
        displayItems: [{
            label: 'Item Price',
            amount: '70.00'
        }, {
            label: 'Shipping',
            amount: '5.00'
        }]
    },
    {
        requestShipping: true
    }
);

paymentRequestWithShipping.show().then((paymentResponse) => {
    console.log('Shipping Address:', paymentResponse.shippingAddress);
    paymentResponse.complete('success');
}).catch((error) => {
    console.error('Error:', error);
});
```

## Explanation
### Common Pitfalls
- **Browser Support**: The `PaymentRequest` API is supported in most modern browsers, but always check compatibility as not all browsers may implement it fully.
- **Payment Method Limitations**: Ensure that the payment methods specified are supported by the user's browser and that they have the necessary payment credentials configured.
- **Handling Payment Responses**: Always handle the payment responses properly and complete the transaction to inform the browser about the success or failure of the payment.

### Additional Notes
- The `PaymentRequest` API enhances user experience by reducing friction during the payment process.
- It is important to handle user privacy and security appropriately when managing payment data.

## One Line Summary
The `PaymentRequest` API in JavaScript simplifies online payment processing by providing a standardized interface for collecting user payment information securely and efficiently.