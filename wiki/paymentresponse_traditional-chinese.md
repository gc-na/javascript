<!--
Meta Description: # PaymentResponse：JavaScript 中的支付響應物件 ## 簡介 `PaymentResponse` 是 Web 支付 API 中的一個重要物件，允許網頁應用程式在完成支付過程後獲取支付的詳細信息。此物件提供了一種標準化的方式來處理和存取支付響應，以提升用戶的購物體驗。 ## ...
Meta Keywords: paymentresponse, paymentrequest, show, javascript, web
-->

# PaymentResponse：JavaScript 中的支付響應物件

## 簡介
`PaymentResponse` 是 Web 支付 API 中的一個重要物件，允許網頁應用程式在完成支付過程後獲取支付的詳細信息。此物件提供了一種標準化的方式來處理和存取支付響應，以提升用戶的購物體驗。

## 文檔
### 目的
`PaymentResponse` 用於表示支付請求的回應，包含了一系列有關支付的詳細資訊。這些資訊可以用於確認交易、更新用戶界面或進行後端處理。

### 用法
在調用 `PaymentRequest` 的 `show()` 方法後，會返回一個 `PaymentResponse` 物件，該物件包含了支付的相關數據。開發者可以使用這些數據進行後續的處理和驗證。

### 屬性
- `details`：包含支付的詳細資訊，具體內容依賴於支付方式。
- `methodName`：表示支付方式的字符串，例如 "basic-card"。
- `payerName`：付款人的姓名。
- `payerEmail`：付款人的電子郵件地址。
- `payerPhone`：付款人的電話號碼。

### 方法
- `complete(status)`：用於標記支付請求的完成狀態，接受一個字符串作為參數，可以是 "success"、"fail" 或 "unknown"。

## 範例
以下是使用 `PaymentResponse` 的基本範例：

```javascript
// 創建支付請求
const paymentRequest = new PaymentRequest(['basic-card'], {
    total: {
        label: 'Total',
        amount: '10.00'
    }
});

// 顯示支付請求
paymentRequest.show().then(function(paymentResponse) {
    // 獲取支付詳細資訊
    console.log(paymentResponse.details);
    
    // 完成支付請求
    paymentResponse.complete("success");
}).catch(function(err) {
    console.error(err);
});
```

## 解釋
在使用 `PaymentResponse` 時，開發者需要注意以下幾點：
- 確保支付方式的支持：不同的瀏覽器可能只支持部分支付方式，需提前進行測試。
- 錯誤處理：在呼叫 `show()` 方法時，應添加適當的錯誤處理，以避免用戶體驗受損。
- 安全性考量：處理支付數據時，需遵循安全標準，避免洩露敏感信息。

## 一句總結
`PaymentResponse` 是一個關鍵的物件，用於處理和存取 Web 支付 API 中的支付響應數據。