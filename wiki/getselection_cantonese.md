<!--
Meta Description: # 使用 JavaScript 的 getSelection 方法：獲取文本選擇 ## 概述 `getSelection` 是一個 JavaScript 方法，用於獲取用戶在文檔中選擇的文本範圍。此方法對於處理用戶選擇的文本或實現自定義文本編輯功能非常有用。 ## 文檔 ### 目的 `getSel...
Meta Keywords: getselection, selection, javascript, window, let
-->

# 使用 JavaScript 的 getSelection 方法：獲取文本選擇

## 概述
`getSelection` 是一個 JavaScript 方法，用於獲取用戶在文檔中選擇的文本範圍。此方法對於處理用戶選擇的文本或實現自定義文本編輯功能非常有用。

## 文檔
### 目的
`getSelection` 方法的主要目的是獲取當前用戶在網頁上選擇的文本範圍，通常用於實現複製、剪切、或特定文本操作的功能。

### 使用方法
要使用 `getSelection` 方法，可以直接調用 `window.getSelection()`。此方法返回一個 Selection 物件，該物件包含用戶當前選擇的文本範圍及相關信息。

### 詳細說明
- **返回值**：`getSelection` 返回一個 Selection 物件，該物件包含以下屬性：
  - `anchorNode`：選擇開始的節點。
  - `focusNode`：選擇結束的節點。
  - `toString()`：返回用戶選擇的文本。
  - `rangeCount`：選擇範圍的數量。

### 語法
```javascript
let selection = window.getSelection();
```

## 範例
### 基本用法
以下是使用 `getSelection` 方法的簡單範例：

```javascript
// 獲取用戶選擇的文本
document.addEventListener('mouseup', function() {
    let selection = window.getSelection();
    console.log('用戶選擇的文本:', selection.toString());
});
```

### 獲取選擇範圍
```javascript
document.addEventListener('mouseup', function() {
    let selection = window.getSelection();
    if (selection.rangeCount > 0) {
        let range = selection.getRangeAt(0);
        console.log('選擇的開始節點:', range.startContainer);
        console.log('選擇的結束節點:', range.endContainer);
    }
});
```

## 解釋
- **常見問題**：
  - `getSelection` 返回的文本可能會包含空格或換行符，這可能會影響後續的文本處理。
  - 確保在用戶完成選擇後再調用 `getSelection`，否則可能獲取到不完整的選擇結果。
  
- **注意事項**：
  - 在某些瀏覽器中，選擇的行為可能會有所不同，特別是在不同的操作系統或設備上。
  - 如果用戶沒有選擇任何文本，`toString()` 方法將返回空字符串。

## 總結
`getSelection` 是一個強大的方法，允許開發者獲取用戶在網頁上選擇的文本範圍，對於實現文本編輯功能、複製和剪切操作非常重要。