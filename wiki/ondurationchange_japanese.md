<!--
Meta Description: # JavaScriptの「ondurationchange」イベントの完全ガイド ## 概要 「ondurationchange」は、HTMLMediaElementの再生メディアの持続時間が変更されたときに発生するイベントです。このイベントは、音声や動画のメディア要素に関連しており、メディアの長...
Meta Keywords: videoelement, ondurationchange, video, イベントは, myvideo
-->

# JavaScriptの「ondurationchange」イベントの完全ガイド

## 概要
「ondurationchange」は、HTMLMediaElementの再生メディアの持続時間が変更されたときに発生するイベントです。このイベントは、音声や動画のメディア要素に関連しており、メディアの長さが変更された際に特定のアクションをトリガーするために使用されます。

## ドキュメント
### 目的
「ondurationchange」イベントは、ユーザーがメディアを再生、停止、またはその他の操作を行った際に、メディアの持続時間が変化した場合に発火します。このイベントを活用することで、メディアプレイヤーのUIを更新したり、持続時間に基づいたロジックを実行したりすることが可能です。

### 使用法
- イベントリスナーをメディア要素に追加することで使用します。
- イベントのリスナーは、持続時間が変更されたときに呼び出されるコールバック関数を指定します。

```javascript
const videoElement = document.getElementById('myVideo');

videoElement.addEventListener('durationchange', function() {
    console.log('動画の持続時間が変更されました。新しい持続時間:', videoElement.duration);
});
```

### 詳細
- **対応ブラウザ**: 最新の主要なブラウザ（Chrome, Firefox, Safari, Edge）でサポートされています。
- **発火条件**: メディアの持続時間が変更されたとき、例えば、ストリーミングメディアが読み込まれた際や、メディアのメタデータが更新された際に発生します。
- **イベントオブジェクト**: `durationchange`イベントには、標準的なイベントオブジェクトが含まれるため、追加の情報を取得することができます。

## 例
### 基本的な使用例
以下のコードは、`<video>`要素の持続時間が変更されたときに、コンソールに新しい持続時間を表示します。

```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const videoElement = document.getElementById('myVideo');
    
    videoElement.addEventListener('durationchange', function() {
        console.log('新しい持続時間:', videoElement.duration);
    });
</script>
```

## 説明
### 一般的な落とし穴
- **持続時間が0の場合**: メディアがまだ読み込まれていない場合、持続時間は0になることがあります。この場合、リスナーは期待通りに動作しない可能性があります。
- **非同期処理の考慮**: メディアの読み込みが非同期で行われるため、持続時間が変更された後に他の処理を行う場合は、適切にエラーハンドリングを行う必要があります。

### 注意事項
- `ondurationchange`イベントは、メディアの読み込みが完了していない場合には発生しないことがあります。
- メディア要素の`preload`属性に注意を払い、期待通りに動作するように設定することが重要です。

## 一文要約
「ondurationchange」イベントは、HTMLメディア要素の持続時間が変更された際に発火し、メディアプレイヤーのUI更新やロジック処理に利用されます。