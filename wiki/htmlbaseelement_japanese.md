<!--
Meta Description: # HTMLBaseElement: JavaScriptにおける基本要素の理解 ## 概要 `HTMLBaseElement`は、HTML文書における基本URLを指定するための要素です。JavaScriptを使用して、動的にベースURLを変更したり、取得したりすることができます。この要素は、相対リ...
Meta Keywords: base, href, htmlbaseelement, baseelement, https
-->

# HTMLBaseElement: JavaScriptにおける基本要素の理解

## 概要
`HTMLBaseElement`は、HTML文書における基本URLを指定するための要素です。JavaScriptを使用して、動的にベースURLを変更したり、取得したりすることができます。この要素は、相対リンクの解決に特に重要です。

## ドキュメンテーション
`HTMLBaseElement`は、HTMLの`<base>`タグに対応するJavaScriptオブジェクトです。この要素は、文書内の相対URLを解決するための基準となるURLを定義します。以下はその主なプロパティとメソッドです。

### プロパティ
- **href**: ベースURLを指定するための文字列。相対パスを持つリンクの基準となるURLです。
- **target**: リンクが開く方法（例：`_blank`、`_self`など）を指定します。

### 使用方法
`HTMLBaseElement`は、通常、HTML文書の`<head>`セクションに配置されます。JavaScriptでは、`document.getElementsByTagName('base')[0]`を使用して、最初の`<base>`要素を取得し、プロパティを操作することができます。

```javascript
// ベースURLを取得
let baseElement = document.getElementsByTagName('base')[0];
let baseHref = baseElement.href;

// ベースURLを設定
baseElement.href = 'https://example.com/';
```

## 例
以下は、`HTMLBaseElement`を使用してベースURLを設定する基本的な例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>HTMLBaseElementの例</title>
    <base href="https://example.com/">
</head>
<body>
    <a href="page.html">ページへ</a> <!-- これは https://example.com/page.html にリンクされます -->
    <script>
        let baseElement = document.getElementsByTagName('base')[0];
        console.log(baseElement.href); // "https://example.com/"
        baseElement.href = 'https://another-example.com/';
        console.log(baseElement.href); // "https://another-example.com/"
    </script>
</body>
</html>
```

## 解説
`HTMLBaseElement`を使用する際の一般的な落とし穴は、`<base>`要素が文書内に一度だけ存在すべきであるという点です。複数の`<base>`要素が存在すると、ブラウザがどのURLを使用するか不明瞭になり、リンクが意図した通りに機能しない可能性があります。また、`<base>`要素は`<head>`内で定義する必要があります。`<body>`内に配置すると、正しく機能しません。

## 一文要約
`HTMLBaseElement`は、相対URLの解決において基準となるURLを指定するためのHTML要素であり、JavaScriptを使用してその値を動的に操作できます。