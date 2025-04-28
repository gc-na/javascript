<!--
Meta Description: # MediaDevices：JavaScript 中的多媒體設備訪問 ## 概述 MediaDevices 是一個 Web API，允許開發者訪問用戶的媒體設備，例如攝像頭和麥克風。這個 API 主要用於實現音視頻通話、錄製和其他多媒體功能。 ## 文檔 ### 目的 MediaDevices A...
Meta Keywords: mediadevices, error, getusermedia, api, navigator
-->

# MediaDevices：JavaScript 中的多媒體設備訪問

## 概述
MediaDevices 是一個 Web API，允許開發者訪問用戶的媒體設備，例如攝像頭和麥克風。這個 API 主要用於實現音視頻通話、錄製和其他多媒體功能。

## 文檔
### 目的
MediaDevices API 旨在提供一種簡單的方式來獲取用戶設備的媒體流，從而支持各種多媒體應用程序的開發。

### 使用方法
要使用 MediaDevices API，首先需要調用 `navigator.mediaDevices`，然後可以使用 `getUserMedia()` 方法來請求訪問用戶的媒體設備。

### 詳細說明
- **navigator.mediaDevices**: 這是一個代表用戶媒體設備的對象，提供了多種方法來訪問這些設備。
- **getUserMedia(constraints)**: 此方法接收一個約束對象，指定要訪問的媒體類型（音頻或視頻）。如果用戶授權訪問，返回一個 Promise，解析為包含媒體流的 MediaStream 對象。
  
  ```javascript
  navigator.mediaDevices.getUserMedia({ video: true, audio: true })
      .then(stream => {
          // 使用媒體流
      })
      .catch(error => {
          console.error("獲取媒體流失敗:", error);
      });
  ```

## 範例
### 獲取攝像頭和麥克風的媒體流
```javascript
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        const videoElement = document.querySelector('video');
        videoElement.srcObject = stream;
        videoElement.play();
    })
    .catch(error => {
        console.error("獲取媒體流失敗:", error);
    });
```

### 僅獲取視頻流
```javascript
navigator.mediaDevices.getUserMedia({ video: true })
    .then(stream => {
        // 處理視頻流
    })
    .catch(error => {
        console.error("獲取視頻流失敗:", error);
    });
```

## 解釋
### 常見陷阱
- **用戶授權**: 確保在調用 `getUserMedia()` 時，使用 HTTPS 協議，因為大多數瀏覽器不允許在不安全的上下文中訪問媒體設備。
- **錯誤處理**: 始終處理 Promise 的拒絕情況，這樣可以捕捉用戶拒絕授權或設備不可用的情況。

### 附加注意事項
- `getUserMedia()` 方法的約束對象可以包含更複雜的設置，如解析度或幀率。
- 若要在不同的設備上測試，請確保設備連接正常，且有正確的驅動程式。

## 一句話總結
MediaDevices API 提供了一個簡便的方式來訪問用戶的多媒體設備，支持音視頻通話和錄製功能。