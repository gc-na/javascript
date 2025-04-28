<!--
Meta Description: # ConstantSourceNode：JavaScript 中的常量音源節點 ## 摘要 ConstantSourceNode 是 Web Audio API 中的一個功能，用於生成恆定的音頻信號，特別適合用於聲音合成和音效設計。 ## 文檔 ConstantSourceNode 讓開發者可以創...
Meta Keywords: audiocontext, constantsourcenode, constantsource, const, window
-->

# ConstantSourceNode：JavaScript 中的常量音源節點

## 摘要
ConstantSourceNode 是 Web Audio API 中的一個功能，用於生成恆定的音頻信號，特別適合用於聲音合成和音效設計。

## 文檔
ConstantSourceNode 讓開發者可以創建一個持續輸出的音頻信號，該信號的頻率和幅度是固定的。這個節點的主要用途是產生持續的音調或噪音，並且可以與其他音頻節點進行連接，以實現更複雜的音頻處理。

### 目的
ConstantSourceNode 主要用於生成恆定的音頻信號，這在音樂合成和音效設計中是非常有用的。它提供了一個簡單的方法來產生持續的聲音輸出，並且可以進行調整和處理。

### 使用方式
要使用 ConstantSourceNode，您需要首先創建一個 AudioContext 實例，然後使用該實例來創建 ConstantSourceNode。以下是基本的使用步驟：

1. 創建 AudioContext。
2. 創建 ConstantSourceNode。
3. 設置頻率和增益。
4. 連接到音頻輸出。
5. 開始播放。

```javascript
// 創建 AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// 創建 ConstantSourceNode
const constantSource = audioContext.createConstantSource();

// 設置頻率
constantSource.offset.value = 440; // 設定為 A4 音符（440 Hz）

// 連接到音頻輸出
constantSource.connect(audioContext.destination);

// 開始播放
constantSource.start();
```

## 範例
以下是幾個使用 ConstantSourceNode 的範例：

### 範例 1：生成固定頻率音調
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const constantSource = audioContext.createConstantSource();
constantSource.offset.value = 523.25; // C5 音符
constantSource.connect(audioContext.destination);
constantSource.start();
```

### 範例 2：創建白噪音
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const constantSource = audioContext.createConstantSource();
constantSource.offset.value = 0; // 設定為 0 以產生白噪音
constantSource.connect(audioContext.destination);
constantSource.start();
```

## 說明
使用 ConstantSourceNode 時，有幾個常見的陷阱和注意事項：

1. **不斷播放**：ConstantSourceNode 在開始後會持續輸出音頻，直到被停止。這意味著如果不適當管理，可能會導致音頻資源浪費。
2. **停止播放**：要停止 ConstantSourceNode 的音頻輸出，必須明確調用 `constantSource.stop()` 方法。
3. **連接**：確保在開始播放之前已經正確連接到音頻上下文的目標（如 destination）。

## 總結
ConstantSourceNode 是 Web Audio API 中一個強大的工具，能夠生成持續的音頻信號，非常適合音樂合成和音效設計應用。