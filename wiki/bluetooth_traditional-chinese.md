<!--
Meta Description: # Bluetooth 與 JavaScript：建立無線連接的指南 ## 摘要 Bluetooth API 允許 JavaScript 應用程式與藍牙設備進行無縫連接，提供了一種在網頁應用中整合藍牙功能的方式。 ## 文件 Bluetooth API 是一組用於與藍牙設備進行通信的網頁標準。使用者...
Meta Keywords: bluetooth, api, gatt, device, then
-->

# Bluetooth 與 JavaScript：建立無線連接的指南

## 摘要
Bluetooth API 允許 JavaScript 應用程式與藍牙設備進行無縫連接，提供了一種在網頁應用中整合藍牙功能的方式。

## 文件
Bluetooth API 是一組用於與藍牙設備進行通信的網頁標準。使用者可以通過這個 API 瀏覽、連接和與附近的藍牙設備互動。這使開發者能夠創建更加互動和智慧的網頁應用，從而擴展了網頁應用的功能性。

### 目的
Bluetooth API 的目的是簡化藍牙設備的發現、連接和數據傳輸過程，使得開發者能夠在網頁中直接與各種藍牙設備進行互動。

### 使用方法
要使用 Bluetooth API，開發者首先需要調用 `navigator.bluetooth.requestDevice()` 方法來請求用戶選擇一個藍牙設備。然後，可以通過該設備的 GATT (通用屬性配置檔) 進行數據交互。

### 詳細說明
1. **請求設備**：開發者可以通過 `requestDevice` 方法請求用戶的藍牙設備。
2. **連接設備**：一旦用戶選擇了設備，開發者可以使用 `device.gatt.connect()` 方法來建立連接。
3. **發現服務和特徵**：連接後，可以獲取設備的服務和特徵，並進行數據讀取或寫入操作。
4. **斷開連接**：使用 `device.gatt.disconnect()` 方法可以安全地斷開連接。

## 例子
以下是使用 Bluetooth API 的基本範例：

```javascript
// 請求設備
navigator.bluetooth.requestDevice({
    filters: [{ services: ['battery_service'] }]
})
.then(device => {
    console.log('選擇的設備：', device);
    return device.gatt.connect();
})
.then(server => {
    console.log('已連接到 GATT Server');
    return server.getPrimaryService('battery_service');
})
.then(service => {
    console.log('獲取服務：', service);
    return service.getCharacteristic('battery_level');
})
.then(characteristic => {
    return characteristic.readValue();
})
.then(value => {
    console.log('電池電量：', value.getUint8(0) + '%');
})
.catch(error => {
    console.error('錯誤：', error);
});
```

## 解釋
在使用 Bluetooth API 時，開發者常見的問題包括：
- **權限問題**：某些瀏覽器可能需要 HTTPS 連接才能訪問 Bluetooth API。
- **設備兼容性**：並非所有藍牙設備都支持 GATT，開發者應確保所選設備的兼容性。
- **用戶授權**：用戶必須手動選擇設備，無法自動連接，這可能影響用戶體驗。

## 一句總結
Bluetooth API 為 JavaScript 提供了一個強大的工具，使開發者能夠輕鬆與藍牙設備進行交互。