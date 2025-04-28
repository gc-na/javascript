<!--
Meta Description: # AnimationPlaybackEvent (アニメーション再生イベント) に関する詳細ガイド ## 概要 `AnimationPlaybackEvent` は、CSSアニメーションやWebアニメーションAPIに関連するイベントを表すJavaScriptのインターフェイスです。このイベントは、...
Meta Keywords: animation, animationplaybackevent, cancel, addeventlistener, event
-->

# AnimationPlaybackEvent (アニメーション再生イベント) に関する詳細ガイド

## 概要
`AnimationPlaybackEvent` は、CSSアニメーションやWebアニメーションAPIに関連するイベントを表すJavaScriptのインターフェイスです。このイベントは、アニメーションの再生、停止、または再開に関する情報を提供します。

## ドキュメンテーション
`AnimationPlaybackEvent` は、アニメーションの再生状況を把握するために使用されます。特に、アニメーションが開始、停止、または再開されたときにトリガーされるイベントです。このイベントは、アニメーションの進行状況を監視したり、ユーザーインタラクションに基づいてアニメーションの動作を変更するために役立ちます。

### プロパティ
- **type**: イベントの種類を示す文字列。通常は "finish" や "cancel" など。
- **target**: イベントが発生した要素。
- **currentTime**: アニメーションの現在の再生時間（秒）。
- **timelineTime**: アニメーションのタイムライン上の時間（秒）。

### 使用法
以下のコードスニペットは、`AnimationPlaybackEvent` を使用してアニメーションの状態を監視する基本的な方法を示しています。

```javascript
const animation = document.querySelector('.my-animation');

animation.addEventListener('finish', (event) => {
    console.log('アニメーションが完了しました。');
});

animation.addEventListener('cancel', (event) => {
    console.log('アニメーションがキャンセルされました。');
});
```

## 例
### アニメーション再生の監視
以下の例では、アニメーションが完了したときとキャンセルされたときにそれぞれメッセージを表示します。

```html
<div class="my-animation" style="width: 100px; height: 100px; background-color: blue;"></div>
<style>
  .my-animation {
      animation: myAnimation 2s forwards;
  }
  @keyframes myAnimation {
      from { transform: translateX(0); }
      to { transform: translateX(200px); }
  }
</style>
<script>
  const animation = document.querySelector('.my-animation');

  animation.addEventListener('finish', (event) => {
      console.log('アニメーションが完了しました。');
  });

  animation.addEventListener('cancel', (event) => {
      console.log('アニメーションがキャンセルされました。');
  });

  // アニメーションをキャンセルする
  setTimeout(() => {
      animation.cancel();
  }, 1000);
</script>
```

## 説明
`AnimationPlaybackEvent` を使用する際の一般的な注意点や落とし穴は以下の通りです。

- **ブラウザの互換性**: `AnimationPlaybackEvent` はすべてのブラウザでサポートされているわけではありません。使用する前にブラウザの互換性を確認してください。
- **非同期処理**: アニメーションの状態を監視する際、非同期処理に注意が必要です。アニメーションの状態が変更された後に正しくイベントがトリガーされることを確認してください。

## 一文の要約
`AnimationPlaybackEvent` は、アニメーションの再生状況を監視するためのイベントで、アニメーションが完了またはキャンセルされた際の情報を提供します。