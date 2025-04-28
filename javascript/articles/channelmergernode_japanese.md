<!--
Meta Description: # ChannelMergerNode: JavaScriptにおける音声チャネルのマージ機能 ## 概要 `ChannelMergerNode`は、Web Audio APIの一部であり、複数のオーディオチャネルを1つのチャネルストリームに統合するために使用されます。これにより、音声データを効率的...
Meta Keywords: audiocontext, channelmergernode, const, channelmerger, connect
-->

# ChannelMergerNode: JavaScriptにおける音声チャネルのマージ機能

## 概要
`ChannelMergerNode`は、Web Audio APIの一部であり、複数のオーディオチャネルを1つのチャネルストリームに統合するために使用されます。これにより、音声データを効率的に処理し、再生することができます。

## ドキュメント
### 目的
`ChannelMergerNode`は、音声信号を複数のチャネルから1つの出力ストリームに結合するためのノードです。特に、ステレオやサラウンドサウンドなどの複数チャネルの音声データを扱う際に非常に便利です。

### 使用法
`ChannelMergerNode`は、`AudioContext`オブジェクトを介して作成されます。以下はその基本的な構文です：

```javascript
const audioContext = new AudioContext();
const channelMerger = audioContext.createChannelMerger(numberOfInputs);
```

- `numberOfInputs`: マージするチャネルの数を指定します（最大で32チャネルまで対応）。

### 詳細
- `ChannelMergerNode`は、オーディオの出力を1つにまとめるための強力なツールです。
- 入力チャネルは`connect()`メソッドを使用して接続できます。
- 出力は`AudioNode`として他のノードに接続することができます。

## 例
以下は、`ChannelMergerNode`を使用して2つのオーディオチャネルをマージする基本的な例です。

```javascript
const audioContext = new AudioContext();
const channelMerger = audioContext.createChannelMerger(2);

// 2つのオーディオソースを作成
const source1 = audioContext.createBufferSource();
const source2 = audioContext.createBufferSource();

// オーディオデータを設定（省略）

// ソースをチャネルマージャーに接続
source1.connect(channelMerger, 0, 0); // チャネル1
source2.connect(channelMerger, 0, 1); // チャネル2

// マージされた出力をスピーカーに接続
channelMerger.connect(audioContext.destination);

// ソースを再生
source1.start();
source2.start();
```

## 説明
`ChannelMergerNode`を使用する際に注意すべき点は以下の通りです。

- **入力チャネルの数**: `numberOfInputs`の指定は、後から変更できないため、必要なチャネル数を正確に設定する必要があります。
- **オーディオデータの準備**: 接続するソースノード（`AudioBufferSourceNode`など）は、オーディオデータを事前に設定しておく必要があります。
- **ブラウザの互換性**: Web Audio APIは、すべてのブラウザで同じようにサポートされているわけではないため、事前に互換性を確認することが重要です。

## 一文要約
`ChannelMergerNode`は、複数のオーディオチャネルを1つのストリームに統合するJavaScriptのWeb Audio APIの機能です。