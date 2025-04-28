<!--
Meta Description: # USBDevice：JavaScript 中的 USB 設備接口 ## 概述 USBDevice 是一個在 JavaScript 中用來與 USB 設備進行交互的接口，屬於 WebUSB API 的一部分。它允許開發者在網頁應用程式中直接與 USB 設備進行通信，提供了更靈活的硬體連接選項。 #...
Meta Keywords: device, usb, usbdevice, javascript, await
-->

# USBDevice：JavaScript 中的 USB 設備接口

## 概述
USBDevice 是一個在 JavaScript 中用來與 USB 設備進行交互的接口，屬於 WebUSB API 的一部分。它允許開發者在網頁應用程式中直接與 USB 設備進行通信，提供了更靈活的硬體連接選項。

## 文檔
### 目的
USBDevice 接口的主要目的是讓網頁應用程式能夠與各種 USB 設備進行連接與數據交換。這使得開發者能夠創建與硬體互動的應用，例如控制打印機、感測器或其他外部設備。

### 使用方法
在使用 USBDevice 之前，您必須先請求 USB 設備的權限，然後才能進行連接。以下是基本的使用步驟：

1. **請求設備**：使用 `navigator.usb.requestDevice()` 方法來請求用戶選擇 USB 設備。
2. **連接設備**：獲取到設備後，可以通過 `device.open()` 方法打開連接。
3. **傳輸數據**：使用 `device.transferIn()` 和 `device.transferOut()` 方法進行數據傳輸。
4. **關閉設備**：完成後，應使用 `device.close()` 方法關閉連接。

### 詳細說明
USBDevice 提供了多個屬性和方法來進行設備管理：

- **屬性**：
  - `device.productId`：設備的產品 ID。
  - `device.vendorId`：設備的廠商 ID。
  - `device.configuration`：設備的當前配置。

- **方法**：
  - `open()`：打開設備連接。
  - `close()`：關閉設備連接。
  - `transferIn(endpoint, length)`：從指定的端點接收數據。
  - `transferOut(endpoint, data)`：向指定的端點發送數據。

## 範例
以下是一些基本的範例用法：

### 請求 USB 設備
```javascript
navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] })
  .then(device => {
    console.log(`選擇的設備：${device.productId}`);
  })
  .catch(error => {
    console.error(`請求設備失敗：${error}`);
  });
```

### 開啟和傳輸數據
```javascript
async function connectToDevice(device) {
  await device.open(); // 開啟設備連接
  await device.selectConfiguration(1); // 選擇配置
  await device.claimInterface(0); // 佔用接口

  const data = new Uint8Array([/* ... */]);
  await device.transferOut(1, data); // 傳輸數據
}
```

## 解釋
在使用 USBDevice 時，有幾個常見的陷阱需要注意：

- **權限問題**：用戶必須授予權限才能連接 USB 設備。
- **設備兼容性**：並非所有 USB 設備都支持 WebUSB，確保您的設備已經經過測試。
- **異步操作**：使用 USBDevice 方法時，大多數是異步的，需使用 `async/await` 或 `.then()` 處理 Promise。

## 一行總結
USBDevice 是一個 JavaScript 接口，允許開發者直接與 USB 設備進行交互和數據傳輸。