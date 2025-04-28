<!--
Meta Description: # JavaScript 中的 USB：深入了解 USB Web API ## 簡介 USB Web API 是一個允許 JavaScript 應用程式與 USB 設備進行通信的接口。這使得網頁應用能夠直接訪問連接到用戶電腦的 USB 設備，實現更豐富的功能和互動性。 ## 文檔 ### 目的 US...
Meta Keywords: usb, device, api, web, javascript
-->

# JavaScript 中的 USB：深入了解 USB Web API

## 簡介
USB Web API 是一個允許 JavaScript 應用程式與 USB 設備進行通信的接口。這使得網頁應用能夠直接訪問連接到用戶電腦的 USB 設備，實現更豐富的功能和互動性。

## 文檔
### 目的
USB Web API 旨在提供一個簡單的方式讓開發者可以直接從網頁應用程式控制和通信 USB 設備，這對於需要與硬體交互的應用程式尤為重要，例如打印機、掃描儀和其他外部設備。

### 用法
要使用 USB Web API，開發者需要確保其網站使用 HTTPS 協議，因為這個 API 只允許安全的上下文中使用。以下是使用 USB API 的基本步驟：

1. **請求設備**：使用 `navigator.usb.requestDevice()` 方法請求用戶選擇 USB 設備。
2. **連接設備**：在用戶選擇設備後，可以使用 `device.open()` 方法來打開與設備的連接。
3. **傳輸數據**：使用 `device.transferOut()` 和 `device.transferIn()` 方法來向設備發送數據或從設備接收數據。
4. **關閉連接**：完成操作後，使用 `device.close()` 方法關閉連接。

### 詳細信息
USB Web API 的核心對象是 `USBDevice`，它提供了多種方法和屬性來處理 USB 設備。以下是一些重要的方法和屬性：

- **`navigator.usb.getDevices()`**：獲取已連接的所有 USB 設備。
- **`device.open()`**：打開與 USB 設備的連接。
- **`device.close()`**：關閉與 USB 設備的連接。
- **`device.transferIn(endpointNumber, length)`**：從 USB 設備的指定端點接收數據。
- **`device.transferOut(endpointNumber, data)`**：向 USB 設備的指定端點發送數據。

## 例子
### 基本用法示例
```javascript
async function connectUSB() {
    try {
        const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
        await device.open();
        console.log('USB 設備已連接', device.productName);
        // 進行數據傳輸
    } catch (error) {
        console.error('無法連接到 USB 設備', error);
    }
}
```

### 數據傳輸示例
```javascript
async function sendData(device, data) {
    const encoder = new TextEncoder();
    const dataBuffer = encoder.encode(data);
    await device.transferOut(1, dataBuffer);
    console.log('數據已發送');
}
```

## 解釋
使用 USB Web API 時，需要注意以下幾點：

- **安全上下文**：USB API 只能在 HTTPS 網站上使用，這意味著開發者需要確保其網站的安全性。
- **用戶授權**：用戶必須明確選擇要連接的 USB 設備，開發者無法在不經過用戶授權的情況下自動連接。
- **錯誤處理**：在進行設備連接和數據傳輸時，必須實施適當的錯誤處理，以應對設備未連接或傳輸失敗等情況。

## 總結
USB Web API 使 JavaScript 開發者能夠直接與 USB 設備進行互動，開啟了許多創新的應用場景。