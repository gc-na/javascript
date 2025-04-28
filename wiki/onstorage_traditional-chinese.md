<!--
Meta Description: # JavaScript onstorage 事件詳解 ## 簡介 `onstorage` 事件是 JavaScript 中的一個重要事件，用於監聽 `localStorage` 或 `sessionStorage` 中的數據更改。當同一個源中的不同窗口或標籤頁對存儲數據進行修改時，會觸發此事件。 ...
Meta Keywords: onstorage, localstorage, event, javascript, sessionstorage
-->

# JavaScript onstorage 事件詳解

## 簡介
`onstorage` 事件是 JavaScript 中的一個重要事件，用於監聽 `localStorage` 或 `sessionStorage` 中的數據更改。當同一個源中的不同窗口或標籤頁對存儲數據進行修改時，會觸發此事件。

## 文檔
### 目的
`onstorage` 事件的主要目的是允許開發者在不同的瀏覽器窗口或標籤頁中，對同一個存儲空間的變化進行響應。這對於需要在多個視圖中保持數據同步的應用程序尤其重要。

### 使用方式
`onstorage` 事件可以通過將事件處理器附加到 `window` 對象來使用。當 `localStorage` 或 `sessionStorage` 中的數據被修改時，會觸發該事件。

#### 語法
```javascript
window.onstorage = function(event) {
    // 處理事件
};
```

### 事件對象
`onstorage` 事件的事件對象包含以下重要屬性：
- `key`: 被修改的存儲項的鍵名。
- `oldValue`: 修改前的值。
- `newValue`: 修改後的值。
- `url`: 觸發事件的文檔的 URL。
- `storageArea`: 觸發事件的存儲區域（`localStorage` 或 `sessionStorage`）。

## 範例
### 基本用法
以下是如何使用 `onstorage` 事件的基本範例：

```javascript
// 當 storage 發生變化時
window.onstorage = function(event) {
    console.log('Key: ' + event.key);
    console.log('Old Value: ' + event.oldValue);
    console.log('New Value: ' + event.newValue);
    console.log('URL: ' + event.url);
};

// 在其他窗口或標籤頁中進行存儲修改
localStorage.setItem('exampleKey', 'exampleValue');
```

### 多窗口同步
在一個窗口中改變 `localStorage` 時，另一個窗口將能夠接收到該變化：

**窗口 A**
```javascript
localStorage.setItem('username', 'Alice');
```

**窗口 B**
```javascript
window.onstorage = function(event) {
    if (event.key === 'username') {
        console.log('Username updated to: ' + event.newValue);
    }
};
```

## 說明
### 常見陷阱
1. **同一窗口不會觸發事件**: `onstorage` 事件僅在不同窗口或標籤頁之間觸發。當在同一窗口中進行 `localStorage` 的更改時，不會有事件被觸發。
2. **事件處理器的設置時機**: 確保在使用 `localStorage` 進行任何操作之前，已經設置好事件處理器，否則可能會錯過事件。

### 附加說明
- `sessionStorage` 的變化不會觸發 `onstorage` 事件，因為 `sessionStorage` 是針對每個窗口的獨立存儲空間，而 `localStorage` 是共享的。
- 瀏覽器的隱私模式可能會影響 `localStorage` 和 `sessionStorage` 的行為，開發者應注意這一點。

## 一句話總結
`onstorage` 事件允許開發者在不同窗口或標籤頁之間響應 `localStorage` 的數據變化。