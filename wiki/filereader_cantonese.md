<!--
Meta Description: # JavaScript FileReader：網頁應用程式文件讀取的利器 ## 簡介 FileReader 是一個 JavaScript API，主要用於在網頁應用程式中讀取文件內容，特別是用於處理用戶上傳的文件。透過 FileReader，開發者可以輕鬆地將本地文件轉換成文字、二進制數據或數據 ...
Meta Keywords: filereader, file, const, input, document
-->

# JavaScript FileReader：網頁應用程式文件讀取的利器

## 簡介
FileReader 是一個 JavaScript API，主要用於在網頁應用程式中讀取文件內容，特別是用於處理用戶上傳的文件。透過 FileReader，開發者可以輕鬆地將本地文件轉換成文字、二進制數據或數據 URL，並在網頁上顯示或進行後續處理。

## 文件說明
FileReader 物件透過 API 提供了一系列方法和事件，讓開發者能夠非同步地讀取文件。它主要用於以下目的：

- 讀取用戶上傳的文件內容。
- 支援多種讀取格式，包括文本、二進制和資料 URL。
- 提供事件監聽來追蹤讀取過程的狀態。

### 使用方法
在使用 FileReader 前，需先確認用戶已選擇文件。常用的 FileReader 方法包括：

- `readAsText(file)`：以文本格式讀取文件。
- `readAsDataURL(file)`：以資料 URL 格式讀取文件，適用於圖片等媒體文件。
- `readAsArrayBuffer(file)`：以 ArrayBuffer 格式讀取文件，適用於二進制數據。

### 事件
FileReader 提供多個事件來追蹤文件讀取過程，包括：

- `onload`：當文件成功讀取後觸發。
- `onerror`：當發生錯誤時觸發。
- `onloadend`：無論讀取成功與否都會觸發。

## 範例
以下是使用 FileReader 的基本範例：

### 讀取文本文件
```javascript
const input = document.createElement('input');
input.type = 'file';
input.onchange = (event) => {
    const file = event.target.files[0];
    const reader = new FileReader();
    reader.onload = (e) => {
        console.log(e.target.result); // 輸出文件內容
    };
    reader.readAsText(file);
};
document.body.appendChild(input);
```

### 讀取圖片文件
```javascript
const inputImage = document.createElement('input');
inputImage.type = 'file';
inputImage.accept = 'image/*';
inputImage.onchange = (event) => {
    const file = event.target.files[0];
    const reader = new FileReader();
    reader.onload = (e) => {
        const img = document.createElement('img');
        img.src = e.target.result; // 設置圖片來源為文件內容
        document.body.appendChild(img);
    };
    reader.readAsDataURL(file);
};
document.body.appendChild(inputImage);
```

## 解釋
使用 FileReader 時有幾個常見的問題和注意事項：

- **文件大小限制**：部分瀏覽器對於可讀取的文件大小有限制，應注意使用者的上傳文件大小。
- **非同步性**：FileReader 的讀取操作是非同步的，確保在讀取完成事件後再進行後續操作。
- **檔案類型**：確保用戶上傳的檔案類型與所需格式相符，以避免讀取錯誤。

## 總結
FileReader 是一個強大的工具，能有效地在 JavaScript 網頁應用程式中處理和讀取用戶上傳的文件，支援多種格式的讀取操作。