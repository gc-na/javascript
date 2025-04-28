<!--
Meta Description: # SourceBufferList - JavaScript 中的源缓冲列表 ## 概述 `SourceBufferList` 是 Web API 中的一个接口，主要用于处理媒体流中的多个 `SourceBuffer` 对象。它通常与 `MediaSource` 接口一起使用，允许开发者以更灵活的...
Meta Keywords: sourcebuffer, sourcebufferlist, mediasource, sourcebuffers, const
-->

# SourceBufferList - JavaScript 中的源缓冲列表

## 概述
`SourceBufferList` 是 Web API 中的一个接口，主要用于处理媒体流中的多个 `SourceBuffer` 对象。它通常与 `MediaSource` 接口一起使用，允许开发者以更灵活的方式管理多媒体内容的缓冲。

## 文档
### 目的
`SourceBufferList` 提供了一种方法来访问和管理与 `MediaSource` 关联的多个 `SourceBuffer` 对象。它允许开发者对音频和视频数据的缓冲进行高效控制，尤其是在处理动态内容时。

### 用法
`SourceBufferList` 是一个只读属性，返回一个 `SourceBuffer` 对象的集合。可以通过 `MediaSource.sourceBuffers` 属性访问它。开发者可以使用 `SourceBufferList` 来遍历所有的 `SourceBuffer`，并对其进行操作。

### 细节
- **创建**: `SourceBufferList` 是通过 `MediaSource` 的 `sourceBuffers` 属性创建的，不能直接实例化。
- **属性**:
  - `length`: 返回 `SourceBuffer` 的数量。
- **方法**:
  - `item(index)`: 返回指定索引位置的 `SourceBuffer` 对象。

## 示例
### 基本用法
```javascript
// 创建 MediaSource 对象
const mediaSource = new MediaSource();
const sourceBufferList = mediaSource.sourceBuffers;

// 添加 SourceBuffer
const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.64001E, mp4a.40.2"');

// 遍历 SourceBufferList
for (let i = 0; i < sourceBufferList.length; i++) {
    console.log(sourceBufferList.item(i)); // 输出每个 SourceBuffer
}
```

## 解释
### 常见陷阱与注意事项
1. **只读属性**: `SourceBufferList` 是只读的，不能添加或删除 `SourceBuffer`。你需要通过 `MediaSource.addSourceBuffer()` 方法来管理 `SourceBuffer`。
2. **同步问题**: 在访问 `SourceBufferList` 时，确保所有 `SourceBuffer` 都已添加并且处于有效状态，否则可能会导致未定义行为。
3. **格式兼容性**: 确保添加的 `SourceBuffer` 支持所需的媒体格式，否则可能无法正常播放。

## 一句话总结
`SourceBufferList` 是一个用于管理和访问多个 `SourceBuffer` 的接口，提供对动态媒体流的高效控制。