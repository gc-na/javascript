<!--
Meta Description: # SubmitEvent：在 JavaScript 中的提交事件 ## 概述 `SubmitEvent` 是一個用於處理表單提交事件的 JavaScript 事件接口。它提供了有關表單提交的詳細信息，並允許開發者在表單提交時進行自定義操作。 ## 文檔 ### 目的 `SubmitEvent` 主...
Meta Keywords: submitevent, event, submit, submitter, preventdefault
-->

# SubmitEvent：在 JavaScript 中的提交事件

## 概述
`SubmitEvent` 是一個用於處理表單提交事件的 JavaScript 事件接口。它提供了有關表單提交的詳細信息，並允許開發者在表單提交時進行自定義操作。

## 文檔
### 目的
`SubmitEvent` 主要用於捕獲表單的提交行為，允許開發者在用戶提交表單時執行特定的邏輯，例如驗證數據、發送 AJAX 請求或取消默認行為。

### 使用方法
當一個表單被提交時，瀏覽器會自動觸發 `submit` 事件。在事件處理程序中，開發者可以訪問 `SubmitEvent` 物件，該物件包含有關提交的表單和提交方式的信息。

#### 組成
`SubmitEvent` 物件的主要屬性包括：
- `submitter`: 提交表單的元素（例如，提交按鈕）。
- `defaultPrevented`: 一個布林值，指示事件是否被取消。

### 事件監聽器示範
以下是如何使用 `SubmitEvent` 的基本範例：

```javascript
document.querySelector('form').addEventListener('submit', function(event) {
    // 獲取 SubmitEvent 物件
    const submitEvent = event;

    // 如果需要，取消默認提交行為
    if (someCondition) {
        event.preventDefault();
    }

    console.log('表單已提交:', submitEvent.submitter);
    console.log('是否已取消默認行為:', submitEvent.defaultPrevented);
});
```

## 範例
### 基本用法
下面的範例顯示如何使用 `SubmitEvent` 來驗證表單數據：

```html
<form id="myForm">
    <input type="text" required />
    <button type="submit">提交</button>
</form>

<script>
    document.getElementById('myForm').addEventListener('submit', function(event) {
        if (!event.target.checkValidity()) {
            event.preventDefault(); // 如果表單無效，取消默認提交
            alert('請填寫所有必填欄位！');
        }
    });
</script>
```

## 解釋
### 常見陷阱
- **未正確使用 `event.preventDefault()`**: 當需要取消表單提交時，必須在事件處理程序中正確使用 `event.preventDefault()`。
- **理解 `submitter` 屬性**: `submitter` 屬性僅在某些情況下可用，確保在具有多個提交按鈕的表單中使用時正確訪問。

### 附加註釋
- `SubmitEvent` 是由更舊的 `Event` 物件擴展而來，因此可以使用 `Event` 的所有屬性和方法。
- 對於需要與後端進行交互的表單，使用 AJAX 或 Fetch API 可以搭配 `SubmitEvent` 進行更靈活的處理。

## 一句概述
`SubmitEvent` 是一個用於捕獲和處理 HTML 表單提交的事件，允許開發者進行自定義操作和數據驗證。