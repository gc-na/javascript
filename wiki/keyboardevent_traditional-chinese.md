<!--
Meta Description: # JavaScript KeyboardEvent 事件詳解 ## 概述 `KeyboardEvent` 是一個與鍵盤事件相關的接口，它在用戶與鍵盤互動時提供信息，常用於捕獲鍵盤輸入並響應用戶的操作。 ## 文檔 `KeyboardEvent` 是一個用於描述鍵盤事件的對象，包括按鍵按下、釋放或重...
Meta Keywords: keyboardevent, event, javascript, keydown, key
-->

# JavaScript KeyboardEvent 事件詳解

## 概述
`KeyboardEvent` 是一個與鍵盤事件相關的接口，它在用戶與鍵盤互動時提供信息，常用於捕獲鍵盤輸入並響應用戶的操作。

## 文檔
`KeyboardEvent` 是一個用於描述鍵盤事件的對象，包括按鍵按下、釋放或重複等動作。當用戶按下鍵盤上的某個按鍵時，瀏覽器會觸發對應的事件。這些事件可以用於增強用戶體驗，例如實現自定義快捷鍵、遊戲控制或表單驗證等。

### 語法
```javascript
new KeyboardEvent(type, options);
```

### 參數
- `type` (字串)：必需，事件的類型，通常為 `"keydown"`、`"keyup"` 或 `"keypress"`。
- `options` (物件)：可選，包含事件的特性，如：
  - `bubbles` (布林值)：事件是否應該在 DOM 中冒泡，預設為 `false`。
  - `cancelable` (布林值)：事件是否可以被取消，預設為 `false`。
  - `key` (字串)：代表按下的鍵的名稱（例如 `"a"`、`"Enter"`）。
  - `code` (字串)：代表按下的鍵的物理位置（例如 `"KeyA"`、`"Enter"`）。
  - `ctrlKey`、`shiftKey`、`altKey`、`metaKey` (布林值)：表示是否按下了對應的修飾鍵。

### 使用範例
```javascript
// 監聽鍵盤按下事件
document.addEventListener('keydown', function(event) {
    console.log(`按下的鍵: ${event.key}`);
});

// 創建並分派一個 KeyboardEvent
const event = new KeyboardEvent('keydown', {
    key: 'A', 
    code: 'KeyA', 
    ctrlKey: true
});
document.dispatchEvent(event);
```

## 解釋
在使用 `KeyboardEvent` 時，有一些常見的陷阱需要注意：

1. **事件類型**：`keypress` 事件在某些瀏覽器中已被淘汰，建議使用 `keydown` 和 `keyup` 來替代。
2. **事件屬性**：確保檢查 `event.key` 和 `event.code` 的使用情境，前者代表鍵的名稱，而後者代表鍵的物理位置。
3. **跨瀏覽器兼容性**：不同瀏覽器對於 `KeyboardEvent` 的支持程度可能有所不同，測試你的代碼在主要瀏覽器上的表現至關重要。

## 一句總結
`KeyboardEvent` 是用於捕捉和處理鍵盤事件的 JavaScript 接口，為用戶提供更互動的體驗。