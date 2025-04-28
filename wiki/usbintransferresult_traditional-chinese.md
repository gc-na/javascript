<!--
Meta Description: # USBInTransferResult：JavaScript 中的 USB 數據傳輸結果 ## 摘要 USBInTransferResult 是一個 JavaScript 接口，用於描述從 USB 設備接收數據的結果。它提供了關於數據傳輸的狀態和接收到的數據的詳細資訊，對於開發基於 USB 的應...
Meta Keywords: usb, result, usbintransferresult, device, error
-->

# USBInTransferResult：JavaScript 中的 USB 數據傳輸結果

## 摘要
USBInTransferResult 是一個 JavaScript 接口，用於描述從 USB 設備接收數據的結果。它提供了關於數據傳輸的狀態和接收到的數據的詳細資訊，對於開發基於 USB 的應用程序至關重要。

## 文檔
USBInTransferResult 是在 Web USB API 中定義的，主要用於處理從 USB 設備傳輸到網頁的數據。當你透過 USB 設備進行數據接收時，這個接口會返回一個包含以下屬性的對象：

- **data**：一個包含接收到的數據的 ArrayBuffer。
- **status**：表明傳輸狀態的字符串，例如 "completed" 或 "error"。
- **bytesTransferred**：成功傳輸的字節數。

### 用法
USBInTransferResult 通常在調用 `transferIn()` 方法時使用，這個方法是 Web USB API 的一部分，可以讓開發者從 USB 設備中請求數據。當數據成功接收後，會返回一個 USBInTransferResult 對象。

#### 語法範例：
```javascript
navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] })
  .then(device => device.open())
  .then(device => device.transferIn(endpointNumber, length))
  .then(result => {
    // 處理 USBInTransferResult
    console.log(result.data);
    console.log(result.status);
    console.log(result.bytesTransferred);
  })
  .catch(error => {
    console.error('傳輸失敗:', error);
  });
```

## 範例
以下是使用 USBInTransferResult 的基本示例：

### 示例 1：從 USB 設備接收數據
```javascript
async function readDataFromUSB(device) {
  await device.open();
  const result = await device.transferIn(1, 64); // endpoint 1, length 64
  if (result.status === 'completed') {
    const decoder = new TextDecoder();
    const data = decoder.decode(result.data);
    console.log('接收到的數據:', data);
  } else {
    console.error('傳輸錯誤:', result.status);
  }
}
```

### 示例 2：處理錯誤狀態
```javascript
async function getData(device) {
  try {
    await device.open();
    const result = await device.transferIn(1, 64);
    
    if (result.status !== 'completed') {
      throw new Error('數據傳輸未完成');
    }

    console.log('接收的字節數:', result.bytesTransferred);
  } catch (error) {
    console.error('發生錯誤:', error);
  }
}
```

## 解釋
在使用 USBInTransferResult 時，有幾個常見的陷阱需要注意：

1. **檢查狀態**：在使用 USBInTransferResult 返回的數據之前，務必檢查 `status` 屬性，確保數據傳輸已成功完成。
2. **數據解碼**：接收到的數據是 ArrayBuffer 格式，必須使用 `TextDecoder` 或類似的工具來進行解碼，才能正確讀取數據內容。
3. **錯誤處理**：在進行 USB 數據傳輸時，可能會遇到多種錯誤，務必使用 try-catch 來處理異常情況。

## 一行摘要
USBInTransferResult 是一個接口，用於描述從 USB 設備接收數據的結果，包括數據內容和傳輸狀態。