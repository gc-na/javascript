<!--
Meta Description: # BluetoothRemoteGATTServer: JavaScript中的藍牙遠端GATT伺服器 ## 概要 BluetoothRemoteGATTServer 是一個在 JavaScript 中實現的 API，用於與藍牙設備中的 GATT（通用屬性配置文件）伺服器進行交互，使開發人員能夠輕...
Meta Keywords: gatt, bluetoothremotegattserver, then, server, service
-->

# BluetoothRemoteGATTServer: JavaScript中的藍牙遠端GATT伺服器

## 概要
BluetoothRemoteGATTServer 是一個在 JavaScript 中實現的 API，用於與藍牙設備中的 GATT（通用屬性配置文件）伺服器進行交互，使開發人員能夠輕鬆地讀取和寫入設備的屬性。

## 文檔
### 目的
BluetoothRemoteGATTServer 使 Web 應用能夠連接到藍牙設備並與其進行數據交換。這個 API 特別適合需要與智能家居設備、健康追踪器及其他藍牙低能耗（BLE）設備進行通信的應用。

### 使用方法
要使用 BluetoothRemoteGATTServer，開發者需要透過 `BluetoothDevice` 物件來獲取 GATT 伺服器。以下是基本的使用步驟：

1. **請求藍牙設備**：
   使用 `navigator.bluetooth.requestDevice` 方法請求用戶選擇藍牙設備。
   
2. **連接到 GATT 伺服器**：
   一旦用戶選擇了設備，可以通過 `device.gatt.connect()` 方法來連接 GATT 伺服器。

3. **操作 GATT 服務和特徵**：
   連接成功後，可以使用 `server.getPrimaryService()` 及 `service.getCharacteristic()` 方法來獲取所需的服務和特徵。

### 詳細
BluetoothRemoteGATTServer 物件提供了以下方法：

- **connect()**：建立與 GATT 伺服器的連接。
- **disconnect()**：斷開與 GATT 伺服器的連接。
- **getPrimaryService(serviceUUID)**：獲取指定 UUID 的主要服務。
- **getPrimaryServices()**：獲取所有主要服務。

這些方法均返回 Promise，意味著它們是異步的，開發者需要使用 `.then()` 或 `async/await` 來處理結果。

## 示例
以下是一個基本的示範，展示如何連接到藍牙設備並訪問其 GATT 伺服器：

```javascript
navigator.bluetooth.requestDevice({ filters: [{ services: ['battery_service'] }] })
  .then(device => {
    console.log('Connecting to GATT Server...');
    return device.gatt.connect();
  })
  .then(server => {
    console.log('GATT Server Connected');
    return server.getPrimaryService('battery_service');
  })
  .then(service => {
    console.log('Service found:', service);
    return service.getCharacteristic('battery_level');
  })
  .then(characteristic => {
    return characteristic.readValue();
  })
  .then(value => {
    console.log('Battery level is ' + value.getUint8(0) + '%');
  })
  .catch(error => {
    console.error('Error: ' + error);
  });
```

## 解釋
在使用 BluetoothRemoteGATTServer 時，開發者可能會遇到一些常見問題：

- **權限問題**：用戶需要手動授權應用程序訪問藍牙設備。若用戶拒絕訪問，則會拋出錯誤。
- **連接失敗**：可能會因為藍牙設備未開啟或超出範圍而導致連接失敗。
- **服務與特徵的可用性**：並非所有藍牙設備都支持所有服務和特徵，開發者需檢查設備的規格。

## 一句總結
BluetoothRemoteGATTServer 是 JavaScript 中的藍牙 API，可實現與藍牙設備的 GATT 伺服器進行數據交換的功能。