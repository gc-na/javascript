<!--
Meta Description: # Trusted Types：提升 JavaScript 網頁安全性的關鍵技術 ## 概述 Trusted Types 是一種 JavaScript 安全機制，用於防止跨站腳本攻擊（XSS），藉由強制開發者使用安全的方式來處理和插入 HTML、JavaScript 代碼。 ## 文件說明 ### ...
Meta Keywords: trusted, types, javascript, html, type
-->

# Trusted Types：提升 JavaScript 網頁安全性的關鍵技術

## 概述
Trusted Types 是一種 JavaScript 安全機制，用於防止跨站腳本攻擊（XSS），藉由強制開發者使用安全的方式來處理和插入 HTML、JavaScript 代碼。

## 文件說明
### 目的
Trusted Types 的主要目的是減少 XSS 攻擊的風險。透過強制使用經過信任的類型來插入動態內容，開發者能夠確保只有經過驗證的資料可以進入 DOM。

### 使用方式
要啟用 Trusted Types，開發者需要在網頁中定義一個 Trusted Type 生成器，並在應用程式中使用這些生成器來創建受信任的內容。

#### 主要 API
- **createPolicy(name, policy)**：創建一個新的 Trusted Type 政策。
- **getPolicy(name)**：獲取指定名稱的 Trusted Type 政策。
- **isHTML(value)**：檢查指定的值是否為受信任的 HTML。

### 詳細說明
使用 Trusted Types 的步驟如下：
1. **創建政策**：使用 `createPolicy` 方法定義一個政策，這個政策可以指定如何處理 HTML 或 JavaScript 字串。
2. **使用政策**：在需要插入 HTML 或 JavaScript 的地方，使用剛剛創建的政策來生成受信任的內容。
3. **啟用政策**：確保網站的 CSP（內容安全政策）設置允許使用 Trusted Types。

## 範例
### 基本用法
```javascript
// 創建一個新的 Trusted Type 政策
const policy = trustedTypes.createPolicy('default', {
    createHTML: (input) => {
        // 這裡可以添加額外的清理邏輯
        return input; // 返回的內容將被視為受信任的 HTML
    }
});

// 使用政策創建受信任的 HTML
const trustedHTML = policy.createHTML('<div>Hello, World!</div>');

// 將受信任的 HTML 插入到 DOM
document.body.innerHTML = trustedHTML;
```

## 解釋
### 常見錯誤和注意事項
- **未定義政策**：如果嘗試使用未定義的政策，將會引發錯誤。
- **不正確的內容安全政策**：如果頁面沒有正確設置 CSP，Trusted Types 將無法正常運行。
- **過度信任**：即使使用 Trusted Types，也不應該忽略對用戶輸入的驗證和清理。

## 一句話總結
Trusted Types 是一種強化 JavaScript 安全性的技術，透過強制使用經過信任的內容來防止 XSS 攻擊。