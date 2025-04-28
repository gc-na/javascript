<!--
Meta Description: # onsecuritypolicyviolation：JavaScript中的安全政策違反事件 ## 簡介 `onsecuritypolicyviolation` 是一個用於監控和處理安全政策違反事件的 JavaScript 事件，主要用於加強網站的安全性。當瀏覽器檢測到不符合內容安全政策（CSP...
Meta Keywords: onsecuritypolicyviolation, script, document, event, html
-->

# onsecuritypolicyviolation：JavaScript中的安全政策違反事件

## 簡介
`onsecuritypolicyviolation` 是一個用於監控和處理安全政策違反事件的 JavaScript 事件，主要用於加強網站的安全性。當瀏覽器檢測到不符合內容安全政策（CSP）的行為時，會觸發此事件。

## 文檔
### 目的
`onsecuritypolicyviolation` 事件的主要目的是提供一種機制，讓開發者能夠捕獲和處理因違反內容安全政策而發生的事件。這樣可以幫助發現潛在的安全問題，並加強應用程序的安全性。

### 使用方法
你可以通過在 DOM 元素上添加事件監聽器來使用 `onsecuritypolicyviolation` 事件。此事件在違反安全政策時自動觸發，並傳遞一個包含詳細信息的事件對象。

```javascript
document.addEventListener('securitypolicyviolation', function(event) {
    console.log('安全政策違反:', event);
});
```

### 詳細信息
- **事件對象**: 事件對象包含以下屬性：
  - `blockedURI`: 被阻止資源的 URI。
  - `effectiveDirective`: 觸發違反的有效指令。
  - `originalPolicy`: 當前的內容安全政策。
  - `sourceFile`: 觸發事件的源文件。
  - `lineNumber`: 源文件中的行號。
  
這些信息可以幫助開發者診斷問題並修正相應的 CSP 設置。

## 示例
### 基本用法
以下是一個簡單的示例，展示如何使用 `onsecuritypolicyviolation` 事件：

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <title>安全政策違反範例</title>
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'none';">
</head>
<body>
    <script>
        document.addEventListener('securitypolicyviolation', function(event) {
            console.log('安全政策違反:', event.blockedURI);
        });

        // 嘗試加載被阻止的腳本
        var script = document.createElement('script');
        script.src = 'http://example.com/unauthorized.js';
        document.body.appendChild(script);
    </script>
</body>
</html>
```

在這個示例中，當嘗試加載未經授權的腳本時，將觸發 `onsecuritypolicyviolation` 事件，並在控制台中顯示相應的違反信息。

## 解釋
### 常見陷阱
- **未正確設置 CSP**: 如果未設置或設置錯誤的內容安全政策，將無法正確捕獲違反事件。
- **事件處理程序未註冊**: 確保在觸發事件之前已經註冊事件處理程序，否則將無法捕獲到事件。

### 額外注意事項
- 確保在應用程序中適當處理這些事件，以便能夠快速應對潛在的安全威脅。

## 簡單總結
`onsecuritypolicyviolation` 事件用於監控和處理安全政策違反，幫助開發者增強網站的安全性。