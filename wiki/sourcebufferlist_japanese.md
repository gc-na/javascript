<!--
Meta Description: # SourceBufferList: JavaScriptにおけるソースバッファリストの詳細ガイド ## 概要 `SourceBufferList`は、Web Media APIの一部で、`MediaSource`オブジェクトに関連する複数の`SourceBuffer`オブジェクトを管理するための...
Meta Keywords: sourcebufferlist, mediasource, sourcebuffer, const, index
-->

# SourceBufferList: JavaScriptにおけるソースバッファリストの詳細ガイド

## 概要
`SourceBufferList`は、Web Media APIの一部で、`MediaSource`オブジェクトに関連する複数の`SourceBuffer`オブジェクトを管理するためのリストです。このクラスは、メディアストリームの動的な管理を可能にし、メディアデータを効率的に操作するための手段を提供します。

## ドキュメンテーション

### 目的
`SourceBufferList`は、`MediaSource`に追加されたすべての`SourceBuffer`を保持し、これらのバッファを操作するためのインターフェースを提供します。これにより、開発者は異なるメディアストリームを統合し、シームレスな再生体験を実現できます。

### 使用法
`SourceBufferList`は、`MediaSource`オブジェクトの`sourceBuffers`プロパティを介してアクセスできます。このプロパティは`SourceBufferList`のインスタンスを返します。

#### 主なメソッドとプロパティ
- `length`: `SourceBufferList`内の`SourceBuffer`の数を返します。
- `item(index)`: 指定したインデックスの`SourceBuffer`を返します。
- `forEach(callback)`: 各`SourceBuffer`に対して指定したコールバックを実行します。

### 詳細
`SourceBufferList`は読み取り専用のリストであり、直接的な操作はできません。新しい`SourceBuffer`を追加するには、`MediaSource`オブジェクトの`addSourceBuffer()`メソッドを使用します。

## 例

以下は、`SourceBufferList`を使用する基本的な例です。

```javascript
// MediaSourceオブジェクトの作成
const mediaSource = new MediaSource();
const videoElement = document.querySelector('video');

// メディアソースの準備
videoElement.src = URL.createObjectURL(mediaSource);

mediaSource.addEventListener('sourceopen', () => {
    // SourceBufferを追加
    const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8, vorbis"');
    
    // SourceBufferListを取得
    const sourceBufferList = mediaSource.sourceBuffers;
    
    console.log('SourceBufferの数:', sourceBufferList.length);
    
    // 各SourceBufferの処理
    sourceBufferList.forEach((buffer, index) => {
        console.log(`SourceBuffer ${index}:`, buffer);
    });
});
```

## 説明
`SourceBufferList`は、メディアの動的な再生やストリーミングにおいて非常に重要です。しかし、以下の点に注意する必要があります。

- **非同期性**: `SourceBuffer`の操作は非同期であるため、イベントリスナーを適切に設定しないと、予期しない動作が発生する可能性があります。
- **メディア形式**: `addSourceBuffer()`メソッドで指定するMIMEタイプは、サポートされているコーデックと一致している必要があります。そうでない場合、エラーが発生します。
- **リソース管理**: メモリの管理に注意し、不要になった`SourceBuffer`は適宜削除することが推奨されます。

## 一文要約
`SourceBufferList`は、`MediaSource`に関連する複数の`SourceBuffer`を管理するためのインターフェースであり、メディアストリームの効率的な操作を可能にします。