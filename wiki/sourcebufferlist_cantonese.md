<!--
Meta Description: # SourceBufferList：JavaScript 中的多媒體緩衝區管理 ## 概述 SourceBufferList 是 Web API 中的一個重要組件，專門用於管理 Media Source Extensions (MSE) 中的多媒體緩衝區。它允許開發者在網頁上動態地添加、刪除和管理...
Meta Keywords: sourcebuffer, sourcebufferlist, mediasource, const, javascript
-->

# SourceBufferList：JavaScript 中的多媒體緩衝區管理

## 概述
SourceBufferList 是 Web API 中的一個重要組件，專門用於管理 Media Source Extensions (MSE) 中的多媒體緩衝區。它允許開發者在網頁上動態地添加、刪除和管理音頻和視頻數據的緩衝。

## 文檔
### 目的
SourceBufferList 是一個集合，包含了多個 SourceBuffer 對象。這些緩衝區可用於處理媒體流，特別是在需要動態加載多媒體內容的情況下。通過 SourceBufferList，開發者可以有效地管理多個媒體來源的緩衝區。

### 用法
要使用 SourceBufferList，您首先需要創建一個 MediaSource 對象，然後透過它來創建 SourceBuffer。當多個 SourceBuffer 被創建後，它們將自動添加到 SourceBufferList 中。

```javascript
const mediaSource = new MediaSource();
const sourceBufferList = mediaSource.sourceBuffers; // 這就是 SourceBufferList
```

### 詳細信息
- **屬性**:
  - `length`: 返回 SourceBufferList 中 SourceBuffer 的數量。
  
- **方法**:
  - `add(SourceBuffer)`: 將一個新的 SourceBuffer 添加到列表中。
  - `remove(SourceBuffer)`: 從列表中刪除指定的 SourceBuffer。

## 示例
### 基本用法示例
以下是創建 MediaSource 並添加 SourceBuffer 的基本示範：

```javascript
const mediaSource = new MediaSource();
const videoElement = document.querySelector('video');

videoElement.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener('sourceopen', function() {
    const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8, vorbis"');
    // 在此處可以進行數據添加
});
```

## 解釋
### 常見陷阱
1. **緩衝區狀態**: 確保在添加數據到 SourceBuffer 之前，SourceBuffer 的狀態為 `open`，否則會導致錯誤。
2. **數據格式**: 使用 SourceBuffer 時，必須確保添加的數據格式與創建 SourceBuffer 時指定的編解碼器相符。
3. **異步操作**: 在多個 SourceBuffer 之間進行操作時要注意異步性，避免因操作順序錯誤而導致的問題。

## 一句話總結
SourceBufferList 是管理多個 SourceBuffer 的集合，為 JavaScript 提供了靈活的多媒體緩衝區處理功能。