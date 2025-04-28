<!--
Meta Description: # onappinstalled：JavaScript 中的應用安裝事件 ## 概述 `onappinstalled` 是一個與 Progressive Web Apps (PWA) 相關的事件，當應用程序被安裝到用戶設備上時觸發。這個事件提供了一種方式，讓開發者能夠執行特定的操作，例如更新 UI ...
Meta Keywords: onappinstalled, event, javascript, addeventlistener, console
-->

# onappinstalled：JavaScript 中的應用安裝事件

## 概述
`onappinstalled` 是一個與 Progressive Web Apps (PWA) 相關的事件，當應用程序被安裝到用戶設備上時觸發。這個事件提供了一種方式，讓開發者能夠執行特定的操作，例如更新 UI 或發送分析數據。

## 文檔
### 目的
`onappinstalled` 事件的主要目的是讓開發者能夠在 PWA 被安裝後執行自定義邏輯。這可以用於通知用戶應用已安裝，或進行某些初始化操作。

### 使用方法
在 JavaScript 中，`onappinstalled` 事件通常與 `beforeinstallprompt` 事件結合使用，以便在用戶安裝應用時做出反應。以下是事件的基本用法：

```javascript
window.addEventListener('appinstalled', (event) => {
    console.log('應用已成功安裝!');
    // 可以在這裡執行其他操作，例如更新 UI
});
```

### 詳細信息
- **事件類型**：`Event`
- **觸發時機**：當用戶成功安裝 PWA 時。
- **支援的瀏覽器**：目前大部分現代瀏覽器都支援此事件，但具體的行為可能會有所不同。

## 示例
以下是使用 `onappinstalled` 事件的基本示例：

```javascript
if ('serviceWorker' in navigator) {
    window.addEventListener('beforeinstallprompt', (event) => {
        event.preventDefault(); // 防止瀏覽器自動顯示安裝提示
        // 儲存事件以便將來使用
        deferredPrompt = event;
        
        // 當用戶點擊安裝按鈕時
        installButton.addEventListener('click', () => {
            deferredPrompt.prompt();  // 顯示安裝提示
            deferredPrompt.userChoice.then((choiceResult) => {
                if (choiceResult.outcome === 'accepted') {
                    console.log('用戶接受了安裝');
                } else {
                    console.log('用戶拒絕了安裝');
                }
            });
        });
    });

    window.addEventListener('appinstalled', (event) => {
        console.log('應用已成功安裝!');
        // 在安裝後執行其他操作
    });
}
```

## 解釋
在使用 `onappinstalled` 事件時，有幾個常見的陷阱需要注意：
- **事件順序**：確保正確的事件順序，`beforeinstallprompt` 必須在 `appinstalled` 之前處理。
- **瀏覽器支持**：不同瀏覽器的支持程度可能不同，建議在開發時進行兼容性測試。
- **用戶體驗**：在用戶安裝應用後，提供清晰的反饋和後續操作指導，以提高用戶體驗。

## 一句總結
`onappinstalled` 事件允許開發者在 Progressive Web App 被成功安裝後執行自定義操作，提升用戶體驗。