<!--
Meta Description: # TextTrackCueList: JavaScriptでの字幕トラックキューリストの操作 ## 概要 `TextTrackCueList`は、HTML5ビデオやオーディオ要素において、字幕やキャプションを管理するためのインターフェースです。これにより、メディアに関連付けられたテキストトラックの...
Meta Keywords: texttrackcuelist, texttrack, const, video, videoelement
-->

# TextTrackCueList: JavaScriptでの字幕トラックキューリストの操作

## 概要
`TextTrackCueList`は、HTML5ビデオやオーディオ要素において、字幕やキャプションを管理するためのインターフェースです。これにより、メディアに関連付けられたテキストトラックのキューを操作できます。

## ドキュメント
`TextTrackCueList`は、`TextTrack`オブジェクトの一部で、`TextTrackCue`のリストを保持します。主に、メディアプレーヤーにおける字幕表示のために使用されます。

### 目的
`TextTrackCueList`を使用することで、開発者はメディアコンテンツに関連する字幕やキャプションをプログラムで管理し、表示や非表示の制御が可能になります。

### 使用方法
`TextTrackCueList`は、`TextTrack.cues`プロパティを通じてアクセスされます。これは、現在アクティブなすべてのキューを取得するためのリストを提供します。

```javascript
const videoElement = document.querySelector('video');
const textTrack = videoElement.textTracks[0]; // 最初のテキストトラックを取得
const cueList = textTrack.cues; // TextTrackCueListを取得
```

### プロパティ
- **length**: `TextTrackCueList`に含まれるキューの数を示すプロパティ。

### メソッド
- **getCueById(id)**: 指定したIDを持つキューを返します。

## 例
以下は、`TextTrackCueList`を使用してビデオの字幕を表示する基本的な例です。

```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
</video>

<script>
  const videoElement = document.querySelector('video');
  const textTrack = videoElement.textTracks[0];

  textTrack.mode = 'showing'; // 字幕を表示するモードに設定

  textTrack.cues.forEach(cue => {
      console.log(`Cue: ${cue.text}`); // 各キューのテキストをログに出力
  });
</script>
```

## 説明
`TextTrackCueList`を使用する際の一般的な落とし穴として、以下の点に注意が必要です。

- **非同期性**: 字幕データが読み込まれる前に`TextTrackCueList`にアクセスすると、空のリストが返されることがあります。これは、`textTracks`がメディアが再生されるまで完全に初期化されないためです。
- **モード設定**: `TextTrack`の`mode`プロパティを変更することで、キューの表示状態を管理できますが、`showing`に設定しないと、キューは表示されません。

## 一文要約
`TextTrackCueList`は、HTML5メディアにおける字幕やキャプションの管理を行うためのJavaScriptインターフェースです。