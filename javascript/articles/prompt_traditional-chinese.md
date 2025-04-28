<!--
Meta Description: # JavaScript 的 prompt 函數：用戶輸入的簡單方法 ## 摘要 `prompt` 是 JavaScript 中一個用於接收用戶輸入的內建函數。它會顯示一個對話框，讓用戶輸入數據並返回該數據。 ## 文檔 ### 目的 `prompt` 函數的主要目的是收集用戶的輸入，這在需要用戶提...
Meta Keywords: prompt, javascript, let, age, message
-->

# JavaScript 的 prompt 函數：用戶輸入的簡單方法

## 摘要
`prompt` 是 JavaScript 中一個用於接收用戶輸入的內建函數。它會顯示一個對話框，讓用戶輸入數據並返回該數據。

## 文檔
### 目的
`prompt` 函數的主要目的是收集用戶的輸入，這在需要用戶提供信息的情況下非常有用，例如表單填寫、選項選擇等。

### 語法
```javascript
let userInput = prompt([message], [default]);
```

### 參數
- **message** (可選)：顯示在對話框中的提示訊息，通常用於告訴用戶需要輸入什麼。
- **default** (可選)：對話框中預設的輸入值，若用戶沒有輸入任何內容，則返回預設值。

### 返回值
`prompt` 返回用戶輸入的字符串。如果用戶按下“取消”按鈕，則返回 `null`。

### 使用說明
- 在使用 `prompt` 時，請注意它會阻止頁面的其他操作，直到用戶關閉對話框。
- `prompt` 的使用通常被建議在非生產環境中，因為它會打斷用戶的流暢體驗。

## 範例
### 基本使用範例
```javascript
let name = prompt("請輸入您的名字：", "無名氏");
console.log("您好，" + name + "!");
```

### 使用預設值
```javascript
let age = prompt("請輸入您的年齡：", "25");
if (age !== null) {
    console.log("您的年齡是：" + age);
}
```

## 解釋
- **兼容性問題**：不是所有瀏覽器都完全支持 `prompt` 的外觀和行為，這可能會影響用戶體驗。
- **用戶體驗**：由於 `prompt` 會打斷當前的頁面操作，過度使用會影響用戶的流暢性，建議使用HTML表單替代。
- **安全性考量**：對於敏感信息的收集，不建議使用 `prompt`，因為它無法提供安全保障。

## 總結
`prompt` 是一個簡單的 JavaScript 函數，用於接收用戶輸入，但應謹慎使用以避免影響用戶體驗。