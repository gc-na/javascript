<!--
Meta Description: # JavaScript FormData 物件詳解：用於處理表單數據 ## 摘要 `FormData` 是一個用於構建表單數據的 JavaScript 物件，能夠輕鬆地將表單數據轉換為可用於 AJAX 請求的格式，特別是在處理檔案上傳時。 ## 文檔 `FormData` 物件是用來構建一個表示表...
Meta Keywords: formdata, name, ajax, javascript, form
-->

# JavaScript FormData 物件詳解：用於處理表單數據

## 摘要
`FormData` 是一個用於構建表單數據的 JavaScript 物件，能夠輕鬆地將表單數據轉換為可用於 AJAX 請求的格式，特別是在處理檔案上傳時。

## 文檔
`FormData` 物件是用來構建一個表示表單數據的鍵值對集合，通常用於 AJAX 請求中。它提供了一種方便的方式來收集和發送表單資料，特別適合於多部分表單資料（例如包含檔案的表單）。

### 用法
要創建一個新的 `FormData` 物件，可以使用以下語法：

```javascript
let formData = new FormData(formElement);
```

這裡 `formElement` 是一個參考到 HTML 表單的元素，這樣可以自動從表單中收集所有的輸入數據。

### 主要功能
- **添加數據**：可以使用 `append(name, value)` 方法向 `FormData` 物件添加新的鍵值對。
- **獲取數據**：可以使用 `get(name)` 方法獲取對應鍵的值。
- **檢查鍵是否存在**：使用 `has(name)` 方法來檢查某個鍵是否存在於 `FormData` 中。
- **刪除數據**：使用 `delete(name)` 方法刪除特定鍵的數據。

## 範例
### 基本用法示例
以下是一個簡單的例子，說明如何使用 `FormData` 來收集表單數據並發送 AJAX 請求：

```html
<form id="myForm">
  <input type="text" name="username" value="JohnDoe" />
  <input type="file" name="profilePicture" />
  <button type="submit">提交</button>
</form>

<script>
  document.getElementById('myForm').addEventListener('submit', function(event) {
    event.preventDefault(); // 防止表單默認提交

    let formData = new FormData(this);

    fetch('/upload', {
      method: 'POST',
      body: formData
    })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('錯誤:', error));
  });
</script>
```

## 解釋
### 常見陷阱與注意事項
1. **IE 支持**：`FormData` 在 Internet Explorer 11 中不完全支持，因此在舊版瀏覽器中使用時需謹慎。
2. **檔案上傳**：在使用 `FormData` 進行檔案上傳時，請確保表單的 `enctype` 設置為 `multipart/form-data`。
3. **URL 編碼**：`FormData` 不會自動對數據進行 URL 編碼，因此在處理複雜的數據時可能需要手動處理。

## 總結
`FormData` 是一個強大的工具，能夠輕鬆地從表單收集數據並用於 AJAX 請求，特別是在處理檔案上傳時極為方便。