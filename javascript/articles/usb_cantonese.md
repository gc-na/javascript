<!--
Meta Description: # USB 與 JavaScript 的關係：如何使用 Web USB API ## 簡介 Web USB API 使得 JavaScript 開發者能夠直接與 USB 設備進行通信，這為網頁應用程序開啟了新的可能性，允許用戶從瀏覽器連接和控制各種硬件設備。 ## 文檔 ### 目的 Web USB...
Meta Keywords: usb, api, web, javascript, device
-->

# USB 與 JavaScript 的關係：如何使用 Web USB API

## 簡介
Web USB API 使得 JavaScript 開發者能夠直接與 USB 設備進行通信，這為網頁應用程序開啟了新的可能性，允許用戶從瀏覽器連接和控制各種硬件設備。

## 文檔
### 目的
Web USB API 的主要目的在於簡化瀏覽器與 USB 設備之間的交互，使開發者能夠在網頁應用中輕鬆訪問和控制 USB 設備。

### 使用方法
要使用 Web USB API，開發者需要確保設備支持 USB 協議，並且用戶的瀏覽器需支持該 API。開發者可以使用 `navigator.usb` 來訪問 USB API 的功能，如下所示：

1. **獲取 USB 設備**：
   ```javascript
   const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
   ```

2. **連接 USB 設備**：
   ```javascript
   await device.open();
   ```

3. **讀取和寫入數據**：
   ```javascript
   const data = new Uint8Array([/* data to send */]);
   await device.transferOut(endpointNumber, data);
   const response = await device.transferIn(endpointNumber, dataLength);
   ```

### 詳細說明
Web USB API 提供了幾個重要的方法和屬性，包括：
- `navigator.usb.requestDevice()`: 顯示用戶選擇 USB 設備的界面。
- `USBDevice.open()`: 開啟與 USB 設備的連接。
- `USBDevice.close()`: 關閉與 USB 設備的連接。
- `USBDevice.transferOut()`: 將數據發送到 USB 設備。
- `USBDevice.transferIn()`: 從 USB 設備接收數據。

開發者需注意，Web USB API 目前對於某些瀏覽器的支持情況有所不同，建議查閱最新的瀏覽器兼容性表。

## 範例
### 基本用法範例
以下是一個簡單的範例，用於連接 USB 設備並傳送數據。
```javascript
async function connectToDevice() {
    try {
        const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
        await device.open();
        const dataToSend = new Uint8Array([0x01, 0x02]);
        await device.transferOut(1, dataToSend);
        console.log("數據已成功發送至 USB 設備");
    } catch (error) {
        console.error("發生錯誤:", error);
    }
}
```

## 解釋
- **常見問題**：用戶在使用 Web USB API 時，可能會面臨一些常見的問題，如設備無法連接、權限被拒絕等。開發者應確保用戶已正確選擇設備並授予所需的權限。
- **注意事項**：由於 Web USB API 直接與硬件交互，開發者需謹慎處理數據並確保不會導致設備損壞。

## 一句總結
Web USB API 使得 JavaScript 開發者能夠方便地與 USB 設備進行互動，開啟了網頁應用的新可能性。