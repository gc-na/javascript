<!--
Meta Description: # JavaScriptの「oncanplay」イベント：音声と動画の再生準備完了通知 ## 概要 `oncanplay`は、HTML5のメディア要素（`<audio>`や`<video>`）に関連するイベントで、メディアが再生可能な状態になったことを示します。このイベントは、メディアのバッファリン...
Meta Keywords: oncanplay, videoelement, video, イベントは, javascript
-->

# JavaScriptの「oncanplay」イベント：音声と動画の再生準備完了通知

## 概要
`oncanplay`は、HTML5のメディア要素（`<audio>`や`<video>`）に関連するイベントで、メディアが再生可能な状態になったことを示します。このイベントは、メディアのバッファリングがある程度完了し、再生を開始できることを示します。

## ドキュメンテーション
### 目的
`oncanplay`イベントは、メディア要素が再生準備が整ったときに発生します。これにより、ユーザーはメディアの再生を開始するための操作を行ったり、UIを更新したりすることができます。

### 使用方法
`oncanplay`イベントは、HTML要素のイベントリスナーとして設定します。JavaScriptを使用して、イベントが発生した際の処理を定義します。

#### イベントリスナーの設定例
```javascript
const videoElement = document.getElementById('myVideo');

videoElement.oncanplay = function() {
    console.log("動画の再生が可能です。");
    // ここに再生開始の処理を追加できます
};
```

### 詳細
- イベントは、メディアがバッファリングを開始した後に、少なくとも一部のデータが読み込まれた時点で発生します。
- このイベントは、特にストリーミングメディアの際に重要です。ネットワークの速度や状態に応じて、再生可能になるタイミングが異なるためです。

## 例
以下は、`oncanplay`イベントを利用したシンプルな例です。

### HTML
```html
<video id="myVideo" width="640" height="360" controls>
    <source src="movie.mp4" type="video/mp4">
    お使いのブラウザはvideoタグに対応していません。
</video>
```

### JavaScript
```javascript
const videoElement = document.getElementById('myVideo');

videoElement.oncanplay = function() {
    console.log("動画の再生が可能です。");
    videoElement.play(); // 自動再生を開始
};
```

## 説明
- **一般的な落とし穴**: `oncanplay`イベントの発生は、メディアが完全に読み込まれていることを保証しません。ユーザーが再生を試みたときに、実際には再生ができない場合があるため、エラーハンドリングを考慮する必要があります。
- **ブラウザ互換性**: `oncanplay`は、HTML5をサポートしているほとんどのモダンブラウザで利用可能ですが、古いブラウザではサポートされていない場合があります。

## 一行の要約
`oncanplay`は、HTML5メディア要素が再生可能な状態になったことを通知するイベントです。