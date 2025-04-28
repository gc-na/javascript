<!--
Meta Description: # JavaScript 的 confirm 函數：用於顯示確認對話框的對話框 ## 簡介 `confirm` 是 JavaScript 中的一個內建函數，用於在網頁上顯示一個確認對話框，讓用戶做出是或否的選擇。這個函數通常用於需要用戶確認某項操作的場景，比如刪除資料或提交表單。 ## 文檔 ###...
Meta Keywords: confirm, javascript, isconfirmed, console, log
-->

# JavaScript 的 confirm 函數：用於顯示確認對話框的對話框

## 簡介
`confirm` 是 JavaScript 中的一個內建函數，用於在網頁上顯示一個確認對話框，讓用戶做出是或否的選擇。這個函數通常用於需要用戶確認某項操作的場景，比如刪除資料或提交表單。

## 文檔
### 目的
`confirm` 函數的主要目的是提供一個簡單的方式來與用戶進行互動，獲取用戶的確認或取消操作的意圖。

### 語法
```javascript
let userResponse = confirm(message);
```

### 參數
- `message` (string)：要顯示在對話框中的提示信息。通常用來告訴用戶他們正在確認的內容。

### 返回值
`confirm` 函數返回一個布林值：
- 如果用戶點擊「確定」，返回 `true`。
- 如果用戶點擊「取消」，返回 `false`。

## 範例
### 基本用法
```javascript
let isConfirmed = confirm("您確定要刪除這個項目嗎？");
if (isConfirmed) {
    console.log("項目已被刪除。");
} else {
    console.log("項目未被刪除。");
}
```

### 使用於表單提交
```javascript
function submitForm() {
    let isConfirmed = confirm("您確定要提交這個表單嗎？");
    if (isConfirmed) {
        // 執行提交操作
        console.log("表單已提交。");
    } else {
        // 取消提交
        console.log("表單提交被取消。");
    }
}
```

## 解釋
使用 `confirm` 函數時，有幾個常見的陷阱和注意事項：
1. **用戶體驗**：過於頻繁地使用 `confirm` 對話框可能會影響用戶體驗，因此應謹慎使用。
2. **非模態性**：`confirm` 對話框是模態的，這意味著用戶必須先處理這個對話框才能繼續與頁面互動。
3. **樣式限制**：`confirm` 對話框的樣式無法自定義，這可能不符合某些網站的設計風格。
4. **可訪問性**：對於某些用戶（特別是依賴鍵盤的用戶），`confirm` 對話框可能會造成可訪問性問題。

## 一句總結
`confirm` 函數用於在 JavaScript 中顯示確認對話框，以獲取用戶的確認或取消操作的意圖。