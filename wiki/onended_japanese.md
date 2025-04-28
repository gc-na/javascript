<!--
Meta Description: # JavaScriptの「onended」イベント: 音声と動画の終了処理 ## 概要 「onended」は、HTMLMediaElementインターフェースに関連するイベントで、メディアの再生が終了した際に発生します。このイベントは、音声や動画の再生が完了したことを検知し、次のアクションを実行す...
Meta Keywords: onended, audio, video, script, イベントは
-->

# JavaScriptの「onended」イベント: 音声と動画の終了処理

## 概要
「onended」は、HTMLMediaElementインターフェースに関連するイベントで、メディアの再生が終了した際に発生します。このイベントは、音声や動画の再生が完了したことを検知し、次のアクションを実行するために利用されます。

## ドキュメンテーション
### 目的
「onended」イベントは、ユーザーがメディアコンテンツを再生した後、その再生が完了したときにトリガーされます。これにより、再生後の処理（例えば、再生リストの次のメディアを再生する、特定のメッセージを表示するなど）を行うことができます。

### 使用法
「onended」イベントは、JavaScriptでメディア要素に対してイベントリスナーを追加することで使用します。以下の手順で設定できます。

1. メディア要素（`<audio>`または`<video>`）を取得します。
2. `onended`プロパティまたは`addEventListener`メソッドを使用してイベントリスナーを登録します。

### 詳細
- `HTMLMediaElement.onended`は、再生が終了したときに呼び出される関数を指定します。
- イベントリスナーは、メディアが自動的に終了した場合や、ユーザーが手動で再生を停止した場合の両方でトリガーされます。

## 例
以下は、「onended」イベントを使用した基本的な例です。

```html
<audio id="myAudio" controls>
  <source src="audiofile.mp3" type="audio/mpeg">
  お使いのブラウザはaudio要素をサポートしていません。
</audio>

<script>
  const audio = document.getElementById('myAudio');

  audio.onended = function() {
    console.log('再生が終了しました。');
    // 他のアクションをここに追加できます。
  };
</script>
```

または、`addEventListener`を使用する方法：

```html
<video id="myVideo" width="320" height="240" controls>
  <source src="videofile.mp4" type="video/mp4">
  お使いのブラウザはvideo要素をサポートしていません。
</video>

<script>
  const video = document.getElementById('myVideo');

  video.addEventListener('ended', function() {
    console.log('動画の再生が終了しました。');
    // 他のアクションをここに追加できます。
  });
</script>
```

## 説明
「onended」イベントを使用する際の一般的な注意点や落とし穴には以下のようなものがあります。

- **再生の手動停止**: ユーザーが再生を手動で停止した場合も「onended」イベントは発生しないため、別途処理を行う必要があります。
- **複数のリスナー**: 同じメディア要素に対して複数の「onended」リスナーを設定することはできますが、管理が複雑になる可能性があります。必要に応じてリスナーを解除することを検討してください。

## 一文要約
「onended」イベントは、メディアの再生が終了した際にトリガーされるイベントで、再生後の処理を実行するために使用されます。