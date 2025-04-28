<!--
Meta Description: # SpeechSynthesisVoice：JavaScript语音合成的核心要素 ## 摘要 `SpeechSynthesisVoice` 是 Web Speech API 的一部分，用于表示可用于语音合成的声音。它包含有关每种声音的属性，例如名称、语言和声音的特性，允许开发者在应用中选择合适的...
Meta Keywords: speechsynthesisvoice, synth, getvoices, const, voices
-->

# SpeechSynthesisVoice：JavaScript语音合成的核心要素

## 摘要
`SpeechSynthesisVoice` 是 Web Speech API 的一部分，用于表示可用于语音合成的声音。它包含有关每种声音的属性，例如名称、语言和声音的特性，允许开发者在应用中选择合适的声音进行语音合成。

## 文档
### 目的
`SpeechSynthesisVoice` 旨在提供有关可用语音合成声音的信息，使开发者能够根据需要选择合适的声音，从而增强用户体验。

### 用法
`SpeechSynthesisVoice` 的实例通常通过 `SpeechSynthesis.getVoices()` 方法获取。此方法返回一个包含所有可用声音的数组，每个声音都是 `SpeechSynthesisVoice` 的实例。开发者可以使用这些声音来设置 `SpeechSynthesisUtterance` 的声音属性。

### 属性
- **name**: 声音的名称，通常是用户友好的描述。
- **lang**: 声音的语言代码，例如 "en-US" 表示美国英语。
- **default**: 一个布尔值，指示该声音是否为默认声音。
- **localService**: 一个布尔值，指示声音是否由本地服务提供。
- **voiceURI**: 声音的唯一标识符，通常用于在不同的浏览器或设备之间保持一致。

## 示例
以下是如何使用 `SpeechSynthesisVoice` 的基本示例：

```javascript
// 获取可用的语音
const synth = window.speechSynthesis;
let voices = [];

// 当声音列表加载完成后调用
synth.onvoiceschanged = () => {
    voices = synth.getVoices();
    // 选择一个声音
    const selectedVoice = voices.find(voice => voice.name === 'Google 普通话');
    
    // 创建语音合成实例
    const utterance = new SpeechSynthesisUtterance('你好，欢迎使用语音合成！');
    utterance.voice = selectedVoice;

    // 开始语音合成
    synth.speak(utterance);
};
```

## 解释
使用 `SpeechSynthesisVoice` 时，开发者常见的陷阱包括：
- **声音未加载**: `getVoices()` 方法可能在未加载声音列表时被调用，导致返回空数组。确保在 `onvoiceschanged` 事件中调用该方法。
- **浏览器兼容性**: 不同浏览器支持的声音可能不同，开发者应考虑为用户提供备选方案。
- **语言支持**: 选择的声音可能不支持指定的语言，确保选择的声音与要合成文字的语言相匹配。

## 一句话总结
`SpeechSynthesisVoice` 是 Web Speech API 中的一个接口，用于获取和描述可用的语音合成声音，有助于提升应用的语音交互能力。