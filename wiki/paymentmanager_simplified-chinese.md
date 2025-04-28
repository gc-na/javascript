<!--
Meta Description: # PaymentManager：JavaScript中的支付管理器 ## 概述 PaymentManager 是一个用于处理在线支付的 JavaScript 组件。它简化了支付流程，通过与各种支付服务提供商的集成，使开发者能够快速实现安全的支付功能。 ## 文档 ### 目的 PaymentMan...
Meta Keywords: paymentmanager, error, javascript, paypal, response
-->

# PaymentManager：JavaScript中的支付管理器

## 概述
PaymentManager 是一个用于处理在线支付的 JavaScript 组件。它简化了支付流程，通过与各种支付服务提供商的集成，使开发者能够快速实现安全的支付功能。

## 文档
### 目的
PaymentManager 的主要目的是提供一个统一的接口来处理不同支付服务的集成，减少开发者在支付流程中的复杂性。

### 用法
在JavaScript中，使用 PaymentManager 进行支付处理的基本步骤如下：

1. **初始化 PaymentManager**：
   ```javascript
   const paymentManager = new PaymentManager();
   ```

2. **设置支付服务**：
   配置所需的支付服务提供商，例如 PayPal、Stripe 等。
   ```javascript
   paymentManager.addProvider('PayPal', {
       clientId: 'YOUR_CLIENT_ID',
       secret: 'YOUR_SECRET'
   });
   ```

3. **发起支付请求**：
   ```javascript
   paymentManager.processPayment({
       provider: 'PayPal',
       amount: 100,
       currency: 'USD'
   }).then(response => {
       console.log('Payment Successful:', response);
   }).catch(error => {
       console.error('Payment Failed:', error);
   });
   ```

### 详细信息
- **构造函数**：`PaymentManager` 的构造函数用于创建支付管理器实例。
- **addProvider(providerName, config)**：添加支付服务提供商及其配置信息。
- **processPayment(paymentInfo)**：处理支付请求并返回一个 Promise，成功时返回支付结果，失败时返回错误信息。

## 示例
### 示例 1：使用 PayPal 进行支付
```javascript
const paymentManager = new PaymentManager();
paymentManager.addProvider('PayPal', {
    clientId: 'YOUR_CLIENT_ID',
    secret: 'YOUR_SECRET'
});

paymentManager.processPayment({
    provider: 'PayPal',
    amount: 50,
    currency: 'USD'
}).then(response => {
    console.log('支付成功:', response);
}).catch(error => {
    console.error('支付失败:', error);
});
```

### 示例 2：使用 Stripe 进行支付
```javascript
const paymentManager = new PaymentManager();
paymentManager.addProvider('Stripe', {
    apiKey: 'YOUR_API_KEY'
});

paymentManager.processPayment({
    provider: 'Stripe',
    amount: 75,
    currency: 'USD'
}).then(response => {
    console.log('支付成功:', response);
}).catch(error => {
    console.error('支付失败:', error);
});
```

## 说明
- **常见问题**：确保在调用 `processPayment` 方法之前已经正确设置支付服务提供商的配置。未正确配置可能导致支付请求失败。
- **错误处理**：在 `catch` 块中处理错误是非常重要的，确保用户能够收到反馈。
- **安全性**：不要在前端代码中暴露敏感信息，例如 API 密钥或客户端密钥。

## 一句话总结
PaymentManager 是一个用于简化 JavaScript 中在线支付处理的强大工具。