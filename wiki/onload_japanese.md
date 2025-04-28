<!--
Meta Description: # JavaScriptのonloadイベント: ウェブページの読み込み完了を検知する方法 ## 概要 `onload`は、ウェブページや特定のリソースが完全に読み込まれた後に実行されるJavaScriptのイベントハンドラです。このイベントは、ページのコンテンツがすべて整った状態で処理を行いたい場...
Meta Keywords: onload, window, html, console, log
-->

# JavaScriptのonloadイベント: ウェブページの読み込み完了を検知する方法

## 概要
`onload`は、ウェブページや特定のリソースが完全に読み込まれた後に実行されるJavaScriptのイベントハンドラです。このイベントは、ページのコンテンツがすべて整った状態で処理を行いたい場合に非常に便利です。

## ドキュメンテーション
### 目的
`onload`イベントは、ブラウザが全てのリソース（画像、スクリプト、スタイルシートなど）を読み込んだ後に実行されるため、DOMが完全に利用可能になったタイミングでJavaScriptを実行するために使用されます。

### 使用法
`onload`は、`window`オブジェクトや特定のHTML要素に対して設定できます。以下は、`window`オブジェクトにおける基本的な使用方法です。

```javascript
window.onload = function() {
    // ページが完全に読み込まれた後に実行されるコード
    console.log("ページが読み込まれました");
};
```

また、特定の要素に`onload`を設定することも可能です。例えば、画像要素が読み込まれた後に何か処理を行いたい場合、次のように書けます。

```html
<img src="image.jpg" onload="console.log('画像が読み込まれました');">
```

### 詳細
- `onload`イベントは、`window.onload`や`element.onload`プロパティに関数を代入することで設定できます。
- 複数の`onload`ハンドラを設定する場合、前のハンドラは上書きされます。これを避けるためには、`addEventListener`メソッドを使用することを推奨します。

```javascript
window.addEventListener('load', function() {
    console.log("ページが読み込まれました");
});
```

## 例
### 基本的な使用例
以下は、`onload`イベントを使った簡単な例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>onloadの例</title>
    <script>
        window.onload = function() {
            alert("ページが読み込まれました！");
        };
    </script>
</head>
<body>
    <h1>JavaScript onloadのデモ</h1>
</body>
</html>
```

### 画像の読み込み完了を検知する例
```html
<img src="example.jpg" onload="console.log('画像が読み込まれました');">
```

## 説明
`onload`イベントにはいくつかの注意点があります。
- ページの読み込み時間が長い場合、ユーザーは待たされることになります。必要な処理は最小限にすることが望ましいです。
- JavaScriptが正しく動作するためには、HTML要素がDOMに追加された後に実行する必要があります。これには`DOMContentLoaded`イベントも考慮することが重要です。
- セキュリティ上の理由から、同一生成元ポリシーに従い、外部リソースの読み込みには注意が必要です。

## 一文要約
`onload`は、ウェブページやリソースが完全に読み込まれた後に実行されるJavaScriptのイベントハンドラです。