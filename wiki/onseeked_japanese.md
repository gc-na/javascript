<!--
Meta Description: # JavaScriptのonseekedイベント：動画や音声のシーク操作を管理する方法 ## 概要 JavaScriptの`onseeked`イベントは、メディア（音声や動画）の再生位置が変更されたときに発生します。このイベントは、ユーザーがメディアのシークバーを操作して再生位置を変更した際に、プ...
Meta Keywords: onseeked, video, イベントは, javascriptの, このイベントは
-->

# JavaScriptのonseekedイベント：動画や音声のシーク操作を管理する方法

## 概要
JavaScriptの`onseeked`イベントは、メディア（音声や動画）の再生位置が変更されたときに発生します。このイベントは、ユーザーがメディアのシークバーを操作して再生位置を変更した際に、プログラム側で特定の処理を実行するために使用されます。

## ドキュメンテーション
`onseeked`イベントは、HTMLMediaElementインターフェースの一部であり、`<audio>`や`<video>`要素に関連付けられています。このイベントは、メディアが新しい再生位置に正常にシークした後にトリガーされます。

### 用途
このイベントを利用することで、メディアの再生位置が変更された際に、ユーザーインターフェースの更新や、特定のデータの取得・処理を行うことが可能です。

### 使用方法
`onseeked`イベントは、JavaScriptのイベントリスナーを使用して設定されます。以下は基本的な構文です。

```javascript
const videoElement = document.querySelector('video');

videoElement.onseeked = function() {
    console.log('再生位置が変更されました。');
};
```

## 例
以下に、`onseeked`イベントの基本的な使用例を示します。

### 例1: 再生位置の変更を検知する
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');

    video.onseeked = function() {
        console.log('再生位置が変更されました。現在の位置: ' + video.currentTime);
    };
</script>
```

この例では、ユーザーが動画のシークバーを操作すると、コンソールに現在の再生位置が表示されます。

## 説明
`onseeked`イベントは、メディアが新しい位置に正常にシークしたときにのみ発生します。以下の点に注意してください：

- **非同期操作**: シーク操作が完了する前に`onseeked`が発生しないため、正確なタイミングでイベントが実行されます。
- **ブラウザの互換性**: `onseeked`イベントは、ほとんどの最新ブラウザでサポートされていますが、古いブラウザでは動作しない場合があります。実際の動作を確認することが重要です。
- **複数回のシーク**: ユーザーが連続してシークした場合、`onseeked`イベントはそれぞれのシーク操作後に発生します。

## 一文要約
JavaScriptの`onseeked`イベントは、メディアの再生位置が変更されたときに発生し、ユーザーのシーク操作に対して特定の処理を実行するために使用されます。