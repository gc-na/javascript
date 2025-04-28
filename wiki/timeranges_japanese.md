<!--
Meta Description: # JavaScriptのTimeRanges: メディアの再生範囲を制御する ## 概要 JavaScriptのTimeRangesは、HTMLMediaElementインターフェースによって提供されるオブジェクトで、メディアの再生範囲を表現します。特に、動画や音声の特定の再生位置や範囲を取得する...
Meta Keywords: buffered, video, start, end, javascriptのtimerangesは
-->

# JavaScriptのTimeRanges: メディアの再生範囲を制御する

## 概要
JavaScriptのTimeRangesは、HTMLMediaElementインターフェースによって提供されるオブジェクトで、メディアの再生範囲を表現します。特に、動画や音声の特定の再生位置や範囲を取得する際に使用されます。

## ドキュメント
TimeRangesオブジェクトは、メディア要素に関連する再生範囲を管理するために使用されます。主に、メディアのバッファリング状況や再生可能な部分を把握するために役立ちます。

### 使用目的
- メディアの再生状況を把握する
- バッファリングされたデータの範囲を確認する
- ユーザーインターフェースでの再生可能部分の表示

### プロパティ
- `length`: TimeRangesの範囲の数を返します。
- `start(index)`: 指定されたインデックスの範囲の開始時間を返します。
- `end(index)`: 指定されたインデックスの範囲の終了時間を返します。

### 使用例
```javascript
// 動画要素の取得
const video = document.querySelector('video');

// TimeRangesを取得
video.addEventListener('loadeddata', () => {
    const buffered = video.buffered;

    for (let i = 0; i < buffered.length; i++) {
        console.log(`範囲${i}: 開始時間 = ${buffered.start(i)}, 終了時間 = ${buffered.end(i)}`);
    }
});
```

## 説明
TimeRangesを使用すると、メディアのバッファリング状況をリアルタイムで確認できます。特に、ユーザーが特定の部分をスキップする場合や、メディアプレーヤーのインターフェースをカスタマイズする際に非常に便利です。

### 注意点
- TimeRangesは、メディアのバッファがない場合や、まだロードされていない場合、空の状態になることがあります。
- `start()`や`end()`メソッドを呼び出す際は、有効なインデックスを指定する必要があります。無効なインデックスを指定すると、エラーが発生します。

## 一文のまとめ
JavaScriptのTimeRangesは、メディアの再生可能な範囲を管理し、バッファリング情報を取得するための重要なツールです。