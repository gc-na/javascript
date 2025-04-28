<!--
Meta Description: # VTTCueに関するJavaScriptの完全ガイド ## 概要 `VTTCue`は、WebVTT（Web Video Text Tracks）形式のキャプションや字幕を扱うためのJavaScriptオブジェクトです。主にHTML5の`<track>`要素と連携し、動画コンテンツに字幕や説明文を...
Meta Keywords: vttcue, cue, track, line, const
-->

# VTTCueに関するJavaScriptの完全ガイド

## 概要
`VTTCue`は、WebVTT（Web Video Text Tracks）形式のキャプションや字幕を扱うためのJavaScriptオブジェクトです。主にHTML5の`<track>`要素と連携し、動画コンテンツに字幕や説明文を追加するために使用されます。

## ドキュメント
### 目的
`VTTCue`は、WebVTTファイル内の各キュー（Cue）を表現するために設計されています。これにより、開発者は特定のタイミングで表示されるテキストやそのスタイルをプログラムで制御できます。

### 使用法
`VTTCue`オブジェクトは、以下のプロパティおよびメソッドを使用して作成および操作されます。

#### プロパティ
- **startTime**: キューが表示される開始時間（秒単位）。
- **endTime**: キューが非表示になる終了時間（秒単位）。
- **text**: 表示されるテキスト内容。
- **line**: テキストの位置（例：line 0は下部、line 100は上部）。
- **position**: テキストの水平方向の位置。
- **size**: テキストサイズの割合（0から100の間）。

#### メソッド
- **VTTCue()**: 新しい`VTTCue`オブジェクトを作成します。

```javascript
const cue = new VTTCue(0, 5, "こんにちは、世界！");
```

## 例
以下の例は、`VTTCue`を使用して簡単なキャプションを作成する方法を示しています。

```javascript
// 新しいVTTCueを作成
const cue = new VTTCue(0, 10, "このビデオはJavaScriptについてです。");

// プロパティを設定
cue.line = 0; // 下部に表示
cue.position = 50; // 中央に配置
cue.size = 100; // フルサイズ

// cueをtrackに追加
const track = document.querySelector("track");
track.addCue(cue);
```

## 説明
### 一般的な落とし穴
- **時間の指定**: `startTime`や`endTime`を設定する際、正確な秒数を指定する必要があります。これを誤ると、キャプションが意図したタイミングで表示されない可能性があります。
- **テキストスタイル**: `VTTCue`オブジェクト自体にはスタイルを設定する機能はありません。スタイルを適用するには、CSSを使用して`<track>`要素やその親要素をスタイリングする必要があります。

### 注意点
- **ブラウザの互換性**: `VTTCue`はHTML5に依存しているため、古いブラウザではサポートされていないことがあります。最新のブラウザを使用することを推奨します。

## 一行要約
`VTTCue`は、WebVTT形式のキャプションをJavaScriptで操作するためのインターフェースです。