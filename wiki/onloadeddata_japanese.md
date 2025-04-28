<!--
Meta Description: # JavaScriptのonloadeddataイベント：完全ガイド ## 概要 `onloadeddata`は、HTMLMediaElement（動画や音声の要素）がメディアデータを読み込んだ際に発火するイベントです。このイベントは、メディアファイルが再生可能な状態になったことを示します。 ##...
Meta Keywords: onloadeddata, video, videoelement, html, イベントは
-->

# JavaScriptのonloadeddataイベント：完全ガイド

## 概要
`onloadeddata`は、HTMLMediaElement（動画や音声の要素）がメディアデータを読み込んだ際に発火するイベントです。このイベントは、メディアファイルが再生可能な状態になったことを示します。

## ドキュメンテーション
`onloadeddata`イベントは、ユーザーがメディアを再生する準備が整ったときに発生します。これは、音声や動画のデータが完全に読み込まれたことを意味します。主に、`<audio>`および`<video>`要素に関連付けられています。

### 目的
- メディアデータの読み込み状態を監視する。
- データが完全に読み込まれた後の処理を実行する。

### 使用法
`onloadeddata`イベントは、次のように設定できます。

```javascript
const videoElement = document.querySelector('video');

videoElement.onloadeddata = function() {
    console.log('メディアデータが読み込まれました。');
};
```

または、addEventListenerメソッドを使っても設定できます。

```javascript
videoElement.addEventListener('loadeddata', function() {
    console.log('メディアデータが読み込まれました。');
});
```

## 例
以下は、`onloadeddata`イベントを使用して動画の読み込みを確認する基本的な例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>onloadeddataイベントの例</title>
</head>
<body>
    <video width="320" height="240" controls>
        <source src="movie.mp4" type="video/mp4">
        ブラウザが動画をサポートしていません。
    </video>
    <script>
        const videoElement = document.querySelector('video');

        videoElement.onloadeddata = function() {
            console.log('動画データが読み込まれました。');
        };
    </script>
</body>
</html>
```

## 説明
`onloadeddata`イベントは、メディアコンテンツが再生可能になると発生しますが、すべてのデータが読み込まれたわけではありません。たとえば、動画の最初のフレームが読み込まれた時点でこのイベントが発火します。

### 注意点
- `onloadeddata`は、メディアのメタデータが読み込まれたときに発火する`onloadedmetadata`とは異なります。`onloadedmetadata`は、メディアの長さや寸法といった情報が利用可能になったときに発生します。
- ネットワークの問題やメディアファイルの形式がブラウザでサポートされていない場合、イベントは発火しないことがあります。

## 一行要約
`onloadeddata`は、HTMLMediaElementがメディアデータを読み込んだ際に発火するイベントです。