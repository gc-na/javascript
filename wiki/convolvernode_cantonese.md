<!--
Meta Description: # ConvolverNode：JavaScript 中音效處理的關鍵工具 ## 簡介 ConvolverNode 是 Web Audio API 中的一個重要組件，用於實現音頻的混響效果。通過使用卷積運算，開發者可以將音頻信號與預定義的脈衝響應進行處理，以模擬不同環境中的音響特性。 ## 文件說明...
Meta Keywords: audiocontext, convolvernode, convolver, buffer, source
-->

# ConvolverNode：JavaScript 中音效處理的關鍵工具

## 簡介
ConvolverNode 是 Web Audio API 中的一個重要組件，用於實現音頻的混響效果。通過使用卷積運算，開發者可以將音頻信號與預定義的脈衝響應進行處理，以模擬不同環境中的音響特性。

## 文件說明
ConvolverNode 的主要目的在於將音頻信號與一個響應（通常是錄製的環境聲音）進行卷積運算，從而產生逼真的混響效果。它主要用於音頻應用程序中的音效增強，特別是在音樂製作和遊戲開發中。

### 用法
1. **創建一個 AudioContext**：
   ```javascript
   const audioContext = new AudioContext();
   ```

2. **創建 ConvolverNode**：
   ```javascript
   const convolver = audioContext.createConvolver();
   ```

3. **設置脈衝響應**：
   你可以將一段音頻作為脈衝響應來設置 ConvolverNode：
   ```javascript
   fetch('path/to/impulse-response.wav')
       .then(response => response.arrayBuffer())
       .then(data => audioContext.decodeAudioData(data))
       .then(buffer => {
           convolver.buffer = buffer;
       });
   ```

4. **連接音頻源與 ConvolverNode**：
   ```javascript
   const source = audioContext.createBufferSource();
   source.buffer = yourAudioBuffer; // 你的音頻緩衝區
   source.connect(convolver);
   convolver.connect(audioContext.destination);
   ```

5. **播放音頻**：
   ```javascript
   source.start();
   ```

## 例子
以下是一個簡單的示範，展示如何使用 ConvolverNode 創建混響效果：

```javascript
const audioContext = new AudioContext();
const convolver = audioContext.createConvolver();

fetch('path/to/impulse-response.wav')
    .then(response => response.arrayBuffer())
    .then(data => audioContext.decodeAudioData(data))
    .then(buffer => {
        convolver.buffer = buffer;

        const source = audioContext.createBufferSource();
        source.buffer = yourAudioBuffer; // 你的音頻緩衝區
        source.connect(convolver);
        convolver.connect(audioContext.destination);
        source.start();
    });
```

## 解釋
在使用 ConvolverNode 時，有一些常見的陷阱和注意事項：
- **脈衝響應的格式**：確保使用的脈衝響應文件格式正確，通常是 WAV 格式。
- **音頻上下文的狀態**：在播放音頻之前，確保音頻上下文處於“運行”狀態。如果上下文處於“停止”狀態，則需要調用 `audioContext.resume()`。
- **性能考量**：使用高質量的脈衝響應會增加 CPU 的負擔，特別是在實時音訊處理時。

## 一句話總結
ConvolverNode 是 Web Audio API 中的關鍵組件，專門用於創建逼真的混響效果，通過卷積運算將音頻信號與脈衝響應結合。