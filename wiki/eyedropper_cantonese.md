<!--
Meta Description: # EyeDropper: JavaScript 中的顏色選擇工具 ## 概要 EyeDropper 是一個 JavaScript API，允許網頁應用程式以直觀的方式從用戶的屏幕上選取顏色。這使得開發者能夠提供更佳的用戶體驗，讓用戶輕鬆選擇所需的顏色。 ## 文檔 ### 目的 EyeDroppe...
Meta Keywords: eyedropper, api, javascript, result, open
-->

# EyeDropper: JavaScript 中的顏色選擇工具

## 概要
EyeDropper 是一個 JavaScript API，允許網頁應用程式以直觀的方式從用戶的屏幕上選取顏色。這使得開發者能夠提供更佳的用戶體驗，讓用戶輕鬆選擇所需的顏色。

## 文檔
### 目的
EyeDropper API 的主要目的是提供一個簡單的方法來捕捉用戶屏幕上的顏色，並將其轉換為可在應用程式中使用的顏色值。這對於設計工具、調色板和其他與顏色相關的應用程式特別有用。

### 使用方法
使用 EyeDropper API 的基本步驟如下：

1. **創建 EyeDropper 實例**  
   首先，你需要創建一個 EyeDropper 的實例：
   ```javascript
   const eyeDropper = new EyeDropper();
   ```

2. **啟動顏色選擇**  
   使用 `open` 方法來啟動顏色選擇器。這是一個異步方法，返回一個 Promise。
   ```javascript
   eyeDropper.open().then(result => {
       console.log(result.sRGBHex); // 輸出選擇的顏色
   }).catch(err => {
       console.error(err); // 處理錯誤
   });
   ```

### 詳細信息
- EyeDropper API 僅在支持的瀏覽器中可用，並且需要 HTTPS 環境。
- 使用者必須授予權限才能訪問其屏幕內容。
- 這個 API 主要用於增強用戶交互，並在設計相關的應用中非常有價值。

## 範例
### 基本使用範例
以下是一個簡單的範例，展示如何在網頁中使用 EyeDropper API。

```html
<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>顏色選擇範例</title>
</head>
<body>
    <button id="pickColor">選擇顏色</button>
    <script>
        document.getElementById('pickColor').addEventListener('click', () => {
            const eyeDropper = new EyeDropper();
            eyeDropper.open().then(result => {
                document.body.style.backgroundColor = result.sRGBHex;
                console.log(`選擇的顏色是: ${result.sRGBHex}`);
            }).catch(err => {
                console.error('無法選擇顏色:', err);
            });
        });
    </script>
</body>
</html>
```

## 解釋
### 常見問題
- **不支持的瀏覽器**：不是所有的瀏覽器都支持 EyeDropper API，因此在使用前應該確認兼容性。
- **權限問題**：用戶必須允許網站訪問其屏幕，否則將無法使用這個功能。
- **異步處理**：`open` 方法是異步的，因此需要使用 Promise 處理結果。

## 一句總結
EyeDropper API 是一個強大的工具，能夠讓用戶在 JavaScript 應用中輕鬆選擇顏色，提升使用體驗。