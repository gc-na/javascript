<!--
Meta Description: # URIError：JavaScript 中的 URI 錯誤 ## 摘要 URIError 是 JavaScript 中的一種內建錯誤類型，當 URI 操作失敗時會被拋出。這通常發生在對不正確的 URI 進行編碼或解碼時。 ## 文檔 ### 目的 URIError 主要用於表示在處理 URI 時...
Meta Keywords: uri, urierror, javascript, decodeuricomponent, decodeuri
-->

# URIError：JavaScript 中的 URI 錯誤

## 摘要
URIError 是 JavaScript 中的一種內建錯誤類型，當 URI 操作失敗時會被拋出。這通常發生在對不正確的 URI 進行編碼或解碼時。

## 文檔
### 目的
URIError 主要用於表示在處理 URI 時出現的錯誤，特別是在使用 `decodeURI()` 或 `decodeURIComponent()` 函數時，當傳入的字符串無法正確解碼時，將會引發此錯誤。

### 用法
在 JavaScript 中，URIError 不是一個函數，而是一個錯誤對象類型。當 URI 操作出現問題時，可以通過 try-catch 結構捕獲這個錯誤，以便進行適當的錯誤處理。

### 詳細說明
- **URIError** 是內建於 JavaScript 的錯誤類型之一，屬於內建的 Error 類別。
- 通常在以下函數中出現：
  - `decodeURI()`
  - `decodeURIComponent()`
- 當傳入的字符串不符合有效 URI 的格式時，會拋出 URIError。

## 範例
### 基本用法
以下是一個使用 `decodeURIComponent()` 的範例，當傳入不正確的 URI 時將引發 URIError：

```javascript
try {
    let result = decodeURIComponent('%E0%A4%A');
} catch (e) {
    if (e instanceof URIError) {
        console.log('捕獲到 URIError:', e.message);
    } else {
        console.log('其他錯誤:', e);
    }
}
```

在上面的範例中，由於 '%E0%A4%A' 不是一個有效的 URI 編碼，將會拋出 URIError。

## 解釋
### 常見問題
- **不正確的編碼**：確保傳入的字符串是正確的 URI 編碼，否則會引發錯誤。
- **錯誤的函數使用**：使用 `decodeURI()` 來解碼整個 URI，而使用 `decodeURIComponent()` 來解碼 URI 的組件部分。

### 注意事項
- 捕獲 URIError 時，要特別檢查錯誤的具體信息，以便針對性地處理。
- 在處理用戶輸入時，應該對 URI 進行驗證，以避免引發這種類型的錯誤。

## 一行總結
URIError 是當無法正確編碼或解碼 URI 時拋出的錯誤，主要用於處理 URI 相關的操作錯誤。