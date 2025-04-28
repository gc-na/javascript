<!--
Meta Description: # onbeforeinstallprompt：JavaScript 的安裝提示事件 ## 概述 `onbeforeinstallprompt` 是一個 JavaScript 事件，用於在用戶訪問支援漸進式網絡應用程式 (PWA) 的網站時，控制安裝提示的顯示。這個事件使開發者能夠自定義何時顯示安裝...
Meta Keywords: onbeforeinstallprompt, deferredprompt, javascript, pwa, prompt
-->

# onbeforeinstallprompt：JavaScript 的安裝提示事件

## 概述
`onbeforeinstallprompt` 是一個 JavaScript 事件，用於在用戶訪問支援漸進式網絡應用程式 (PWA) 的網站時，控制安裝提示的顯示。這個事件使開發者能夠自定義何時顯示安裝提示，從而提升用戶體驗。

## 文檔
### 目的
`onbeforeinstallprompt` 事件的主要目的是在用戶瀏覽器準備顯示 PWA 安裝提示之前，讓開發者有機會進行一些自定義的操作，例如顯示自定義提示或收集用戶的反饋。

### 使用方法
要使用 `onbeforeinstallprompt` 事件，開發者需要在 JavaScript 中為 `window` 對象添加事件監聽器。當事件觸發時，開發者可以調用 `prompt()` 方法來顯示安裝提示。

### 詳細信息
1. **事件監聽器**：通過 `window.addEventListener` 方法來監聽 `beforeinstallprompt` 事件。
2. **事件對象**：事件對象包含一個 `prompt()` 方法，開發者可以調用此方法來顯示安裝提示。
3. **防止自動顯示**：在事件被觸發時，瀏覽器不會自動顯示提示，開發者必須手動調用 `prompt()`。

## 範例
以下是使用 `onbeforeinstallprompt` 的基本範例：

```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
    // 防止瀏覽器自動顯示提示
    e.preventDefault();
    // 儲存事件，以便稍後使用
    deferredPrompt = e;
    
    // 顯示自定義的安裝提示按鈕
    const installButton = document.getElementById('installButton');
    installButton.style.display = 'block';

    installButton.addEventListener('click', () => {
        // 顯示安裝提示
        deferredPrompt.prompt();
        // 等待用戶響應
        deferredPrompt.userChoice.then((choiceResult) => {
            if (choiceResult.outcome === 'accepted') {
                console.log('用戶接受了安裝提示');
            } else {
                console.log('用戶拒絕了安裝提示');
            }
            deferredPrompt = null;
        });
    });
});
```

## 解釋
### 常見問題
1. **事件不觸發**：確保你的網站符合 PWA 標準，並且在 HTTPS 環境下運行。
2. **用戶選擇**：用戶可能會拒絕安裝提示，因此開發者應提供清晰的安裝理由和好處。
3. **瀏覽器兼容性**：並非所有瀏覽器都支援 `onbeforeinstallprompt`，開發者應檢查目標用戶的瀏覽器環境。

### 附加注意事項
- 開發者應避免過於頻繁地顯示安裝提示，以免影響用戶體驗。
- 在提示前，提供足夠的信息讓用戶理解為何要安裝應用。

## 簡短總結
`onbeforeinstallprompt` 事件為開發者提供了控制 PWA 安裝提示顯示的能力，從而改善用戶體驗。