<!--
Meta Description: # onhashchange: JavaScriptにおけるハッシュ変更イベントの利用方法 ## 概要 `onhashchange`は、URLのハッシュ部分が変更されたときに発生するイベントを処理するためのJavaScriptのプロパティです。これを活用することで、シングルページアプリケーション（S...
Meta Keywords: onhashchange, hash, html, window, function
-->

# onhashchange: JavaScriptにおけるハッシュ変更イベントの利用方法

## 概要
`onhashchange`は、URLのハッシュ部分が変更されたときに発生するイベントを処理するためのJavaScriptのプロパティです。これを活用することで、シングルページアプリケーション（SPA）や動的なコンテンツの表示を容易に管理できます。

## ドキュメント
`onhashchange`イベントは、ブラウザのアドレスバーでハッシュが変更されたときにトリガーされます。ハッシュ部分はURLの`#`以降の部分で、ページの特定のセクションを示すために使用されます。このイベントを利用することで、ユーザーが異なるビューやコンテンツに遷移した際に、JavaScriptで適切な処理を行うことができます。

### 使い方
`onhashchange`は、以下のように使用します。

```javascript
window.onhashchange = function() {
    // ハッシュが変更されたときの処理
    console.log("ハッシュが変更されました: " + location.hash);
};
```

このコードでは、ブラウザのハッシュが変更されると、コンソールに新しいハッシュ値が表示されます。

### 詳細
- **イベントの発生**: ハッシュが変更されると、`onhashchange`イベントが発生します。手動でURLのハッシュを変更することによっても、イベントはトリガーされます。
- **対応ブラウザ**: 主要なモダンブラウザ（Chrome、Firefox、Edge、Safariなど）でサポートされていますが、古いブラウザでは互換性に注意が必要です。

## 例
以下は、特定のハッシュに基づいてコンテンツを表示するシンプルな例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>onhashchangeの例</title>
</head>
<body>
    <div id="content">ここにコンテンツが表示されます。</div>
    <script>
        window.onhashchange = function() {
            const hash = location.hash.substring(1); // ハッシュの先頭の#を除去
            document.getElementById('content').innerText = hash ? "選択されたハッシュ: " + hash : "ハッシュが設定されていません。";
        };
    </script>
</body>
</html>
```

この例では、URLにハッシュを追加することで、コンテンツが動的に変わります。

## 説明
`onhashchange`イベントは非常に便利ですが、以下の点に注意が必要です。

- **履歴管理**: ハッシュの変更はブラウザの履歴に記録されるため、ユーザーが「戻る」ボタンを押すと、前のハッシュに戻ることができます。
- **パフォーマンス**: 頻繁にハッシュが変更される場合、イベントが多くトリガーされる可能性があります。必要に応じてイベントリスナーを適切に管理することが重要です。
- **初期読み込み**: ページが読み込まれたときに、現在のハッシュを取得したい場合は、`onhashchange`の定義の前に初期値の取得を行うことをお勧めします。

## 一文要約
`onhashchange`は、URLのハッシュが変更されたときに発生するイベントを処理するためのJavaScript機能です。