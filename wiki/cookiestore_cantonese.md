<!--
Meta Description: # CookieStore: JavaScript 中的 Cookie 管理 ## 概要 CookieStore 是一個新的 JavaScript API，旨在簡化瀏覽器中的 Cookie 管理。它提供了方便的方式來創建、讀取和刪除 Cookie，使得開發者能更輕鬆地處理用戶數據。 ## 文檔 ##...
Meta Keywords: cookie, cookiestore, console, error, api
-->

# CookieStore: JavaScript 中的 Cookie 管理

## 概要
CookieStore 是一個新的 JavaScript API，旨在簡化瀏覽器中的 Cookie 管理。它提供了方便的方式來創建、讀取和刪除 Cookie，使得開發者能更輕鬆地處理用戶數據。

## 文檔
### 目的
CookieStore API 旨在提供一個統一的介面來操作 Cookie，從而提高開發效率，並減少手動操作 Cookie 的繁瑣。

### 使用方法
CookieStore API 主要包含以下方法：
- `get(name)`：根據 Cookie 名稱獲取 Cookie 的值。
- `set(cookie)`：創建或更新 Cookie。
- `delete(name)`：根據名稱刪除指定的 Cookie。

以下是 CookieStore 的基本使用方法：

```javascript
// 獲取 CookieStore
const cookieStore = cookieStore || window.cookieStore;

// 設置 Cookie
cookieStore.set({
  name: 'username',
  value: 'JohnDoe',
  expires: new Date(Date.now() + 60 * 60 * 1000), // 1小時後過期
  path: '/'
}).then(() => {
  console.log('Cookie 設置成功');
}).catch((error) => {
  console.error('設置 Cookie 時出錯：', error);
});

// 獲取 Cookie
cookieStore.get('username').then((cookie) => {
  if (cookie) {
    console.log(`Cookie 值：${cookie.value}`);
  } else {
    console.log('未找到 Cookie');
  }
}).catch((error) => {
  console.error('獲取 Cookie 時出錯：', error);
});

// 刪除 Cookie
cookieStore.delete('username').then(() => {
  console.log('Cookie 刪除成功');
}).catch((error) => {
  console.error('刪除 Cookie 時出錯：', error);
});
```

## 範例
這裡是一個簡單的範例，展示了如何使用 CookieStore API 來管理 Cookie：

```javascript
async function manageCookies() {
  const cookieStore = window.cookieStore;

  // 設置一個 Cookie
  await cookieStore.set({
    name: 'sessionToken',
    value: 'abc123',
    expires: new Date(Date.now() + 24 * 60 * 60 * 1000), // 1天後過期
    path: '/'
  });

  // 獲取 Cookie
  const cookie = await cookieStore.get('sessionToken');
  console.log(cookie ? `獲取 Cookie：${cookie.value}` : '未找到 Cookie');

  // 刪除 Cookie
  await cookieStore.delete('sessionToken');
  console.log('Cookie 已刪除');
}

manageCookies();
```

## 解釋
使用 CookieStore API 時，有幾個常見的注意事項：
- 瀏覽器支持：並非所有瀏覽器都支持 CookieStore API，請檢查你的目標瀏覽器的兼容性。
- 異步操作：CookieStore 的操作是異步的，使用 `then()` 或 `async/await` 來處理結果。
- Cookie 大小限制：每個 Cookie 的大小有限制，通常為 4KB，請注意這一點以免造成數據丟失。

## 一句總結
CookieStore 是一個強大的 JavaScript API，用於簡化 Cookie 的創建、讀取和刪除操作，提升開發者的工作效率。