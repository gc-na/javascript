<!--
Meta Description: # onSeeking: JavaScriptにおけるメディアの再生位置の変更イベント ## 概要 `onSeeking`は、HTMLMediaElement（音声や動画を扱う要素）に関連するイベントで、ユーザーがメディアの再生位置を変更したときに発生します。このイベントは、ユーザーがシークバーを操...
Meta Keywords: onseeking, videoelement, イベントは, video, myvideo
-->

# onSeeking: JavaScriptにおけるメディアの再生位置の変更イベント

## 概要
`onSeeking`は、HTMLMediaElement（音声や動画を扱う要素）に関連するイベントで、ユーザーがメディアの再生位置を変更したときに発生します。このイベントは、ユーザーがシークバーを操作した際にトリガーされ、メディアの再生位置を追跡したり、特定のアクションを実行するのに役立ちます。

## ドキュメント
`onSeeking`イベントは、HTMLMediaElementの一部であり、ユーザーがメディアの再生位置を変更する際に発生します。このイベントは、次のような要素で使用されます：

- `<audio>` 要素
- `<video>` 要素

### 目的
`onSeeking`を使用することで、メディアの再生位置が変更された際に特定の処理を実行することができます。これにより、ユーザーエクスペリエンスを向上させたり、デバッグ情報を収集したりすることが可能になります。

### 使用法
`onSeeking`イベントは、次のようにHTMLMediaElementにイベントリスナーを追加することで使用できます。

```javascript
const videoElement = document.getElementById('myVideo');

videoElement.onseeking = function() {
    console.log('ユーザーが再生位置を変更しました。');
};
```

## 例
以下は、`onSeeking`イベントを使用した基本的な例です。

```html
<video id="myVideo" width="600" controls>
    <source src="movie.mp4" type="video/mp4">
    お使いのブラウザは、videoタグをサポートしていません。
</video>

<script>
    const videoElement = document.getElementById('myVideo');

    videoElement.onseeking = function() {
        console.log('再生位置が変更されました。現在の位置: ' + videoElement.currentTime);
    };
</script>
```

この例では、ユーザーがビデオの再生位置を変更するたびに、現在の再生位置がコンソールに表示されます。

## 説明
- **一般的な落とし穴**: `onSeeking`イベントは、ユーザーがシークバーを動かしたときにのみ発生します。プログラムによって再生位置が変更された場合（例えば、`currentTime`プロパティを直接変更した場合）には発生しません。
- **注意事項**: `onSeeking`イベントは、ユーザーの操作に基づくイベントであるため、メディアがシーク中である間、他のイベント（例えば`onSeeked`）も考慮する必要があります。`onSeeked`は、シークが完了した後に発生します。

## 一文要約
`onSeeking`は、ユーザーがメディアの再生位置を変更した際に発生するイベントで、主にHTMLMediaElementで使用されます。