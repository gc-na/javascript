<!--
Meta Description: # USBDevice：JavaScript 中的 USB 設備操作介面 ## 摘要 USBDevice 是一個用於在 Web 應用程式中與 USB 設備進行互動的介面，透過它，開發者可以輕鬆地連接、讀取和寫入 USB 設備。 ## 文檔 ### 目的 USBDevice 介面提供了一組 API，讓...
Meta Keywords: usb, usbdevice, device, error, javascript
-->

# USBDevice：JavaScript 中的 USB 設備操作介面

## 摘要
USBDevice 是一個用於在 Web 應用程式中與 USB 設備進行互動的介面，透過它，開發者可以輕鬆地連接、讀取和寫入 USB 設備。

## 文檔
### 目的
USBDevice 介面提供了一組 API，讓開發者能夠透過瀏覽器直接與 USB 設備進行通訊，這對於需要與硬體設備進行互動的應用程式尤其重要，例如打印機、傳感器和其他外部設備。

### 使用方式
要使用 USBDevice，首先需要獲取使用者的許可，然後可以使用 `navigator.usb` 物件來發現和連接 USB 設備。以下是一些基本步驟：

1. **請求設備**：使用 `navigator.usb.requestDevice()` 方法來請求特定的 USB 設備。
2. **連接設備**：一旦獲得許可，可以使用 `USBDevice.open()` 方法來連接設備。
3. **傳輸數據**：使用 `USBDevice.transferIn()` 和 `USBDevice.transferOut()` 方法來讀取和寫入設備數據。

### 詳細說明
- **USBDevice 物件的屬性**：
  - `productId`：設備的產品 ID。
  - `vendorId`：設備的供應商 ID。
  - `interfaces`：設備支持的介面列表。

- **方法**：
  - `open()`：打開與 USB 設備的連接。
  - `close()`：關閉 USB 設備的連接。
  - `selectAlternateInterface()`：選擇設備的替代介面。

## 範例
以下是 USBDevice 使用的基本範例：

```javascript
async function connectUSB() {
  try {
    const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
    await device.open(); // 開啟設備
    console.log("Connected to USB device: ", device.productId);
  } catch (error) {
    console.error("Error connecting to USB device: ", error);
  }
}

connectUSB();
```

## 解釋
### 常見陷阱
1. **權限問題**：使用者必須手動授予權限，否則無法連接設備。
2. **設備不支持**：並不是所有 USB 設備都支持 WebUSB，必須確保設備的相容性。
3. **錯誤處理**：在使用 USBDevice 的過程中，必須適當處理異常情況，例如設備斷開或無法訪問。

### 注意事項
- 確保在 HTTPS 環境中使用 USBDevice，因為大多數瀏覽器不允許在不安全的環境下訪問 USB。
- 有些瀏覽器可能對 USB 設備的支持不完整，建議檢查兼容性。

## 一句話總結
USBDevice 介面為 JavaScript 提供了直接與 USB 設備進行互動的能力，讓開發者可以輕鬆讀取和寫入設備數據。