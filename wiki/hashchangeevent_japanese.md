<!--
Meta Description: # HashChangeEvent: JavaScriptにおけるハッシュ変更イベントの詳細 ## 概要 `HashChangeEvent`は、URLのハッシュ部分が変更されたときに発生するイベントです。このイベントを利用することで、シングルページアプリケーション（SPA）や動的なページ遷移を実現す...
Meta Keywords: hashchangeevent, hashchange, html, window, location
-->

# HashChangeEvent: JavaScriptにおけるハッシュ変更イベントの詳細

## 概要
`HashChangeEvent`は、URLのハッシュ部分が変更されたときに発生するイベントです。このイベントを利用することで、シングルページアプリケーション（SPA）や動的なページ遷移を実現することができます。

## ドキュメンテーション
### 目的
`HashChangeEvent`は、ユーザーがブラウザのアドレスバーでハッシュを変更したときや、JavaScriptを使用してハッシュを変更したときに発生します。このイベントは、ブラウザの履歴を操作するために便利です。

### 使用法
`HashChangeEvent`を使用する場合、`window`オブジェクトの`hashchange`イベントリスナーを設定する必要があります。以下のコードスニペットでは、ハッシュが変更されたときに発動する関数を示しています。

```javascript
window.addEventListener('hashchange', function(event) {
    console.log('ハッシュが変更されました: ' + location.hash);
});
```

### 詳細
- **プロパティ**:
  - `newURL`: 新しい URL。
  - `oldURL`: 古い URL。
- **ブラウザの互換性**: ほとんどのモダンブラウザでサポートされていますが、古いブラウザではサポートされない可能性があります。

## 例
以下は、`HashChangeEvent`を使用した基本的な例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>HashChangeEventの例</title>
</head>
<body>
    <h1>ハッシュ変更イベント例</h1>
    <a href="#section1">セクション1</a>
    <a href="#section2">セクション2</a>

    <script>
        window.addEventListener('hashchange', function() {
            const currentHash = location.hash;
            console.log(`現在のハッシュ: ${currentHash}`);
        });
    </script>
</body>
</html>
```

この例では、ユーザーがリンクをクリックしてハッシュを変更すると、コンソールに新しいハッシュが表示されます。

## 説明
- **一般的な落とし穴**: `hashchange`イベントは、ハッシュが変更されるたびに発生しますが、`location.hash`の変更が無い場合（例えば、同じハッシュを再度クリックした場合）には発生しません。
- **履歴管理**: `HashChangeEvent`を使用することで、ユーザーのナビゲーション履歴を管理しやすくなり、バックボタンの使用にも対応できます。

## 一文要約
`HashChangeEvent`は、URLのハッシュ部分が変更された際に発生するイベントで、シングルページアプリケーションにおけるダイナミックなナビゲーションを実現します。