<!--
Meta Description: # FocusEvent：JavaScript 中的焦點事件 ## 簡介 FocusEvent 是 JavaScript 中一個重要的事件類型，用於處理元素獲得或失去焦點的情況。它廣泛應用於表單元素、按鈕及其他可互動元素中，確保使用者與網頁的互動更為流暢。 ## 文檔 ### 目的 FocusEve...
Meta Keywords: focusevent, inputfield, javascript, focus, blur
-->

# FocusEvent：JavaScript 中的焦點事件

## 簡介
FocusEvent 是 JavaScript 中一個重要的事件類型，用於處理元素獲得或失去焦點的情況。它廣泛應用於表單元素、按鈕及其他可互動元素中，確保使用者與網頁的互動更為流暢。

## 文檔
### 目的
FocusEvent 的主要目的是提供一種機制，以便在使用者與網頁元素互動時，能夠監控焦點的變化。這對於表單驗證、用戶體驗改進等場景十分重要。

### 使用方式
FocusEvent 主要有兩種事件：
- `focus`：當元素獲得焦點時觸發。
- `blur`：當元素失去焦點時觸發。

這些事件可以通過 JavaScript 的事件監聽器進行處理。

### 詳細說明
- **屬性**：
  - `relatedTarget`：返回與當前焦點事件相關的元素，通常是失去焦點的元素。
  - `bubbles`：表示事件是否會向上冒泡。
  - `cancelable`：表示事件是否可以被取消。

- **實作範例**：
  ```javascript
  const inputField = document.getElementById('myInput');

  inputField.addEventListener('focus', () => {
    console.log('輸入框已獲得焦點');
  });

  inputField.addEventListener('blur', () => {
    console.log('輸入框已失去焦點');
  });
  ```

## 範例
以下是一個基本的使用範例，展示如何使用 FocusEvent 來監控輸入框的焦點變化。

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>FocusEvent 範例</title>
</head>
<body>
    <input type="text" id="myInput" placeholder="請輸入文字...">
    <script>
        const inputField = document.getElementById('myInput');

        inputField.addEventListener('focus', () => {
            console.log('輸入框已獲得焦點');
        });

        inputField.addEventListener('blur', () => {
            console.log('輸入框已失去焦點');
        });
    </script>
</body>
</html>
```

## 解釋
在使用 FocusEvent 時，開發者需小心一些常見的陷阱：
- **事件冒泡**：`focus` 和 `blur` 事件不會冒泡，這可能導致一些開發者意外地無法捕獲事件。
- **可取消性**：雖然大多數事件是可取消的，但焦點事件的行為無法被取消，因此需要注意。
- **兼容性**：大多數現代瀏覽器都支持 FocusEvent，但在某些舊版本的瀏覽器中，行為可能會有所不同。

## 一句總結
FocusEvent 是 JavaScript 中用於監控元素獲得或失去焦點的重要事件。