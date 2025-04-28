<!--
Meta Description: # SpeechSynthesisUtterance：JavaScript中的语音合成发声对象 ## 概述 `SpeechSynthesisUtterance` 是 Web Speech API 中的一个接口，允许开发者通过 JavaScript 创建和控制语音合成的文本发声。 ## 文档 `Spe...
Meta Keywords: utterance, speechsynthesisutterance, javascript, const, window
-->

# SpeechSynthesisUtterance：JavaScript中的语音合成发声对象

## 概述
`SpeechSynthesisUtterance` 是 Web Speech API 中的一个接口，允许开发者通过 JavaScript 创建和控制语音合成的文本发声。

## 文档
`SpeechSynthesisUtterance` 是用于表示要被语音合成引擎发声的文本内容的对象。开发者可以通过这个对象设置要合成的文本、发音、音调、速率等属性。

### 目的
该接口的主要目的是提供一种简单的方法来生成计算机语音，以增强用户体验，特别是在无障碍应用程序和教育软件中。

### 用法
创建 `SpeechSynthesisUtterance` 对象的基本步骤如下：

1. **创建实例**
   ```javascript
   const utterance = new SpeechSynthesisUtterance('你好，世界！');
   ```

2. **设置属性**
   ```javascript
   utterance.lang = 'zh-CN';  // 设置语言为中文
   utterance.pitch = 1;        // 设置音调
   utterance.rate = 1;         // 设置语速
   ```

3. **调用语音合成**
   ```javascript
   window.speechSynthesis.speak(utterance);
   ```

### 属性
- `text`：要合成的文本字符串。
- `lang`：语言代码，指定发音的语言。
- `pitch`：音调，范围通常在 0 到 2 之间。
- `rate`：语速，通常范围在 0.1 到 10 之间。
- `voice`：指定所使用的语音。

## 示例
### 基础用法
```javascript
const utterance = new SpeechSynthesisUtterance('欢迎使用语音合成！');
utterance.lang = 'zh-CN';
utterance.rate = 1;
window.speechSynthesis.speak(utterance);
```

### 选择不同的语音
```javascript
const utterance = new SpeechSynthesisUtterance('你好，今天的天气如何？');
const voices = window.speechSynthesis.getVoices();
utterance.voice = voices.find(voice => voice.name === 'Microsoft Zira Desktop'); // 根据名称选择语音
window.speechSynthesis.speak(utterance);
```

## 说明
- **常见问题**：某些浏览器可能不支持所有可用的声音。因此，在选择语音时，最好先调用 `getVoices()` 方法并检查可用的语音列表。
- **异步加载**：在某些情况下，语音可能尚未加载，建议在 `voiceschanged` 事件触发后再执行语音合成。
- **用户交互**：为了满足某些浏览器的安全要求，通常需要在用户交互（例如点击按钮）后发起语音合成。

## 一句话总结
`SpeechSynthesisUtterance` 是 JavaScript 中用于创建和控制语音合成文本发声的对象。