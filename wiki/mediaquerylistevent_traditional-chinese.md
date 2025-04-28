<!--
Meta Description: # MediaQueryListEvent 在 JavaScript 中的應用與使用指南 ## 簡介 MediaQueryListEvent 是一種特定的事件類型，用於監聽媒體查詢的變化。這使得開發者能夠根據不同的媒體狀態（如螢幕尺寸的變化）執行相應的行為，從而改善用戶體驗。 ## 文檔 ### 目...
Meta Keywords: mediaquerylistevent, mediaquerylist, event, javascript, matches
-->

# MediaQueryListEvent 在 JavaScript 中的應用與使用指南

## 簡介
MediaQueryListEvent 是一種特定的事件類型，用於監聽媒體查詢的變化。這使得開發者能夠根據不同的媒體狀態（如螢幕尺寸的變化）執行相應的行為，從而改善用戶體驗。

## 文檔
### 目的
MediaQueryListEvent 主要用於監控媒體查詢的變化，通過事件監聽器來響應這些變化，實現響應式設計。

### 使用方式
要使用 MediaQueryListEvent，開發者需首先創建一個 MediaQueryList 對象，然後可以向這個對象添加事件監聽器，監聽媒體查詢的變化。

#### 語法
```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');
mediaQueryList.addEventListener('change', (event) => {
    if (event.matches) {
        // 當螢幕寬度小於600px時的行為
    } else {
        // 當螢幕寬度大於600px時的行為
    }
});
```

### 事件屬性
- `matches`: 一個布林值，指示媒體查詢是否匹配當前的視口。
- `media`: 媒體查詢的字串，描述了該查詢的條件。

## 範例
### 基本範例
以下範例展示了如何使用 MediaQueryListEvent 來監聽螢幕大小變化：
```javascript
const mediaQueryList = window.matchMedia('(min-width: 800px)');

function handleMediaChange(event) {
    if (event.matches) {
        console.log('螢幕寬度大於800px');
    } else {
        console.log('螢幕寬度小於800px');
    }
}

// 添加事件監聽器
mediaQueryList.addEventListener('change', handleMediaChange);

// 初始化檢查
handleMediaChange(mediaQueryList);
```

## 解釋
在使用 MediaQueryListEvent 時，開發者應注意以下幾點：
1. **事件重複觸發**: 當媒體查詢條件發生變化時，事件會持續觸發，開發者需確保有效管理事件回調，以避免性能問題。
2. **瀏覽器支持**: 雖然大多數現代瀏覽器都支持這個 API，但在某些舊版瀏覽器中，可能需要使用 `addListener` 方法。
3. **初始化狀態**: 在設置事件監聽器之前，建議先檢查當前的媒體查詢狀態，以確保應用程序在首次加載時能正確反映視口狀態。

## 總結
MediaQueryListEvent 是一個強大的工具，可以幫助開發者創建更具響應性的 Web 應用，通過監聽媒體查詢的變化來調整用戶界面。