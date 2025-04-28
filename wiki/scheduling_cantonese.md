<!--
Meta Description: # JavaScript 排程 (Scheduling)：實現非同步任務的有效管理 ## 簡介 JavaScript 排程是指在特定時間或條件下執行代碼的能力。這種技術在開發應用程式時特別重要，因為它能有效地管理非同步任務，例如定時器、延遲執行的功能和事件調度。 ## 文件 排程的主要目的是幫助開發...
Meta Keywords: javascript, setinterval, settimeout, callback, args
-->

# JavaScript 排程 (Scheduling)：實現非同步任務的有效管理

## 簡介
JavaScript 排程是指在特定時間或條件下執行代碼的能力。這種技術在開發應用程式時特別重要，因為它能有效地管理非同步任務，例如定時器、延遲執行的功能和事件調度。

## 文件
排程的主要目的是幫助開發者控制何時執行特定的程式碼段。JavaScript 提供了幾種原生方法來實現排程，最常見的有 `setTimeout()` 和 `setInterval()`。

### `setTimeout()`
- **用途**：在指定的毫秒數後執行一個函數。
- **語法**：
  ```javascript
  setTimeout(callback, delay, ...args);
  ```
  - `callback`：要執行的函數。
  - `delay`：延遲的毫秒數。
  - `...args`：可選的附加參數，將會傳遞給 `callback`。

### `setInterval()`
- **用途**：每隔指定的毫秒數執行一次函數。
- **語法**：
  ```javascript
  setInterval(callback, interval, ...args);
  ```
  - `callback`：要執行的函數。
  - `interval`：執行的間隔時間，單位為毫秒。
  - `...args`：可選的附加參數，將會傳遞給 `callback`。

## 範例
### 使用 `setTimeout()`
```javascript
console.log("開始計時...");
setTimeout(() => {
  console.log("3秒後執行的代碼");
}, 3000);
```

### 使用 `setInterval()`
```javascript
let count = 0;
const intervalId = setInterval(() => {
  count++;
  console.log(`已執行 ${count} 次`);
  if (count === 5) {
    clearInterval(intervalId); // 停止執行
    console.log("停止計時");
  }
}, 1000);
```

## 解釋
在使用排程時，開發者需注意以下幾點：
- **非同步行為**：`setTimeout()` 和 `setInterval()` 會將回調函數放入事件隊列，這意味著它們不會阻塞主執行線程。
- **內存洩漏**：如果不清除不再需要的計時器，可能會導致內存洩漏。使用 `clearTimeout()` 和 `clearInterval()` 來停止計時器。
- **精確度**：`setInterval()` 的執行不一定準確，因為它可能會受到其他代碼執行的影響，導致延遲。

## 一句總結
JavaScript 排程技術允許開發者有效管理非同步任務的執行時機。