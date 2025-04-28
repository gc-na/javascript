<!--
Meta Description: # JavaScript の onemptied イベントについて ## 概要 `onemptied` イベントは、HTMLMediaElement（音声や動画を扱う要素）が空になったときに発生するイベントです。このイベントは、メディアコンテンツが完全に再生され、再生が終了した後や、ユーザーがメディ...
Meta Keywords: onemptied, video, videoelement, イベントは, document
-->

# JavaScript の onemptied イベントについて

## 概要
`onemptied` イベントは、HTMLMediaElement（音声や動画を扱う要素）が空になったときに発生するイベントです。このイベントは、メディアコンテンツが完全に再生され、再生が終了した後や、ユーザーがメディアを停止した際に発生します。

## ドキュメンテーション
`onemptied` イベントは、主に `<audio>` や `<video>` 要素に関連しています。このイベントを使用することで、メディアコンテンツが空になった時点で特定の処理を行うことができます。

### 目的
- メディアが空になった時の処理を行う。
- ユーザーインターフェースの更新や通知を行う。

### 使用法
`onemptied` イベントは、メディア要素のイベントリスナーとして設定します。以下のように記述します。

```javascript
const videoElement = document.getElementById('myVideo');

videoElement.onemptied = function() {
    console.log('メディアが空になりました');
};
```

## 例
以下は、`onemptied` イベントの基本的な使用例です。

### 例1: メディアが空になったときのメッセージ表示

```html
<video id="myVideo" width="600" controls>
    <source src="movie.mp4" type="video/mp4">
    ブラウザがビデオタグをサポートしていません。
</video>

<script>
    const videoElement = document.getElementById('myVideo');

    videoElement.onemptied = function() {
        alert('動画が終了しました。');
    };
</script>
```

### 例2: メディアが空になったときの UI 更新

```html
<button id="playButton">再生</button>
<video id="myVideo" width="600" controls>
    <source src="movie.mp4" type="video/mp4">
</video>
<div id="status"></div>

<script>
    const videoElement = document.getElementById('myVideo');
    const statusDiv = document.getElementById('status');

    videoElement.onemptied = function() {
        statusDiv.innerText = 'メディアが空になりました。';
    };

    document.getElementById('playButton').onclick = function() {
        videoElement.play();
    };
</script>
```

## 説明
`onemptied` イベントは、メディアが終了したときに発生しますが、注意すべき点があります。例えば、ユーザーがビデオを手動で停止したときもこのイベントが発生します。また、`onemptied` は、メディアがキューに追加されていない場合にも発生するため、プログラムの流れによっては予期しないタイミングで発生することがあります。

### 注意点
- `onemptied` イベントは、メディアが完全に終了した場合や手動で停止された場合にも発生します。
- ブラウザやデバイスによっては、イベントの動作が異なる場合がありますので、テストが必要です。

## 1行要約
`onemptied` イベントは、メディア要素が空になったときに発生し、特定の処理を行うために使用されます。