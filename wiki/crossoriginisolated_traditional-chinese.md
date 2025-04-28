<!--
Meta Description: # JavaScript 中的 crossOriginIsolated：跨源隔離的概念 ## 概述 `crossOriginIsolated` 是一個屬性，用於檢查當前的 JavaScript 環境是否處於跨源隔離狀態。這一特性對於安全性和性能優化至關重要，特別是在涉及 WebAssembly 和 ...
Meta Keywords: crossoriginisolated, javascript, sharedarraybuffer, window, console
-->

# JavaScript 中的 crossOriginIsolated：跨源隔離的概念

## 概述
`crossOriginIsolated` 是一個屬性，用於檢查當前的 JavaScript 環境是否處於跨源隔離狀態。這一特性對於安全性和性能優化至關重要，特別是在涉及 WebAssembly 和 SharedArrayBuffer 等高效能計算時。

## 文檔
### 目的
`crossOriginIsolated` 屬性是 `Window` 物件的一部分，旨在確定當前頁面是否在跨源隔離的上下文中運行。若返回 `true`，表示頁面能夠安全地使用某些高性能 API，如 SharedArrayBuffer。

### 使用方式
要使用 `crossOriginIsolated`，只需直接訪問 `window.crossOriginIsolated` 屬性。這是一個只讀屬性，返回布林值。

```javascript
if (window.crossOriginIsolated) {
    console.log("當前環境是跨源隔離的");
} else {
    console.log("當前環境不是跨源隔離的");
}
```

### 詳細信息
- **跨源隔離的條件**：當文檔使用 `Cross-Origin-Embedder-Policy` 和 `Cross-Origin-Opener-Policy` HTTP 標頭正確配置時，頁面將被認為是跨源隔離的。
- **安全性**：跨源隔離能夠防止其他來源的文檔訪問或修改當前文檔的內容，從而增強安全性。
- **支持情況**：並非所有瀏覽器都支持這一屬性，開發者應當查閱相應的瀏覽器兼容性資料。

## 範例
以下是一些基本的使用範例：

### 範例 1：檢查跨源隔離狀態
```javascript
if (window.crossOriginIsolated) {
    alert("頁面在跨源隔離模式下運行。");
} else {
    alert("頁面未在跨源隔離模式下運行。");
}
```

### 範例 2：使用跨源隔離
```javascript
if (window.crossOriginIsolated) {
    // 安全使用 SharedArrayBuffer
    const sharedBuffer = new SharedArrayBuffer(1024);
    console.log("成功創建 SharedArrayBuffer");
} else {
    console.log("無法創建 SharedArrayBuffer，因為未在跨源隔離模式下運行");
}
```

## 解釋
- **常見問題**：開發者可能會錯誤地認為所有頁面都可以使用高級 API，而不考慮到跨源隔離的要求。必須正確設置 HTTP 標頭來啟用此功能。
- **注意事項**：在某些情況下，即使設置了正確的標頭，某些瀏覽器仍可能不支持該功能。建議在使用前進行充分的測試。

## 一句總結
`crossOriginIsolated` 是一個關鍵的 JavaScript 屬性，用於確定當前環境是否支持高性能 API，增強安全性。