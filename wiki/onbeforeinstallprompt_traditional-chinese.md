<!--
Meta Description: # onbeforeinstallprompt：JavaScript 中的安裝提示事件 ## 摘要 `onbeforeinstallprompt` 是一個 JavaScript 事件，用於在 PWA（進階網頁應用程式）安裝之前，允許開發者控制安裝提示的顯示時機，從而改善用戶體驗。 ## 文檔 `on...
Meta Keywords: onbeforeinstallprompt, deferredprompt, pwa, prompt, installbutton
-->

# onbeforeinstallprompt：JavaScript 中的安裝提示事件

## 摘要
`onbeforeinstallprompt` 是一個 JavaScript 事件，用於在 PWA（進階網頁應用程式）安裝之前，允許開發者控制安裝提示的顯示時機，從而改善用戶體驗。

## 文檔
`onbeforeinstallprompt` 事件在瀏覽器檢測到網頁可以被安裝為 PWA 時觸發。開發者可以通過監聽此事件，阻止默認的安裝提示顯示，並在希望的時候顯示自定義提示。

### 目的
此事件的主要目的是讓開發者在用戶訪問網站時，根據用戶的互動或其他條件來決定何時顯示安裝提示，從而提高用戶的安裝意願。

### 使用方法
要使用 `onbeforeinstallprompt` 事件，開發者需要添加事件監聽器，並在事件觸發時調用相應的函數。以下是基本的使用步驟：

1. 監聽 `beforeinstallprompt` 事件。
2. 阻止默認行為以防止自動顯示安裝提示。
3. 在適合的時機，通過使用 `prompt()` 方法顯示安裝提示。

### 詳細信息
- 事件類型：`Event`
- 事件屬性：
  - `prompt()`：顯示安裝提示。
  - `userChoice`：返回一個 Promise，表示用戶的選擇結果。

## 示例
以下是簡單的使用範例：

```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
    // 阻止瀏覽器自動顯示安裝提示
    e.preventDefault();
    // 儲存事件以便稍後使用
    deferredPrompt = e;
    // 顯示自定義安裝提示
    showInstallPrompt();
});

// 觸發安裝提示的函數
function showInstallPrompt() {
    const installButton = document.getElementById('install-button');
    installButton.style.display = 'block';

    installButton.addEventListener('click', async () => {
        // 顯示安裝提示
        deferredPrompt.prompt();
        // 等待用戶的選擇
        const choiceResult = await deferredPrompt.userChoice;

        if (choiceResult.outcome === 'accepted') {
            console.log('用戶接受了安裝提示');
        } else {
            console.log('用戶拒絕了安裝提示');
        }

        // 重置
        deferredPrompt = null;
        installButton.style.display = 'none';
    });
}
```

## 解釋
### 常見問題與注意事項
- **事件未觸發**：若 `onbeforeinstallprompt` 事件未觸發，請確認網站符合 PWA 的所有要求，包括 HTTPS、manifest.json 文件等。
- **多次顯示**：`prompt()` 方法只能被調用一次，若用戶拒絕安裝，`deferredPrompt` 將無法再次使用。
- **用戶體驗**：在選擇何時顯示安裝提示時，考慮用戶的互動行為，如點擊按鈕或完成某個任務，以提高接受率。

## 一句總結
`onbeforeinstallprompt` 事件允許開發者控制 PWA 安裝提示的顯示時機，從而優化用戶體驗。