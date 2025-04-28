<!--
Meta Description: # JavaScriptにおけるondragendイベントの詳細ガイド ## 概要 `ondragend`イベントは、HTML要素がドラッグ操作を終了したときに発生するイベントです。このイベントは、ドラッグアンドドロップ操作の一部として使用され、ユーザーがオブジェクトをドラッグして放したときの処理を...
Meta Keywords: draggable, ondragend, html, div, true
-->

# JavaScriptにおけるondragendイベントの詳細ガイド

## 概要
`ondragend`イベントは、HTML要素がドラッグ操作を終了したときに発生するイベントです。このイベントは、ドラッグアンドドロップ操作の一部として使用され、ユーザーがオブジェクトをドラッグして放したときの処理を実施できます。

## ドキュメント
### 目的
`ondragend`は、ユーザーが要素をドラッグしてリリースした時にトリガーされ、ドラッグ操作の完了に関連する処理を実行するためのイベントです。このイベントは、ドラッグアンドドロップのインターフェースを構築する際に非常に重要です。

### 使用法
`ondragend`イベントは、HTML要素に対して直接設定することができます。次のように使用します。

```html
<div id="draggable" draggable="true">ドラッグ可能な要素</div>
```

```javascript
document.getElementById("draggable").ondragend = function(event) {
    console.log("ドラッグが終了しました！");
};
```

### 詳細
- **イベントオブジェクト**: `ondragend`イベントが発生すると、イベントオブジェクトが渡され、ドラッグされた要素やその他の関連情報にアクセスできます。
- **対応ブラウザ**: ほとんどの最新ブラウザでサポートされていますが、古いブラウザでは動作しないことがあります。
- **draggable属性**: 要素に`draggable="true"`を設定することで、その要素がドラッグ可能になります。

## 例
以下は、`ondragend`イベントを使用した基本的な例です。

### 例1: シンプルなドラッグ終了イベント
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>ondragendの例</title>
</head>
<body>
    <div id="draggable" draggable="true">ドラッグしてみてください</div>

    <script>
        document.getElementById("draggable").ondragend = function(event) {
            alert("ドラッグが終了しました！");
        };
    </script>
</body>
</html>
```

### 例2: ドラッグした位置の取得
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>ondragendの位置取得例</title>
</head>
<body>
    <div id="draggable" draggable="true" style="width:100px; height:100px; background-color:lightblue;">ドラッグ</div>

    <script>
        document.getElementById("draggable").ondragend = function(event) {
            console.log("ドラッグ位置:", event.clientX, event.clientY);
        };
    </script>
</body>
</html>
```

## 説明
### よくある落とし穴
- **draggable属性の設定**: `draggable`属性が設定されていない要素では`ondragend`イベントは発生しません。必ず`draggable="true"`を指定してください。
- **スタイルの影響**: ドラッグ中に要素のスタイルが変わると、ユーザーがドラッグを終了したときの視覚的なフィードバックが失われる可能性があります。スタイルの変更に注意を払いましょう。

## 一文要約
`ondragend`イベントは、ドラッグ操作が完了したときに発生し、ユーザーインターフェースでのドラッグアンドドロップ機能の実装に役立ちます。