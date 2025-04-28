<!--
Meta Description: # MediaKeySession：JavaScript 中的媒體密鑰會話管理 ## 摘要 MediaKeySession 是一個 JavaScript 接口，用於管理和操作媒體內容的加密密鑰會話，特別是在使用 HTML5 的媒體播放時實現數字版權管理 (DRM)。 ## 文檔 ### 目的 Med...
Meta Keywords: mediakeysession, mediakeys, error, console, javascript
-->

# MediaKeySession：JavaScript 中的媒體密鑰會話管理

## 摘要
MediaKeySession 是一個 JavaScript 接口，用於管理和操作媒體內容的加密密鑰會話，特別是在使用 HTML5 的媒體播放時實現數字版權管理 (DRM)。

## 文檔
### 目的
MediaKeySession 的主要目的是提供一個介面，用於管理與媒體內容的 DRM 相關的加密密鑰。這個介面讓開發者能夠請求和獲取密鑰，並在播放受保護的媒體內容時進行管理。

### 使用方法
在使用 MediaKeySession 前，開發者需要先初始化 MediaKeys 物件，然後使用該物件創建一個新的 MediaKeySession。下面是基本的使用流程：

1. 創建一個 MediaKeys 實例。
2. 透過 MediaKeys 實例創建 MediaKeySession。
3. 使用 MediaKeySession 進行密鑰請求和管理。

### 詳細信息
- **屬性**：
  - `expiration`：返回密鑰會話的過期時間。
  - `keyIds`：返回與該會話相關的密鑰 ID 列表。
  
- **方法**：
  - `close()`：關閉當前的密鑰會話。
  - `update()`：用於更新密鑰會話的內容。

## 示例
以下是 MediaKeySession 的基本用法示例：

```javascript
// 創建 MediaKeys 實例
const mediaKeys = new MediaKeys('com.widevine.alpha');

// 創建 MediaKeySession
const keySession = mediaKeys.createSession();

// 請求密鑰
keySession.generateRequest('cenc', initData).then(() => {
    console.log('密鑰請求成功');
}).catch(error => {
    console.error('密鑰請求失敗:', error);
});

// 更新密鑰會話
keySession.update(newKeyData).then(() => {
    console.log('密鑰會話更新成功');
}).catch(error => {
    console.error('密鑰會話更新失敗:', error);
});

// 關閉密鑰會話
keySession.close().then(() => {
    console.log('密鑰會話已關閉');
});
```

## 解釋
在使用 MediaKeySession 時，有幾個常見的陷阱：
- 確保在創建 MediaKeySession 之前，MediaKeys 實例已正確初始化。
- 要注意異步操作的處理，因為許多方法都返回 Promise，必須使用 `.then()` 和 `.catch()` 來處理成功和失敗的情況。
- 在密鑰會話過期後，必須重新建立會話以繼續播放受保護的內容。

## 一句總結
MediaKeySession 是一個關鍵的 JavaScript 接口，用於管理和操作媒體內容的加密密鑰會話，特別是在實現 DRM 時。