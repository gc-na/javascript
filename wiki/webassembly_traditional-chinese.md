<!--
Meta Description: # WebAssembly 與 JavaScript 的關聯 ## 摘要 WebAssembly（簡稱Wasm）是一種高效的二進制指令格式，旨在作為網頁應用程序的可攜帶、低級別的運行時，並能與JavaScript緊密整合，提升網頁性能。 ## 文檔 WebAssembly 是由 W3C 和其他技術組...
Meta Keywords: webassembly, add, const, int, javascript
-->

# WebAssembly 與 JavaScript 的關聯

## 摘要
WebAssembly（簡稱Wasm）是一種高效的二進制指令格式，旨在作為網頁應用程序的可攜帶、低級別的運行時，並能與JavaScript緊密整合，提升網頁性能。

## 文檔
WebAssembly 是由 W3C 和其他技術組織共同開發的標準，主要目的是讓開發者能夠用不同的語言（如C、C++、Rust等）編寫程式，並將其編譯成Wasm格式，然後在瀏覽器中運行。這樣可以大幅提升計算性能，尤其是對於需要密集運算的應用，如遊戲、視頻編輯和科學計算。

### 主要用途
- **性能提升**：Wasm在執行速度上接近原生應用程序，特別適合計算密集型任務。
- **跨平台支持**：Wasm應用可以在任何支持Wasm的環境中運行，無需修改代碼。
- **與JavaScript整合**：Wasm可以與JavaScript無縫互操作，讓開發者能夠利用兩者的優勢。

### 使用方式
要在JavaScript中使用WebAssembly，首先需要將源代碼編譯為Wasm格式，然後使用JavaScript的`WebAssembly`API進行加載和執行。以下是基本步驟：

1. 編譯源代碼為Wasm格式。
2. 使用JavaScript的`WebAssembly.instantiate`方法加載Wasm模塊。
3. 調用Wasm導出的函數。

## 範例
以下是如何在JavaScript中加載和執行WebAssembly模塊的基本示例：

### 編譯C代碼為Wasm
假設我們有一個簡單的C函數：

```c
int add(int a, int b) {
    return a + b;
}
```
使用Emscripten編譯成Wasm：

```bash
emcc add.c -o add.wasm -s MODULARIZE=1 -s EXPORT_NAME="createAddModule"
```

### 在JavaScript中使用
使用JavaScript加載和調用Wasm模塊：

```javascript
const fs = require('fs');

async function loadWasm() {
    const wasmBuffer = fs.readFileSync('add.wasm');
    const { instance } = await WebAssembly.instantiate(wasmBuffer);
    const result = instance.exports.add(5, 3);
    console.log(result); // 輸出: 8
}

loadWasm();
```

## 解釋
在使用WebAssembly時，開發者需要注意以下幾點：

- **安全性**：WebAssembly運行在沙盒環境中，這意味著它不能直接訪問DOM或其他瀏覽器API。
- **性能考量**：雖然Wasm提供了接近原生的性能，但不一定適合所有場景，對於簡單的邏輯處理，JavaScript仍可能更高效。
- **調試困難**：由於Wasm是二進制格式，調試過程可能不如JavaScript直觀。

## 一句話總結
WebAssembly是提升JavaScript性能的重要工具，特別適合計算密集型的應用。