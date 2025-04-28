<!--
Meta Description: # AnalyserNode：JavaScript 中的音頻分析工具 ## 簡介 AnalyserNode 是 Web Audio API 中的一個重要組件，使開發者能夠對音頻數據進行實時分析，並獲取音頻的頻譜和時間域信息。這對於創建音頻可視化效果和音頻處理應用非常有用。 ## 文檔 ### 目的 ...
Meta Keywords: analysernode, audiocontext, const, analyser, javascript
-->

# AnalyserNode：JavaScript 中的音頻分析工具

## 簡介
AnalyserNode 是 Web Audio API 中的一個重要組件，使開發者能夠對音頻數據進行實時分析，並獲取音頻的頻譜和時間域信息。這對於創建音頻可視化效果和音頻處理應用非常有用。

## 文檔
### 目的
AnalyserNode 的主要目的是提供一個接口，讓開發者能夠獲取音頻信號的頻譜和時間域數據。這些數據可用於音頻可視化、音效控制和音頻分析等應用。

### 使用方法
要使用 AnalyserNode，首先需要創建一個 AudioContext，然後使用 `createAnalyser()` 方法來生成 AnalyserNode 實例。這個節點可以連接到音頻源，並且可以用來獲取音頻數據。

#### 基本語法：
```javascript
const audioContext = new AudioContext();
const analyserNode = audioContext.createAnalyser();
```

### 詳細信息
- **屬性**：
  - `fftSize`: 設置 FFT (快速傅立葉變換) 的大小，決定了頻譜的解析度。
  - `frequencyBinCount`: 返回 FFT 的一半大小，表示頻率數據的大小。
  - `smoothTimeConstant`: 設置平滑時間常數，用於平滑輸出數據。
  
- **方法**：
  - `getByteFrequencyData()`: 獲取頻率數據的字節數組。
  - `getByteTimeDomainData()`: 獲取時間域數據的字節數組。

## 範例
以下是使用 AnalyserNode 的基本範例：

```javascript
const audioContext = new AudioContext();
const analyser = audioContext.createAnalyser();
const source = audioContext.createMediaElementSource(audioElement);

source.connect(analyser);
analyser.connect(audioContext.destination);

const dataArray = new Uint8Array(analyser.frequencyBinCount);

function draw() {
    requestAnimationFrame(draw);
    analyser.getByteFrequencyData(dataArray);
    // 在這裡可以使用 dataArray 進行可視化
}
draw();
```

## 解釋
- **常見陷阱**：
  - 確保音頻上下文已經解鎖，因為某些瀏覽器需要用戶交互才能啟動音頻上下文。
  - 設置不當的 `fftSize` 可能會影響分析的準確性。
  
- **注意事項**：
  - AnalyserNode 是一個實時處理的節點，使用時要注意性能，尤其是在高更新率的可視化情況下。
  - 需要處理音頻流的延遲，特別是在進行實時音頻處理時。

## 一句話總結
AnalyserNode 是 Web Audio API 中用來實時分析音頻數據的工具，能夠有效獲取頻譜和時間域信息。