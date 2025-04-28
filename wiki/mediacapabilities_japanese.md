<!--
Meta Description: # MediaCapabilities: JavaScriptでのメディア能力の確認 ## 概要 `MediaCapabilities`は、JavaScriptを使用して、ブラウザがサポートするメディアのエンコーディングやデコーディングの能力を確認するためのインターフェースです。このAPIを活用する...
Meta Keywords: mediacapabilities, query, video, console, log
-->

# MediaCapabilities: JavaScriptでのメディア能力の確認

## 概要
`MediaCapabilities`は、JavaScriptを使用して、ブラウザがサポートするメディアのエンコーディングやデコーディングの能力を確認するためのインターフェースです。このAPIを活用することで、開発者は特定のメディア形式（動画や音声）の再生が適切に行えるかどうかを判断できます。

## ドキュメンテーション
`MediaCapabilities`インターフェースは、メディアコンテンツの特性に基づいて、ブラウザのデコーディング能力を確認するためのメソッドを提供します。このAPIは、情報を取得するために`query()`メソッドを使用します。

### 目的
- メディアコンテンツの再生可能性を確認する。
- ブラウザの対応するコーデックやフォーマットを調べる。

### 使用法
以下は、`MediaCapabilities`を使用する基本的な流れです。

1. `MediaCapabilities`オブジェクトを取得します。
2. `query()`メソッドを使用して、特定のメディア形式の能力を照会します。

### メソッド
- **query()**: 指定されたメディアの形式、コーデック、ビットレート、フレームレートなどの情報を基に、ブラウザがそのメディアを再生できるかどうかを返します。

### パラメータ
`query()`メソッドは、次のようなオブジェクトを引数として受け取ります:
- `type`: メディアのタイプ（例: "video"、"audio"）。
- `video`: 動画の詳細設定（オプション）。
- `audio`: 音声の詳細設定（オプション）。

### 戻り値
`query()`メソッドは、Promiseを返し、結果として`MediaCapabilitiesInfo`オブジェクトが得られます。このオブジェクトには、サポートされているかどうか、ハードウェアアクセラレーションの有無、再生のパフォーマンスに関する情報が含まれます。

## 例
以下は、`MediaCapabilities`を使用した基本的な例です。

```javascript
if ('mediaCapabilities' in navigator) {
    const mediaQuery = {
        type: 'video',
        video: {
            contentType: 'video/mp4; codecs="avc1.42E01E, mp4a.40.2"',
            width: 1280,
            height: 720,
            bitrate: 1200000,
            framerate: 30
        }
    };

    navigator.mediaCapabilities.query(mediaQuery)
        .then((capabilities) => {
            if (capabilities.supported) {
                console.log('メディアはサポートされています！');
            } else {
                console.log('メディアはサポートされていません。');
            }
        })
        .catch((error) => {
            console.error('エラーが発生しました:', error);
        });
} else {
    console.log('MediaCapabilities APIはこのブラウザではサポートされていません。');
}
```

## 説明
- **共通の落とし穴**: `MediaCapabilities`はすべてのブラウザでサポートされているわけではありません。古いブラウザや特定のモバイルブラウザでは、APIが無効な場合があります。そのため、事前にサポート状況を確認することが重要です。
- **パフォーマンスの考慮**: すべてのメディア形式が、ブラウザのハードウェアアクセラレーションを利用できるわけではありません。特に低スペックのデバイスでは、パフォーマンスが低下する可能性があります。

## 一文の要約
`MediaCapabilities`は、JavaScriptを用いてブラウザのメディア再生能力を確認するインターフェースです。