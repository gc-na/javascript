<!--
Meta Description: # PaymentRequest：JavaScript 的支付請求 API ## 簡介 `PaymentRequest` 是一個用於處理網頁支付的 JavaScript API，旨在提供一個統一的方式來收集用戶的支付信息，簡化線上購物過程。此 API 支援各種支付方式，包括信用卡、數字錢包等，並能提...
Meta Keywords: paymentrequest, api, methoddata, details, javascript
-->

# PaymentRequest：JavaScript 的支付請求 API

## 簡介
`PaymentRequest` 是一個用於處理網頁支付的 JavaScript API，旨在提供一個統一的方式來收集用戶的支付信息，簡化線上購物過程。此 API 支援各種支付方式，包括信用卡、數字錢包等，並能提升用戶體驗，減少購物車放棄率。

## 文件說明
### 目的
`PaymentRequest` 的主要目的是讓開發者可以輕鬆地創建和管理支付請求，從而簡化用戶在網站上的支付流程。

### 使用方法
要使用 `PaymentRequest`，開發者需創建一個新的 `PaymentRequest` 實例，並提供必要的參數，例如可用的支付方式、商品信息等。然後，通過調用 `.show()` 方法來顯示支付對話框，並處理用戶的支付選擇。

### 詳細說明
以下是 `PaymentRequest` 的主要構造函數和方法：

- **構造函數**：`PaymentRequest(methodData, details, options)`
  - `methodData`：一個包含支付方式的對象陣列。
  - `details`：包含支付金額、商品描述等信息的對象。
  - `options`：可選的配置選項對象。

- **方法**：
  - `.show()`：顯示支付請求對話框，並返回一個 Promise，當用戶完成支付後該 Promise 將被解析。
  - `.abort()`：可以用來中止當前的支付請求。

## 範例
以下是使用 `PaymentRequest` 的基本範例：

```javascript
// 定義支付方式
const methodData = [{
    supportedMethods: 'basic-card',
    data: {
        supportedNetworks: ['visa', 'mastercard'],
        merchantName: '商戶名稱'
    }
}];

// 定義支付詳情
const details = {
    total: {
        label: '商品總價',
        amount: '10.00'
    },
    displayItems: [{
        label: '商品1',
        amount: '5.00'
    }, {
        label: '商品2',
        amount: '5.00'
    }]
};

// 創建支付請求
const request = new PaymentRequest(methodData, details);

// 顯示支付對話框
request.show().then(function(paymentResponse) {
    // 處理支付回應
    console.log(paymentResponse);
    paymentResponse.complete('success'); // 完成支付
}).catch(function(err) {
    console.error('支付請求失敗:', err);
});
```

## 解釋
在使用 `PaymentRequest` 時，開發者應注意以下幾點：

- **瀏覽器支持**：並非所有瀏覽器都支持 `PaymentRequest` API，開發者需檢查兼容性。
- **HTTPS要求**：`PaymentRequest` 只能在 HTTPS 環境中使用，以保護用戶的支付信息。
- **用戶體驗**：應該確保在用戶選擇支付方式後及時處理請求，避免用戶等待過久。

## 一句總結
`PaymentRequest` 是一個強大的 API，能簡化網頁支付流程並提升用戶體驗。