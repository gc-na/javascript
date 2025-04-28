<!--
Meta Description: # SourceBufferList：JavaScript 中的媒體緩衝區管理 ## 概述 `SourceBufferList` 是 Web API 中的一個接口，用於處理多個 `SourceBuffer` 物件的集合，這些物件通常與媒體串流（如音頻或視頻）有關。它使開發者能夠更有效地管理和操作媒體...
Meta Keywords: mediasource, sourcebufferlist, sourcebuffer, const, javascript
-->

# SourceBufferList：JavaScript 中的媒體緩衝區管理

## 概述
`SourceBufferList` 是 Web API 中的一個接口，用於處理多個 `SourceBuffer` 物件的集合，這些物件通常與媒體串流（如音頻或視頻）有關。它使開發者能夠更有效地管理和操作媒體資料的緩衝。

## 文檔
### 目的
`SourceBufferList` 主要用於在媒體播放過程中管理多個 `SourceBuffer`，它為媒體串流提供了更好的控制，特別是在處理多媒體格式時。

### 使用方法
`SourceBufferList` 是由 `MediaSource` 物件的 `sourceBuffers` 屬性返回的，這是一個 `SourceBuffer` 物件的集合。開發者通常會透過以下方式使用它：

1. 創建一個 `MediaSource` 物件。
2. 使用 `addSourceBuffer` 方法將一個或多個 `SourceBuffer` 加入到 `MediaSource` 。
3. 透過 `sourceBuffers` 屬性訪問 `SourceBufferList`，並對其進行操作。

### 詳細信息
- `SourceBufferList` 提供了一個類陣列（Array-like）對象，允許你通過索引訪問每個 `SourceBuffer`。
- 它的主要屬性和方法包括：
  - `length`：返回 `SourceBuffer` 的數量。
  - `item(index)`：返回指定索引的 `SourceBuffer`。
  - `forEach(callback)`：對 `SourceBufferList` 中的每個 `SourceBuffer` 執行指定的回調函數。

## 示例
以下是使用 `SourceBufferList` 的基本範例：

```javascript
// 創建 MediaSource 物件
const mediaSource = new MediaSource();
const videoElement = document.querySelector('video');

// 當 MediaSource 可用時
mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer1 = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E, mp4a.40.2"');
    const sourceBuffer2 = mediaSource.addSourceBuffer('audio/mp4; codecs="mp4a.40.2"');

    const sourceBufferList = mediaSource.sourceBuffers;

    // 使用 forEach 遍歷 SourceBufferList
    sourceBufferList.forEach((buffer) => {
        console.log(buffer);
    });
});

// 將 MediaSource 設置為視頻元素
videoElement.src = URL.createObjectURL(mediaSource);
```

## 解釋
在使用 `SourceBufferList` 時，開發者應注意以下幾點：
- `SourceBuffer` 需要在 `MediaSource` 的 `sourceopen` 事件發生後才可以被添加，否則會引發錯誤。
- 不同的 `SourceBuffer` 之間的資料流必須彼此獨立，以避免競爭條件。
- 當對 `SourceBuffer` 進行操作時，必須小心處理緩衝區的狀態，以防止數據丟失或播放中斷。

## 總結
`SourceBufferList` 是一個強大的工具，能夠幫助開發者在 JavaScript 中有效地管理與媒體串流相關的多個緩衝區。