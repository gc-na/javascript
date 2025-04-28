<!--
Meta Description: # PaymentResponse: JavaScript 中的支付響應物件 ## 簡介 `PaymentResponse` 是一個在 JavaScript 中用於處理網上支付的物件，充當與支付請求交互的媒介。它允許開發者在網頁中集成支付功能，提升用戶的購物體驗。 ## 文檔 `PaymentRes...
Meta Keywords: paymentresponse, paymentrequest, javascript, show, error
-->

# PaymentResponse: JavaScript 中的支付響應物件

## 簡介
`PaymentResponse` 是一個在 JavaScript 中用於處理網上支付的物件，充當與支付請求交互的媒介。它允許開發者在網頁中集成支付功能，提升用戶的購物體驗。

## 文檔
`PaymentResponse` 物件是 Web 支付 API 的一部分，主要用於處理來自支付請求的響應。當用戶在網頁上發起支付時，瀏覽器會返回 `PaymentResponse` 物件，其包含與支付交易相關的資訊。

### 目的
`PaymentResponse` 的目的是提供一個標準化的方式來處理支付響應，讓開發者能夠輕鬆訪問交易的詳細資料，如支付狀態、付款方式以及交易金額等。

### 使用方式
要使用 `PaymentResponse`，首先需要創建一個支付請求，然後在用戶確認支付後，獲取響應。這裡是如何使用它的基本步驟：

1. 創建一個 `PaymentRequest` 物件。
2. 調用 `show()` 方法來顯示支付界面。
3. 當用戶完成支付後，將返回一個 `PaymentResponse` 物件。

### 詳細說明
`PaymentResponse` 物件的屬性和方法包括：

- `details`: 包含支付交易的詳細資訊。
- `paymentMethod`: 用戶選擇的付款方式。
- `payerName`: 付款人的姓名。
- `complete(status)`: 用於標記支付過程的完成狀態，參數為字符串，如 `"success"` 或 `"fail"`。

## 示例
以下是使用 `PaymentResponse` 的基本示例：

```javascript
// 創建支付請求
const paymentRequest = new PaymentRequest(
  ['basic-card'],
  {
    total: {
      label: '總計',
      amount: '10.00',
    },
  }
);

// 顯示支付界面
paymentRequest.show().then((paymentResponse) => {
  // 取得支付響應
  console.log(paymentResponse);
  
  // 完成支付
  paymentResponse.complete('success');
}).catch((error) => {
  console.error('支付失敗:', error);
});
```

## 說明
使用 `PaymentResponse` 時，有幾個常見的陷阱需要注意：

1. **支付方法的支持**: 不同瀏覽器對支付方法的支持可能不同，開發者應該檢查用戶的瀏覽器是否支持所需的支付方法。
2. **異常處理**: 確保在處理 `show()` 返回的 Promise 時，添加錯誤處理，以便能處理用戶取消支付的情況。
3. **安全性**: 請確保使用 HTTPS 來提供安全的支付環境，因為 `PaymentRequest` 僅在安全上下文中可用。

## 總結
`PaymentResponse` 是一個方便的 JavaScript 物件，用於處理網路支付響應，提供一個標準化的支付處理方式，提升用戶體驗。