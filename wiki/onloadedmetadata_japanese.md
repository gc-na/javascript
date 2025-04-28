<!--
Meta Description: # JavaScriptの「onloadedmetadata」イベントの完全ガイド ## 概要 `onloadedmetadata`は、HTMLMediaElement（例えば、`<video>`や`<audio>`）のメタデータが読み込まれたときに発火するイベントです。このイベントを利用することで...
Meta Keywords: video, onloadedmetadata, console, log, 例えば
-->

# JavaScriptの「onloadedmetadata」イベントの完全ガイド

## 概要
`onloadedmetadata`は、HTMLMediaElement（例えば、`<video>`や`<audio>`）のメタデータが読み込まれたときに発火するイベントです。このイベントを利用することで、メディアの情報（例えば、長さやビデオの幅と高さなど）を取得することができます。

## ドキュメンテーション
### 目的
`onloadedmetadata`イベントは、メディアファイルのメタデータが完全に読み込まれた際にトリガーされ、ユーザーや開発者がメディアの特性を把握するための重要な情報を提供します。

### 使用法
このイベントは、HTMLMediaElementオブジェクト（`<audio>`や`<video>`）に直接関連付けられます。イベントリスナーを追加することで、メタデータが読み込まれたときに特定の処理を実行できます。

### 詳細
- **対応ブラウザ**: 最新の主要ブラウザ（Chrome, Firefox, Safari, Edgeなど）がサポートしています。
- **イベントのプロパティ**: `event.target`を使用してメディア要素にアクセスできます。
- **イベントの発火タイミング**: メタデータが読み込まれた後に発火するため、メディアの再生準備が整ったことを示します。

## 例
以下は、`onloadedmetadata`イベントを使用した基本的な例です。

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    お使いのブラウザは動画タグに対応していません。
</video>

<script>
    const video = document.getElementById('myVideo');

    video.onloadedmetadata = function() {
        console.log('動画の長さ:', video.duration);
        console.log('動画の幅:', video.videoWidth);
        console.log('動画の高さ:', video.videoHeight);
    };
</script>
```

## 説明
`onloadedmetadata`イベントを使用する際の一般的な落とし穴や注意点は以下の通りです。

- **非同期処理**: メタデータが読み込まれる前にイベントリスナーが設定されていない場合、イベントが発火しないことがあります。必ずメディア要素の作成後にリスナーを設定してください。
- **ブラウザの互換性**: 一部の古いブラウザではこのイベントがサポートされていない可能性があります。必要に応じてフォールバックを用意すると良いでしょう。
- **メディアの種類**: `onloadedmetadata`はオーディオおよびビデオメディアでのみ使用可能です。他のメディアタイプには適用されません。

## 一文要約
`onloadedmetadata`は、HTMLMediaElementのメタデータが読み込まれた際に発火するイベントで、メディアの特性を把握するのに役立ちます。