<!--
Meta Description: # USBIsochronousInTransferResult：JavaScript 中的 USB 传输结果处理 ## 概述 USBIsochronousInTransferResult 是 WebUSB API 中的一个接口，专门用于处理通过 USB 连接进行的等时输入传输的结果。它允许开发者高...
Meta Keywords: usb, usbisochronousintransferresult, device, await, data
-->

# USBIsochronousInTransferResult：JavaScript 中的 USB 传输结果处理

## 概述
USBIsochronousInTransferResult 是 WebUSB API 中的一个接口，专门用于处理通过 USB 连接进行的等时输入传输的结果。它允许开发者高效地从 USB 设备接收流式数据，适用于实时数据传输的应用场景，如音频和视频流。

## 文档
### 目的
USBIsochronousInTransferResult 旨在提供 USB 等时输入传输的结果，包括接收到的数据和传输状态。该接口让开发者可以更好地控制 USB 设备的数据流，并进行实时处理。

### 使用
在 JavaScript 中，USBIsochronousInTransferResult 通常与 `USBDevice` 接口结合使用，尤其是在进行等时数据传输时。以下是如何在 WebUSB 中使用的基本步骤：

1. **连接 USB 设备**：使用 `navigator.usb.requestDevice()` 请求连接 USB 设备。
2. **打开设备**：通过 `device.open()` 打开设备。
3. **开始传输**：使用 `device.transferIn(endpointNumber, length)` 方法进行等时输入传输。
4. **处理结果**：使用 USBIsochronousInTransferResult 处理传输结果。

### 详细信息
- **属性**：
  - `data`：接收到的数据，这是一个 `ArrayBuffer`，包含了传输的数据内容。
  - `status`：传输的状态，指示是否成功完成传输。

- **方法**：
  - `transferIn(endpointNumber, length)`：请求从指定的端点接收数据，并返回一个 `Promise`，该 promise 解析为 USBIsochronousInTransferResult 对象。

## 示例
以下是一个使用 USBIsochronousInTransferResult 的基本示例：

```javascript
async function readFromUSB() {
    const device = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
    await device.open();
    await device.selectConfiguration(1);
    await device.claimInterface(0);

    const result = await device.transferIn(1, 64); // 从端点 1 读取 64 字节
    const data = new Uint8Array(result.data);
    console.log("接收到的数据:", data);
    
    await device.releaseInterface(0);
    await device.close();
}

readFromUSB().catch(console.error);
```

## 解释
在使用 USBIsochronousInTransferResult 时，开发者需要注意以下几点：

- 确保 USB 设备已正确连接并具有合适的权限。
- 处理数据时，注意数组缓冲区的大小，避免因数据溢出导致错误。
- 需要处理可能的错误，如传输失败或设备被移除等情况。

## 一句话总结
USBIsochronousInTransferResult 是 WebUSB API 中用于处理 USB 设备等时输入传输结果的接口，支持实时数据的接收和处理。