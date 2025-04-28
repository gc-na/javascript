<!--
Meta Description: # JavaScript BroadcastChannel API：實現多窗口間的即時通訊 ## 簡介 `BroadcastChannel` 是一個 JavaScript API，允許同一個源的不同瀏覽器上下文（如標籤頁或 iframe）之間進行即時通訊。這使得在多個視窗或標籤頁開啟的應用程式能夠輕...
Meta Keywords: broadcastchannel, channel, javascript, new, event
-->

# JavaScript BroadcastChannel API：實現多窗口間的即時通訊

## 簡介
`BroadcastChannel` 是一個 JavaScript API，允許同一個源的不同瀏覽器上下文（如標籤頁或 iframe）之間進行即時通訊。這使得在多個視窗或標籤頁開啟的應用程式能夠輕鬆地共享資料和狀態。

## 文檔
### 目的
`BroadcastChannel` 旨在簡化多上下文之間的資料傳遞，特別是在需要即時更新的應用場景，例如即時聊天應用或協作工具。

### 使用方式
使用 `BroadcastChannel` 的基本步驟如下：

1. **創建一個新的 `BroadcastChannel` 實例**：
   ```javascript
   const channel = new BroadcastChannel('channel_name');
   ```

2. **發送消息**：
   使用 `postMessage` 方法將資料發送到所有訂閱此頻道的上下文：
   ```javascript
   channel.postMessage('Hello, World!');
   ```

3. **接收消息**：
   使用 `onmessage` 事件監聽器接收來自頻道的消息：
   ```javascript
   channel.onmessage = (event) => {
       console.log(event.data);
   };
   ```

4. **關閉頻道**：
   當不再需要通訊時，應關閉頻道以釋放資源：
   ```javascript
   channel.close();
   ```

### 詳細說明
- **頻道名稱**：`BroadcastChannel` 的名稱在所有上下文中必須相同，這樣消息才能被正確接收。
- **支持的類型**：可以通過 `postMessage` 發送的資料類型包括字串、物件（必須是可序列化的）等。
- **性能考慮**：由於消息是廣播的，所有訂閱該頻道的上下文都會接收到消息，因此在高頻率發送的情況下可能影響性能。

## 範例
### 基本示範
```javascript
// 在一個標籤頁中
const channel = new BroadcastChannel('my_channel');

channel.onmessage = (event) => {
    console.log('Received:', event.data);
};

channel.postMessage('Hello from the first tab!');

// 在另一個標籤頁中
const channel2 = new BroadcastChannel('my_channel');

channel2.postMessage('Hello from the second tab!');
```

### 進階示範
```javascript
const channel = new BroadcastChannel('notifications');

channel.onmessage = (event) => {
    if (event.data.type === 'new-message') {
        console.log('New message received:', event.data.content);
    }
};

channel.postMessage({ type: 'new-message', content: 'Hello everyone!' });
```

## 解釋
- **常見陷阱**：`BroadcastChannel` 僅在同一來源下的上下文之間有效，跨不同來源無法使用。
- **瀏覽器支持**：目前大多數現代瀏覽器均支持 `BroadcastChannel`，但在編寫代碼之前，應檢查目標瀏覽器的兼容性。
- **數據類型限制**：傳遞的對象必須是可序列化的，否則將導致錯誤。

## 總結
`BroadcastChannel` API 提供了一種簡單易用的方式來實現多窗口間的即時通訊，適合用於需要即時更新的 Web 應用。