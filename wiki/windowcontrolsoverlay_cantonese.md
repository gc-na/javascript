<!--
Meta Description: # WindowControlsOverlay：JavaScript 中的窗口控制覆蓋層 ## 簡介 `WindowControlsOverlay` 是一個 JavaScript API，旨在改善 Web 應用程序的窗口控制設計。它允許開發者自定義窗口的控制元素，提供更靈活的用戶介面體驗，特別是在全...
Meta Keywords: windowcontrolsoverlay, overlay, true, javascript, window
-->

# WindowControlsOverlay：JavaScript 中的窗口控制覆蓋層

## 簡介
`WindowControlsOverlay` 是一個 JavaScript API，旨在改善 Web 應用程序的窗口控制設計。它允許開發者自定義窗口的控制元素，提供更靈活的用戶介面體驗，特別是在全螢幕模式下。

## 文檔
`WindowControlsOverlay` 主要用於桌面應用程序和 PWA（漸進式 Web 應用程序），允許開發者控制和自定義窗口的標題欄和控制按鈕（例如最小化、最大化和關閉按鈕）。這個 API 提供了一個標準化的方法來使用和管理窗口控制，從而改善用戶體驗。

### 目的
- 提供在全螢幕模式下的窗口控制自定義。
- 使開發者能夠更好地設計與平台原生應用一致的用戶介面。

### 使用方法
要使用 `WindowControlsOverlay`，首先需要確保應用程序以全螢幕模式運行。然後可以通過以下方法進行控制：

```javascript
if ('WindowControlsOverlay' in window) {
    // 取得目前的 WindowControlsOverlay 實例
    const overlay = new WindowControlsOverlay();

    // 設定自定義的控制樣式
    overlay.setControls({
        close: true,
        minimize: true,
        maximize: true
    });

    // 啟用窗口控制覆蓋層
    overlay.enable();
}
```

## 示例
### 基本用法
以下是一個簡單的示例，展示如何啟用 `WindowControlsOverlay` 並自定義控制按鈕：

```javascript
if ('WindowControlsOverlay' in window) {
    const overlay = new WindowControlsOverlay();
    overlay.setControls({
        close: true,
        minimize: true,
        maximize: true
    });
    overlay.enable();
}
```

### 自定義樣式
開發者還可以通過 CSS 自定義窗口控制的樣式：

```css
:host {
    --overlay-background: rgba(0, 0, 0, 0.5);
}

window-controls-overlay {
    background-color: var(--overlay-background);
}
```

## 解釋
### 常見陷阱
- 確保應用程序已經進入全螢幕模式，否則 `WindowControlsOverlay` 將無法正常運作。
- 不同瀏覽器對 `WindowControlsOverlay` 的支持程度可能不同，開發者需做好兼容性測試。

### 注意事項
- 只有在 PWA 或桌面應用程式中，`WindowControlsOverlay` 功能才會完全發揮作用。
- 使用時需遵循最佳實踐，確保用戶介面的可用性和一致性。

## 一句總結
`WindowControlsOverlay` 允許開發者自定義全螢幕應用的窗口控制元素，提升用戶介面的靈活性和美觀度。