<!--
Meta Description: # EyeDropper：JavaScript 的顏色取樣器 API ## 概述 EyeDropper 是一個 JavaScript API，允許開發者從用戶的螢幕上取樣顏色，並獲取該顏色的 RGB 或 HEX 值。這個功能對於需要顏色選擇或調色板功能的應用程序非常有用。 ## 文件說明 EyeDr...
Meta Keywords: eyedropper, api, javascript, open, hex
-->

# EyeDropper：JavaScript 的顏色取樣器 API

## 概述
EyeDropper 是一個 JavaScript API，允許開發者從用戶的螢幕上取樣顏色，並獲取該顏色的 RGB 或 HEX 值。這個功能對於需要顏色選擇或調色板功能的應用程序非常有用。

## 文件說明
EyeDropper API 的主要目的是提供一種直觀的方式來選擇顏色。用戶可以啟動 EyeDropper 工具，然後使用鼠標選擇螢幕上的顏色。

### 用法
要使用 EyeDropper API，首先需要創建一個 EyeDropper 的實例，然後調用 `open` 方法來啟動顏色選擇器。

```javascript
const eyeDropper = new EyeDropper();
eyeDropper.open()
  .then(result => {
      console.log(result.sRGBHex); // 獲取選擇顏色的 HEX 值
  })
  .catch(err => {
      console.error(err); // 處理錯誤
  });
```

### 參數
- `open()`：這是一個返回 Promise 的方法，當用戶選擇顏色後，該 Promise 會解析為一個包含顏色資訊的對象。

### 返回的對象
- `sRGBHex`：所選顏色的 HEX 格式字符串。

## 示例
以下是使用 EyeDropper API 的基本示例：

```javascript
// 創建 EyeDropper 實例
const eyeDropper = new EyeDropper();

// 啟動顏色選擇器
eyeDropper.open()
  .then(result => {
      // 輸出選擇的顏色
      console.log(`選擇的顏色是：${result.sRGBHex}`);
  })
  .catch(err => {
      console.error('發生錯誤：', err);
  });
```

## 解釋
使用 EyeDropper API 時，需要注意以下幾點：

1. 兼容性：EyeDropper API 目前僅在某些現代瀏覽器中受支持，如 Chrome 和 Edge。請先確認用戶的瀏覽器版本。
2. 安全性：使用 EyeDropper API 時，必須在安全環境中（例如 HTTPS）運行，否則將無法調用。
3. 用戶交互：在調用 `open` 方法後，必須等待用戶進行顏色選擇，這意味著該方法只能在用戶交互事件（如按鈕點擊）中調用。

## 一句總結
EyeDropper 是一個方便的 JavaScript API，允許用戶從螢幕上選擇顏色並獲取其 HEX 值。