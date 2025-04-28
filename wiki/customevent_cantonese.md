<!--
Meta Description: # CustomEvent：JavaScript 中的自定義事件 ## 簡介 `CustomEvent` 是 JavaScript 中用於創建自定義事件的功能，讓開發者能夠在應用程式中觸發和處理自定義事件。透過 `CustomEvent`，開發者能夠傳遞額外的數據給事件監聽器，增強應用的互動性。 #...
Meta Keywords: customevent, javascript, detail, bubbles, 默認為
-->

# CustomEvent：JavaScript 中的自定義事件

## 簡介
`CustomEvent` 是 JavaScript 中用於創建自定義事件的功能，讓開發者能夠在應用程式中觸發和處理自定義事件。透過 `CustomEvent`，開發者能夠傳遞額外的數據給事件監聽器，增強應用的互動性。

## 文檔
`CustomEvent` 構造函數允許開發者創建一個新的事件對象，該對象可以攜帶附加的數據。使用 `CustomEvent` 可以方便地在不同的組件之間傳遞信息，提升應用的靈活性和可維護性。

### 語法
```javascript
let event = new CustomEvent(type, options);
```

### 參數
- **type**: 字符串，表示事件的名稱，必須提供。
- **options**: 一個可選的對象，包含以下屬性：
  - **bubbles**: 布爾值，指示事件是否可以冒泡，默認為 `false`。
  - **cancelable**: 布爾值，指示事件是否可被取消，默認為 `false`。
  - **detail**: 可以攜帶的附加數據，默認為 `null`。

### 使用範例
以下是一個使用 `CustomEvent` 的簡單範例：

```javascript
// 定義事件類型
const myEvent = new CustomEvent('myCustomEvent', {
    detail: { key: 'value' },
    bubbles: true,
    cancelable: true
});

// 事件監聽器
document.addEventListener('myCustomEvent', function (e) {
    console.log('自定義事件被觸發:', e.detail);
});

// 觸發事件
document.dispatchEvent(myEvent);
```

在這個例子中，我們創建了一個名為 `myCustomEvent` 的自定義事件，並將一個包含鍵值對的對象作為事件詳細信息。當事件被觸發時，監聽器會捕獲這個事件並顯示詳細信息。

## 解釋
使用 `CustomEvent` 時，有幾個常見的陷阱需要注意：

1. **事件名稱的唯一性**: 確保自定義事件名稱不與現有事件名稱衝突，否則可能導致意想不到的行為。
2. **冒泡和可取消性**: 根據應用需求，合理設置 `bubbles` 和 `cancelable` 屬性。若設置為 `false`，則事件將不會冒泡或可被取消。
3. **事件詳細信息的使用**: 在傳遞數據時，利用 `detail` 屬性來攜帶需要的信息，但要注意數據的格式和類型，以便正確處理。

## 一句概述
`CustomEvent` 是一個強大的工具，用於在 JavaScript 應用中創建和處理自定義事件，允許開發者靈活傳遞數據。