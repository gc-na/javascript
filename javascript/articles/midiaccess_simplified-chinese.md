<!--
Meta Description: # MIDIAccess: JavaScript中的媒体访问接口 ## 概述 MIDIAccess是一个Web API，允许开发者通过JavaScript访问和控制MIDI设备。它提供了一种简便的方法来与MIDI硬件互动，使得开发音乐应用程序和其他基于MIDI的项目变得更加高效。 ## 文档 ###...
Meta Keywords: midiaccess, outputs, console, function, const
-->

# MIDIAccess: JavaScript中的媒体访问接口

## 概述
MIDIAccess是一个Web API，允许开发者通过JavaScript访问和控制MIDI设备。它提供了一种简便的方法来与MIDI硬件互动，使得开发音乐应用程序和其他基于MIDI的项目变得更加高效。

## 文档
### 目的
MIDIAccess接口的主要目的是提供对MIDI输入和输出设备的访问，允许开发者读取MIDI消息并发送MIDI信号，从而实现与音乐硬件的交互。

### 使用
要使用MIDIAccess接口，开发者需要通过`navigator.requestMIDIAccess()`方法请求对MIDI设备的访问。此方法返回一个`Promise`，解析为MIDIAccess对象。

### 详细信息
```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
  // 处理成功的MIDI访问
}

function onMIDIFailure() {
  console.error('无法访问MIDI设备');
}
```
- `onMIDISuccess`回调函数接收一个`MIDIAccess`对象，可以使用它来获取所有输入和输出设备。
- `onMIDIFailure`回调函数在请求失败时被调用。

## 示例
### 基本用法
以下是一个简单的示例，展示如何获取MIDI输入和输出设备的信息。

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
  const inputs = midiAccess.inputs;
  const outputs = midiAccess.outputs;

  console.log('可用的MIDI输入设备:');
  inputs.forEach(input => {
    console.log(input.name);
  });

  console.log('可用的MIDI输出设备:');
  outputs.forEach(output => {
    console.log(output.name);
  });
}, function() {
  console.error('无法访问MIDI设备');
});
```

### 发送MIDI信息
以下示例演示如何通过MIDI输出设备发送MIDI消息。

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
  const outputs = midiAccess.outputs;
  
  if (outputs.size > 0) {
    const output = outputs.values().next().value;
    const noteOnMessage = [0x90, 60, 0x7f]; // Note on, middle C, velocity 127
    output.send(noteOnMessage);
  }
});
```

## 说明
- **浏览器支持**：确保使用的浏览器支持Web MIDI API，主要的现代浏览器如Chrome和Edge支持该功能，但Firefox和Safari的支持可能有限。
- **权限问题**：用户必须允许网页访问MIDI设备。首次请求时会弹出权限提示。
- **设备连接**：MIDI设备需要正确连接并被系统识别，否则无法获取到MIDI输入或输出设备的信息。

## 一句话总结
MIDIAccess是一个强大的API，允许JavaScript开发者与MIDI设备进行交互，适用于音乐应用的开发。