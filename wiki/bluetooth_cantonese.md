<!--
Meta Description: # Bluetooth 在 JavaScript 中的應用 ## 簡介 Bluetooth 是一種無線通信技術，JavaScript 中的 Web Bluetooth API 使開發者能夠與支持 Bluetooth 的設備進行互動。 ## 文檔 ### 目的 Web Bluetooth API 允許...
Meta Keywords: bluetooth, api, web, gatt, then
-->

# Bluetooth 在 JavaScript 中的應用

## 簡介
Bluetooth 是一種無線通信技術，JavaScript 中的 Web Bluetooth API 使開發者能夠與支持 Bluetooth 的設備進行互動。

## 文檔
### 目的
Web Bluetooth API 允許網頁直接與藍牙設備進行連接，從而實現數據交換或控制功能。這對於物聯網設備、穿戴設備和其他藍牙連接的硬件特別有用。

### 使用方式
使用 Web Bluetooth API 時，開發者首先需要請求用戶的授權，然後掃描可用的藍牙設備並建立連接。以下是基本的 API 方法：

- `navigator.bluetooth.requestDevice()`: 請求用戶選擇一個藍牙設備。
- `device.gatt.connect()`: 與選定設備的 GATT 服務建立連接。
- `service.getCharacteristic()`: 獲取特定的特徵以進行數據讀取或寫入。

### 詳細信息
Web Bluetooth API 提供了一組功能強大的方法和屬性，通過這些方法和屬性，開發者可以輕鬆與藍牙設備進行通信。這些包括：

- **設備過濾**: 可以在請求設備時使用過濾器來限制可見的設備。
- **服務和特徵**: 使用 GATT 服務與特徵進行數據交互。
- **數據格式**: 通常使用 ArrayBuffer 和 DataView 處理二進制數據。

## 範例
以下是如何使用 Web Bluetooth API 的基本範例：

```javascript
// 請求用戶選擇藍牙設備
navigator.bluetooth.requestDevice({
  filters: [{ services: ['battery_service'] }]
})
.then(device => {
  console.log('選擇的設備:', device);
  return device.gatt.connect();
})
.then(server => {
  console.log('連接到 GATT 服務:', server);
  return server.getPrimaryService('battery_service');
})
.then(service => {
  return service.getCharacteristic('battery_level');
})
.then(characteristic => {
  return characteristic.readValue();
})
.then(value => {
  console.log('電池電量:', value.getUint8(0));
})
.catch(error => {
  console.error('發生錯誤:', error);
});
```

## 解釋
在使用 Web Bluetooth API 時，開發者可能會遇到一些常見的陷阱：

- **瀏覽器支持**: 並非所有瀏覽器都支持 Web Bluetooth，確保在支持的瀏覽器中測試。
- **HTTPS要求**: 此 API 只能在安全上下文中使用，請確保你的網站使用 HTTPS。
- **設備兼容性**: 不是所有藍牙設備都支持 GATT，開發者需要確認設備的兼容性。
- **用戶授權**: 藍牙設備的連接需要用戶的明確授權，請務必正確處理用戶的選擇。

## 簡短總結
JavaScript 中的 Web Bluetooth API 使開發者能夠輕鬆與藍牙設備進行連接和數據交換。