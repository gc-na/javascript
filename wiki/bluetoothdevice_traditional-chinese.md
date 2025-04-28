<!--
Meta Description: # BluetoothDevice：JavaScript中的藍牙裝置操作 ## 簡介 BluetoothDevice 是一個 JavaScript 介面，用於表示可通過 Web Bluetooth API 進行互動的藍牙裝置。它讓網頁能夠與藍牙周邊設備進行連接和通信，從而擴展了 Web 應用的功能。...
Meta Keywords: bluetoothdevice, error, bluetooth, gatt, const
-->

# BluetoothDevice：JavaScript中的藍牙裝置操作

## 簡介
BluetoothDevice 是一個 JavaScript 介面，用於表示可通過 Web Bluetooth API 進行互動的藍牙裝置。它讓網頁能夠與藍牙周邊設備進行連接和通信，從而擴展了 Web 應用的功能。

## 文檔
### 目的
BluetoothDevice 介面主要用於在 Web 應用中管理藍牙裝置的連接，並允許開發者訪問裝置的服務和特徵，進而實現數據的讀取和寫入。

### 使用方式
要創建 BluetoothDevice 實例，開發者通常通過 `navigator.bluetooth.requestDevice()` 方法來請求使用者選擇一個藍牙裝置。選擇裝置後，將返回一個 BluetoothDevice 物件，該物件包含裝置的各種屬性和方法。

### 詳細說明
- **屬性**
  - `name`: 藍牙裝置的名稱。
  - `id`: 裝置的唯一標識符。
  - `gatt`: 可用於訪問 GATT (Generic Attribute Profile) 服務的 GATTServer 物件。

- **使用範例**
  ```javascript
  navigator.bluetooth.requestDevice({ filters: [{ services: ['battery_service'] }] })
    .then(device => {
      console.log('發現裝置:', device.name);
      // 進一步操作
    })
    .catch(error => {
      console.error('錯誤:', error);
    });
  ```

- **方法**
  - `gatt.connect()`: 連接到裝置。
  - `gatt.disconnect()`: 斷開與裝置的連接。

## 例子
### 基本用法
以下是一個基本的範例，展示如何連接到藍牙裝置並獲取其電量服務的數據：

```javascript
async function connectToBluetoothDevice() {
  try {
    const device = await navigator.bluetooth.requestDevice({
      filters: [{ services: ['battery_service'] }]
    });

    const server = await device.gatt.connect();
    const service = await server.getPrimaryService('battery_service');
    const characteristic = await service.getCharacteristic('battery_level');
    const value = await characteristic.readValue();
    
    console.log('電池電量:', value.getUint8(0), '%');
  } catch (error) {
    console.error('連接失敗:', error);
  }
}

connectToBluetoothDevice();
```

## 解釋
使用 BluetoothDevice 時，開發者需要注意以下幾點：
- 確保使用 HTTPS 協議，因為 Web Bluetooth API 只能在安全上下文中使用。
- 藍牙裝置必須具有相應的服務和特徵，否則可能導致請求失敗。
- 用戶必須手動授權連接裝置，因此應提供友好的用戶界面以指導用戶。

## 總結
BluetoothDevice 介面使得 JavaScript 開發者能夠方便地操作藍牙裝置，擴展網頁應用的互動性和功能性。