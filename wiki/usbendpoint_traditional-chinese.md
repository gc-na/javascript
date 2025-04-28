<!--
Meta Description: # USBEndpoint：JavaScript 中的 USB 端點操作 ## 概述 `USBEndpoint` 是 JavaScript 中 WebUSB API 的一部分，允許開發者與 USB 設備進行通訊。這個接口提供了一種簡單的方法來與各種 USB 設備互動，從而使網頁應用能夠直接與硬體設備...
Meta Keywords: device, usb, usbendpoint, javascript, const
-->

# USBEndpoint：JavaScript 中的 USB 端點操作

## 概述
`USBEndpoint` 是 JavaScript 中 WebUSB API 的一部分，允許開發者與 USB 設備進行通訊。這個接口提供了一種簡單的方法來與各種 USB 設備互動，從而使網頁應用能夠直接與硬體設備連接和傳輸數據。

## 文檔
### 目的
`USBEndpoint` 設計用於表示 USB 通訊中的端點。端點是 USB 設備與主機之間的數據傳輸通道，每個端點都有唯一的地址和類型（如輸入或輸出）。

### 使用方法
要使用 `USBEndpoint`，必須先獲取一個 USB 設備的實例，然後可以通過該設備的 `configuration` 和 `interface` 屬性來訪問端點。

```javascript
navigator.usb.requestDevice({ filters: [{ vendorId: 0xXXXX }] })
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
    const endpoint = device.interfaces[0].endpoints[0]; // 獲取第一個端點
    // 進一步操作
  })
  .catch(error => {
    console.error(error);
  });
```

### 詳細說明
`USBEndpoint` 物件包含以下屬性：
- `endpointNumber`：端點的地址，範圍從 0 到 255。
- `direction`：端點的方向，可能是 'in' 或 'out'，分別表示數據流入或流出設備。
- `type`：端點的類型，包括控制端點、輸入端點和輸出端點等。

要從端點讀取或寫入數據，使用 `transferIn` 和 `transferOut` 方法。

## 範例
### 基本使用範例
以下是如何從 USB 端點讀取數據的範例：

```javascript
async function readFromEndpoint(device) {
  const endpoint = device.interface[0].endpoints[0];
  const result = await device.transferIn(endpoint.endpointNumber, 64); // 讀取 64 字節
  console.log(new TextDecoder().decode(result.data));
}
```

### 寫入數據範例
以下是如何向 USB 端點寫入數據的範例：

```javascript
async function writeToEndpoint(device, data) {
  const endpoint = device.interface[0].endpoints[1]; // 假設有輸出端點
  const result = await device.transferOut(endpoint.endpointNumber, new TextEncoder().encode(data));
  console.log(result); // 檢查寫入結果
}
```

## 解釋
在使用 `USBEndpoint` 時，開發者需注意以下幾點：
- 確保設備已正確連接並且已被選擇。
- 端點的方向必須正確，嘗試從輸出端點讀取數據會導致錯誤。
- 設備的接口必須在使用前聲明。
- 使用 Promise 進行異步操作，避免阻塞主執行緒。

## 總結
`USBEndpoint` 是 JavaScript 中用於與 USB 設備進行數據傳輸的重要接口，提供了簡單而強大的方法來輕鬆實現硬體交互。