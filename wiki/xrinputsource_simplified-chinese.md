<!--
Meta Description: # XRInputSource：JavaScript中的XR输入源 ## 概述 XRInputSource 是 WebXR API 中的一个重要接口，用于表示与 XR（扩展现实）设备交互的输入设备，例如手柄、手套或其他输入设备。通过 XRInputSource，开发者可以获取关于输入设备的状态和位置...
Meta Keywords: xrinputsource, inputsource, session, event, deviceid
-->

# XRInputSource：JavaScript中的XR输入源

## 概述
XRInputSource 是 WebXR API 中的一个重要接口，用于表示与 XR（扩展现实）设备交互的输入设备，例如手柄、手套或其他输入设备。通过 XRInputSource，开发者可以获取关于输入设备的状态和位置的信息，从而创建沉浸式的虚拟现实（VR）和增强现实（AR）体验。

## 文档
### 目的
XRInputSource 主要用于访问与 XR 会话相关的输入设备的信息，帮助开发者处理用户输入，并实现与虚拟环境的交互。

### 用法
XRInputSource 对象通常在 XR 会话的 `session.inputSources` 属性中找到。每个输入源都包含有关设备的属性，例如设备类型、输入状态、以及与用户交互的位置和方向等信息。

### 详细信息
- **属性**:
  - `deviceId`: 唯一标识输入设备的字符串。
  - `handedness`: 设备的使用方式，例如左手或右手。
  - `targetRaySpace`: 与 XR 空间的关系，通常用于表示用户的目标方向。
  - `gripSpace`: 表示设备的握持空间，通常用于手柄或其他控制器。
  - `profiles`: 设备支持的输入配置文件数组，提供了设备功能的详细信息。

### 方法
XRInputSource 主要是一个数据结构，通常不包含方法，但开发者可以通过其属性获取实时的输入状态。

## 示例
以下是使用 XRInputSource 的基本示例：

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSource = event.inputSource;
        console.log('用户选择了输入源:', inputSource.deviceId);
    });

    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach((inputSource) => {
            console.log('新输入源添加:', inputSource);
        });
    });
});
```

## 解释
在使用 XRInputSource 时，有几个常见的注意事项：
- **设备兼容性**: 并非所有设备都支持所有属性。开发者应检查设备的支持情况。
- **事件监听**: 需要正确注册事件监听器，以确保输入事件被捕获。
- **会话状态**: 确保在有效的 XR 会话中使用输入源，否则可能获取失败或返回空值。

## 一句话总结
XRInputSource 是用于获取与 XR 设备交互的输入信息的接口，帮助开发者实现丰富的用户体验。