<!--
Meta Description: # HTMLScriptElement：JavaScript 中的 HTML <script> 元素 ## 概述 `HTMLScriptElement` 是一個表示 HTML 中 `<script>` 標籤的接口，提供對 JavaScript 腳本的動態操作功能。它使開發者能夠在網頁中插入和修改腳本...
Meta Keywords: script, javascript, document, htmlscriptelement, async
-->

# HTMLScriptElement：JavaScript 中的 HTML <script> 元素

## 概述
`HTMLScriptElement` 是一個表示 HTML 中 `<script>` 標籤的接口，提供對 JavaScript 腳本的動態操作功能。它使開發者能夠在網頁中插入和修改腳本元素，並控制其加載及執行行為。

## 文檔
`HTMLScriptElement` 是一個 DOM 接口，專門用於處理網頁中的 `<script>` 標籤。此接口提供了多個屬性和方法，讓開發者能夠動態地創建和配置腳本元素。主要的屬性包括：

- `src`：指定外部 JavaScript 檔案的 URL。
- `type`：定義腳本的 MIME 類型，預設為 `"text/javascript"`。
- `async`：一個布林值，指示腳本是否應該異步加載。
- `defer`：一個布林值，指示腳本是否應該延遲執行，直到文檔解析完成。
- `innerHTML`：用於直接寫入腳本內容。

### 用法
要使用 `HTMLScriptElement`，可以通過 JavaScript 的 `document.createElement` 方法創建一個 `<script>` 標籤，然後設置其屬性。

```javascript
const script = document.createElement('script');
script.src = 'https://example.com/script.js'; // 設定外部腳本的來源
script.type = 'text/javascript'; // 設定腳本類型
script.async = true; // 設定為異步加載
document.head.appendChild(script); // 將腳本添加到文檔中
```

## 示例
以下是幾個基本示例，展示如何使用 `HTMLScriptElement`：

1. **動態添加外部腳本：**

    ```javascript
    const script = document.createElement('script');
    script.src = 'https://example.com/external.js';
    document.body.appendChild(script);
    ```

2. **使用內部腳本：**

    ```javascript
    const script = document.createElement('script');
    script.innerHTML = 'console.log("Hello, World!");';
    document.body.appendChild(script);
    ```

3. **異步加載腳本：**

    ```javascript
    const script = document.createElement('script');
    script.src = 'https://example.com/asyncScript.js';
    script.async = true;
    document.head.appendChild(script);
    ```

## 解釋
使用 `HTMLScriptElement` 時需注意以下幾點：

- **加載順序**：如果同時設置 `async` 和 `defer`，`async` 的優先級更高。這可能導致腳本的加載和執行順序不如預期。
- **跨域問題**：在加載外部腳本時，需考慮 CORS（跨來源資源共享）政策，否則可能會導致腳本無法正常加載。
- **DOM 解析**：如果腳本中包含與 DOM 交互的代碼，確保在文檔完全加載後再執行，否則可能會導致錯誤。

## 總結
`HTMLScriptElement` 是一個強大且靈活的接口，用於在 JavaScript 中動態操作 HTML `<script>` 標籤，以便有效地管理和加載 JavaScript 腳本。