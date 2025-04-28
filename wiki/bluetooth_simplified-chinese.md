<!--
Meta Description: # JavaScript 中的蓝牙 (Bluetooth) API ## 概述 蓝牙（Bluetooth）API 使开发者能够在网页中与蓝牙设备进行交互。通过该 API，开发者可以发现、连接并与蓝牙设备进行数据传输，实现物联网（IoT）应用的需求。 ## 文档 蓝牙 API 主要通过 `naviga...
Meta Keywords: api, bluetooth, gatt, then, navigator
-->

# JavaScript 中的蓝牙 (Bluetooth) API

## 概述
蓝牙（Bluetooth）API 使开发者能够在网页中与蓝牙设备进行交互。通过该 API，开发者可以发现、连接并与蓝牙设备进行数据传输，实现物联网（IoT）应用的需求。

## 文档
蓝牙 API 主要通过 `navigator.bluetooth` 对象提供，包含多个方法和属性，以支持蓝牙设备的扫描、连接和通信。

### 目的
该 API 旨在简化与蓝牙设备的交互，使网页应用能够直接与支持蓝牙的硬件进行通信。

### 用法
1. **请求设备**: 使用 `navigator.bluetooth.requestDevice()` 方法请求连接的蓝牙设备。
2. **连接设备**: 通过 `device.gatt.connect()` 方法建立 GATT 连接。
3. **读取和写入特征**: 通过 GATT 服务器与设备的特征进行交互，使用 `getCharacteristic()` 方法实现。

### 重要属性和方法
- `navigator.bluetooth.requestDevice()`: 请求一个或多个蓝牙设备。
- `BluetoothDevice.gatt.connect()`: 建立与设备的 GATT 连接。
- `BluetoothRemoteGATTService.getCharacteristic()`: 获取特定特征。

## 示例
以下是如何使用蓝牙 API 连接到设备的基础示例：

```javascript
// 请求设备
navigator.bluetooth.requestDevice({ 
  filters: [{ services: ['battery_service'] }] 
})
.then(device => {
  console.log('连接到设备:', device.name);
  return device.gatt.connect();
})
.then(server => {
  console.log('已连接到GATT服务器:', server);
  return server.getPrimaryService('battery_service');
})
.then(service => {
  return service.getCharacteristic('battery_level');
})
.then(characteristic => {
  return characteristic.readValue();
})
.then(value => {
  console.log('电池电量:', value.getUint8(0));
})
.catch(error => {
  console.error('发生错误:', error);
});
```

## 说明
- **权限问题**: 在使用蓝牙 API 时，浏览器需要用户的授权，因此必须确保适当地处理权限请求。
- **兼容性**: 目前，蓝牙 API 在某些浏览器中（如 Chrome 和 Edge）支持较好，但在 Firefox 和 Safari 中可能存在限制。
- **HTTPS**: 蓝牙 API 仅在 HTTPS 环境下可用，因此确保您的网页通过安全协议提供。

## 一句话总结
JavaScript 的蓝牙 API 允许开发者与蓝牙设备进行便捷的连接和数据交互。