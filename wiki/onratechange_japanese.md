<!--
Meta Description: # onratechange：JavaScriptにおける音声や動画の再生速度変更イベント ## 概要 `onratechange`は、HTMLMediaElementインターフェースで使用されるイベントで、音声や動画の再生速度が変更された際に発生します。このイベントを使用することで、メディアプレー...
Meta Keywords: video, onratechange, playbackrate, function, イベントは
-->

# onratechange：JavaScriptにおける音声や動画の再生速度変更イベント

## 概要
`onratechange`は、HTMLMediaElementインターフェースで使用されるイベントで、音声や動画の再生速度が変更された際に発生します。このイベントを使用することで、メディアプレーヤーの再生速度に対するユーザーのインタラクションを監視し、適切なアクションを実行することができます。

## ドキュメンテーション
### 目的
`onratechange`イベントは、再生速度が変更されたときに特定の処理を実行するためのトリガーとして機能します。たとえば、ユーザーが再生速度を変更するUIを操作したときに、新しい速度に基づいて情報を更新することができます。

### 使用法
`onratechange`イベントは、HTMLMediaElement（`<video>`や`<audio>`要素）に割り当てることができます。イベントリスナーを設定することで、再生速度が変更された瞬間にコールバック関数を実行できます。

```javascript
const video = document.querySelector('video');

video.onratechange = function() {
    console.log(`再生速度が変更されました: ${video.playbackRate}`);
};
```

### 詳細
- **対象要素**: `<video>`および`<audio>`要素
- **プロパティ**:
  - `playbackRate`: 現在の再生速度を示す数値（1.0は通常速度）
- **イベントの発火タイミング**: ユーザーが再生速度を変更したとき（例：速度を1.5倍に設定した際）

## 例
以下は、`onratechange`イベントの基本的な使用例です。

```html
<video id="myVideo" width="600" controls>
    <source src="movie.mp4" type="video/mp4">
    あなたのブラウザは video タグをサポートしていません。
</video>

<script>
    const video = document.getElementById('myVideo');
    
    video.onratechange = function() {
        console.log(`現在の再生速度: ${video.playbackRate}`);
    };

    // 再生速度を変更する関数
    function changePlaybackRate(rate) {
        video.playbackRate = rate;
    }
</script>
```

## 説明
`onratechange`イベントに関連する一般的な落とし穴や注意点は以下の通りです。

- **対応ブラウザ**: 古いブラウザではサポートされていない場合があります。最新のブラウザでの動作を確認してください。
- **プレーヤーの状態**: 再生速度を変更する前に、メディアが再生中であることを確認する必要があります。再生されていない場合、速度を変更しても効果がない場合があります。
- **イベントの多重発火**: 速度変更が連続して行われた場合、複数回イベントが発火する可能性があります。必要に応じて、イベントリスナー内で状態を管理することをお勧めします。

## 一文の要約
`onratechange`は、JavaScriptで音声や動画の再生速度が変更された際に発生するイベントで、ユーザーインタラクションに基づいて適切な処理を実行するために使用されます。