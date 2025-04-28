<!--
Meta Description: # showSaveFilePicker：JavaScript 中的檔案儲存對話框 ## 簡介 `showSaveFilePicker` 是一個 Web API，允許用戶在瀏覽器中選擇檔案儲存位置，並指定檔案名稱。這個功能使得 Web 應用程式能夠更方便地儲存檔案，增強了用戶體驗。 ## 文檔 ##...
Meta Keywords: showsavefilepicker, await, options, javascript, const
-->

# showSaveFilePicker：JavaScript 中的檔案儲存對話框

## 簡介
`showSaveFilePicker` 是一個 Web API，允許用戶在瀏覽器中選擇檔案儲存位置，並指定檔案名稱。這個功能使得 Web 應用程式能夠更方便地儲存檔案，增強了用戶體驗。

## 文檔
### 目的
`showSaveFilePicker` 方法的主要目的是提供一個接口，讓用戶能夠選擇儲存檔案的路徑和名稱。這可以用於各種應用程式，如文本編輯器、圖像編輯器等，讓用戶能夠輕鬆地保存檔案。

### 用法
要使用 `showSaveFilePicker`，你需要先確保你的瀏覽器支持這個 API。這個方法返回一個 Promise，當用戶選擇檔案或取消對話框後，Promise 會被解析。

#### 語法
```javascript
const fileHandle = await window.showSaveFilePicker(options);
```

#### 參數
- `options`（可選）：一個包含檔案儲存選項的物件，例如：
  - `types`: 指定可儲存的檔案類型，通常是一個物件陣列，包含 `description` 和 `accept` 屬性。

### 示例
以下是使用 `showSaveFilePicker` 的基本示例：

```javascript
async function saveFile() {
    const options = {
        types: [{
            description: '文本檔案',
            accept: {
                'text/plain': ['.txt'],
            },
        }],
    };

    try {
        const fileHandle = await window.showSaveFilePicker(options);
        const writable = await fileHandle.createWritable();
        await writable.write('Hello, World!');
        await writable.close();
        console.log('檔案已儲存！');
    } catch (error) {
        console.error('儲存檔案時發生錯誤:', error);
    }
}
```

### 解釋
- **常見陷阱**：請注意，`showSaveFilePicker` 只能在用戶的互動事件中被調用（例如按鈕點擊事件），否則會拋出錯誤。
- **相容性問題**：不是所有的瀏覽器都支持這個 API，建議檢查瀏覽器的相容性。
- **選項配置**：在指定 `options` 時，一定要確保 `accept` 的 MIME 類型和擴展名一致，以避免用戶選取不正確的檔案類型。

## 一句話總結
`showSaveFilePicker` 是一個方便的 JavaScript 方法，允許用戶選擇檔案儲存位置和名稱，增強 Web 應用程式的使用體驗。