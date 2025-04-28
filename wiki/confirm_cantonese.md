<!--
Meta Description: # JavaScript 的 confirm 函數：用於用戶確認的對話框 ## 概述 `confirm` 是 JavaScript 中一個內建的函數，用於顯示一個對話框，讓用戶確認或取消某個操作。此函數通常用於需要用戶進一步確認的場景，例如刪除文件或提交表單時。 ## 文檔 ### 目的 `conf...
Meta Keywords: confirm, javascript, let, message, 如果用戶點擊
-->

# JavaScript 的 confirm 函數：用於用戶確認的對話框

## 概述
`confirm` 是 JavaScript 中一個內建的函數，用於顯示一個對話框，讓用戶確認或取消某個操作。此函數通常用於需要用戶進一步確認的場景，例如刪除文件或提交表單時。

## 文檔
### 目的
`confirm` 函數的主要目的是提供一種簡單的方式來獲取用戶的確認。它會彈出一個對話框，顯示指定的訊息，並提供“確定”和“取消”兩個按鈕。

### 使用方法
`confirm` 的語法如下：
```javascript
let userResponse = confirm(message);
```
- **參數**：
  - `message`（字符串）：要顯示在對話框中的文本消息。

- **返回值**：
  - 如果用戶點擊“確定”，則返回 `true`。
  - 如果用戶點擊“取消”，則返回 `false`。

### 詳細說明
- `confirm` 函數會阻塞代碼的執行，直到用戶做出選擇。
- 這個對話框的外觀和感覺可能會根據不同的瀏覽器而異。
- 不建議頻繁使用 `confirm`，因為它可能會影響用戶體驗，過多的彈出窗口可能會讓用戶感到煩惱。

## 範例
### 基本用法
```javascript
let isConfirmed = confirm("你確定要刪除這個項目嗎？");
if (isConfirmed) {
    console.log("項目已被刪除。");
} else {
    console.log("項目未被刪除。");
}
```

### 另一個範例
```javascript
let proceed = confirm("你要繼續嗎？");
if (proceed) {
    alert("繼續進行！");
} else {
    alert("操作已取消。");
}
```

## 解釋
- **常見問題**：
  - 用戶可能會誤點“取消”而不小心中斷操作，因此需要在設計時考慮這一點。
  - `confirm` 是同步函數，這意味著在用戶做出選擇之前，後續代碼不會執行。

- **注意事項**：
  - 不同的瀏覽器可能會對 `confirm` 對話框進行不同的樣式處理。
  - 使用 `confirm` 將阻止用戶與頁面進行其他交互，直到對話框關閉。

## 一句總結
`confirm` 函數是一個用於顯示確認對話框的簡單方法，幫助開發者獲取用戶的選擇。