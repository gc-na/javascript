<!--
Meta Description: # onplaying: JavaScriptにおける再生イベントの管理 ## 概要 `onplaying`は、HTML5のメディア要素（`<audio>`や`<video>`）に関連するイベントで、メディアが再生を開始したときに発生します。このイベントは、ユーザーが再生ボタンをクリックしたり、自動...
Meta Keywords: onplaying, video, myvideo, イベントは, audio
-->

# onplaying: JavaScriptにおける再生イベントの管理

## 概要
`onplaying`は、HTML5のメディア要素（`<audio>`や`<video>`）に関連するイベントで、メディアが再生を開始したときに発生します。このイベントは、ユーザーが再生ボタンをクリックしたり、自動再生が始まった場合にトリガーされます。

## ドキュメンテーション
`onplaying`イベントは、メディア要素が再生中であることを示すために使用されます。これは、メディアが一時停止状態から再生状態に変わったときに発生し、再生の進行状況をトラッキングするために役立ちます。

### 使用方法
`onplaying`イベントは、JavaScriptを使ってメディア要素にリスナーを追加することで使用できます。以下はその基本的な構文です。

```javascript
const videoElement = document.querySelector('video');

videoElement.onplaying = function() {
    console.log('動画が再生中です');
};
```

### 詳細
- **対象**: `<audio>`および`<video>`要素
- **イベントの発火**: メディアが再生を開始したとき
- **イベントオブジェクト**: `onplaying`イベントには、標準のイベントオブジェクトが渡されます。

## 例
以下は、`onplaying`イベントの基本的な使用例です。

```html
<video id="myVideo" width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    お使いのブラウザは動画タグをサポートしていません。
</video>

<script>
    const myVideo = document.getElementById('myVideo');

    myVideo.onplaying = function() {
        console.log('動画が再生されました！');
    };
</script>
```

## 説明
- **一般的な落とし穴**: `onplaying`イベントは、再生が開始されたときにのみ発生します。ユーザーが一時停止した後、再度再生を開始するとイベントは再度発火しますが、同じメディア要素で他の再生イベント（`onplay`や`onpause`など）と混同しないよう注意が必要です。
- **ブラウザの互換性**: ほとんどのモダンブラウザは`onplaying`イベントをサポートしていますが、古いバージョンのブラウザでは動作しない可能性があります。互換性を確認することをお勧めします。

## 一文要約
`onplaying`は、HTML5メディア要素が再生を開始したときに発生するイベントで、再生の状態を管理するために使用されます。