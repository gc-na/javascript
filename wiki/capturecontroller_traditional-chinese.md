<!--
Meta Description: # CaptureController：JavaScript 中的捕獲控制器 ## 簡介 CaptureController 是一個前端 API，專門用於管理媒體捕獲過程，如音頻和視頻流，並可用於處理多個媒體設備的輸入。這個功能對於開發需要即時捕獲和處理媒體內容的應用程式來說非常重要。 ## 文檔 ...
Meta Keywords: capturecontroller, controller, javascript, event, const
-->

# CaptureController：JavaScript 中的捕獲控制器

## 簡介
CaptureController 是一個前端 API，專門用於管理媒體捕獲過程，如音頻和視頻流，並可用於處理多個媒體設備的輸入。這個功能對於開發需要即時捕獲和處理媒體內容的應用程式來說非常重要。

## 文檔
### 目的
CaptureController 的主要目的是提供一個一致的界面來控制多個媒體設備的捕獲過程。它允許開發者在同一應用中管理不同的音頻和視頻流，並能夠輕鬆地啟用或禁用特定的捕獲媒體。

### 用法
使用 CaptureController 之前，開發者需要先創建一個 CaptureController 實例，然後指定要捕獲的媒體類型。接下來，可以使用各種方法來啟動或停止捕獲，以及獲取捕獲的媒體流。

#### 基本語法
```javascript
const controller = new CaptureController();
```

### 詳細說明
- **屬性**:
  - `mediaStreams`: 返回當前捕獲的媒體流列表。
  
- **方法**:
  - `start()`: 開始捕獲指定的媒體。
  - `stop()`: 停止捕獲當前的媒體。
  - `getStreams()`: 獲取當前捕獲的媒體流。

### 事件
CaptureController 還支持多種事件，例如 `streamadded` 和 `streamremoved`，用於監聽媒體流的添加和刪除。

## 範例
### 基本使用範例
```javascript
const controller = new CaptureController();

// 開始捕獲音頻和視頻流
controller.start();

// 停止捕獲
controller.stop();

// 獲取當前的媒體流
const streams = controller.getStreams();
console.log(streams);
```

### 事件監聽範例
```javascript
controller.addEventListener('streamadded', (event) => {
  console.log('新媒體流已添加:', event.stream);
});

controller.addEventListener('streamremoved', (event) => {
  console.log('媒體流已移除:', event.stream);
});
```

## 解釋
### 常見陷阱
1. **權限問題**: 使用 CaptureController 時，確保用戶授予了相應的媒體捕獲權限，否則將無法正常捕獲媒體流。
2. **瀏覽器支持**: CaptureController 目前可能並非所有瀏覽器都支持，使用前需檢查兼容性。
3. **異步處理**: 捕獲過程是異步的，開發者需合理處理 Promise 及其返回的結果，避免出現錯誤。

## 總結
CaptureController 是一個強大的工具，用於在 JavaScript 中管理媒體捕獲過程，能有效提升應用的媒體處理能力。