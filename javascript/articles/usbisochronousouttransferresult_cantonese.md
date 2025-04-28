<!--
Meta Description: # USBIsochronousOutTransferResult：JavaScript 中的 USB 傳輸結果 ## 簡介 USBIsochronousOutTransferResult 是一個在 JavaScript 中用於處理 USB 連接的異步結果的接口，特別是針對 ISO（等時）傳輸。此接...
Meta Keywords: usb, usbisochronousouttransferresult, device, error, then
-->

# USBIsochronousOutTransferResult：JavaScript 中的 USB 傳輸結果

## 簡介
USBIsochronousOutTransferResult 是一個在 JavaScript 中用於處理 USB 連接的異步結果的接口，特別是針對 ISO（等時）傳輸。此接口對於需要實時數據傳輸的應用程式（如音頻或視頻設備）至關重要。

## 文檔
USBIsochronousOutTransferResult 提供了一個結構化的方式來獲取有關 USB 等時輸出傳輸的結果。當進行 USB 等時傳輸時，此結果將包含傳輸的狀態及相關的數據信息。

### 目的
此接口的主要目的在於允許開發者檢查 USB 等時傳輸的狀態，確保數據能夠有效地發送至 USB 設備。

### 使用方法
要使用 USBIsochronousOutTransferResult，開發者需要首先建立 USB 連接，然後發起傳輸請求。當請求完成後，將返回 USBIsochronousOutTransferResult 物件，該物件包含了傳輸的成功與否、傳輸的字節數量等信息。

### 詳細信息
- **屬性**：
  - `status`: 表示傳輸的狀態，可以是 "ok" 或 "error"。
  - `bytesTransferred`: 表示成功傳輸的字節數。
  - `data`: 包含實際的傳輸數據。

- **方法**：
  - `abort()`: 用於中止正在進行的傳輸請求。

## 範例
以下是使用 USBIsochronousOutTransferResult 的基本範例：

```javascript
navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] })
  .then(device => {
    return device.open();
  })
  .then(device => {
    return device.selectConfiguration(1);
  })
  .then(device => {
    return device.claimInterface(0);
  })
  .then(device => {
    // 發起等時輸出傳輸
    return device.transferOut(1, new Uint8Array([1, 2, 3, 4]));
  })
  .then(result => {
    if (result.status === 'ok') {
      console.log(`成功傳輸 ${result.bytesTransferred} 字節`);
    } else {
      console.error('傳輸失敗');
    }
  })
  .catch(error => {
    console.error(`出現錯誤: ${error}`);
  });
```

## 解釋
在使用 USBIsochronousOutTransferResult 時，開發者應注意以下幾點：

- **錯誤處理**：確保在每個步驟中都進行錯誤處理，以防止出現未捕獲的異常。
- **設備兼容性**：並非所有 USB 設備都支持等時傳輸，開發者應檢查設備的規格。
- **傳輸大小**：確保傳輸的數據大小符合設備的要求，否則可能導致傳輸失敗。

## 一句總結
USBIsochronousOutTransferResult 是處理 USB 等時輸出傳輸的關鍵接口，提供了傳輸狀態及數據的詳細信息。