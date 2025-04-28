<!--
Meta Description: # DocumentType（JavaScriptにおける文書型） ## 概要 DocumentTypeは、HTMLやXML文書の種類を定義するために使用されるオブジェクトです。JavaScriptを使用してDOMにアクセスする際、文書型は重要な役割を果たします。このオブジェクトを利用することで、ブ...
Meta Keywords: doctype, document, console, log, html
-->

# DocumentType（JavaScriptにおける文書型）

## 概要
DocumentTypeは、HTMLやXML文書の種類を定義するために使用されるオブジェクトです。JavaScriptを使用してDOMにアクセスする際、文書型は重要な役割を果たします。このオブジェクトを利用することで、ブラウザがどの文書を解析しているかを把握できます。

## ドキュメンテーション
DocumentTypeオブジェクトは、`document.doctype`プロパティを通じてアクセスできます。このプロパティは、現在の文書のDOCTYPEを表すDocumentTypeオブジェクトを返します。DOCTYPEは、HTML文書の最初の行に記載され、使用されるHTMLのバージョンや仕様を示します。

### 使用方法
```javascript
const doctype = document.doctype;
console.log(doctype.name); // DOCTYPE名を出力
console.log(doctype.publicId); // 公開IDを出力
console.log(doctype.systemId); // システムIDを出力
```

### 詳細
DocumentTypeオブジェクトには、以下のプロパティがあります：
- **name**: DOCTYPEの名前（例: "html"）。
- **publicId**: 文書の公開ID（省略可能）。
- **systemId**: 文書のシステムID（省略可能）。

DOCTYPEは、文書の解釈方法をブラウザに指示するため、正しいDOCTYPEを指定することが重要です。適切なDOCTYPEを使用することで、文書が期待通りに表示され、標準に準拠した動作が保証されます。

## 例
### 基本的な使用例
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>DocumentTypeの例</title>
</head>
<body>
    <script>
        const doctype = document.doctype;
        console.log("DOCTYPEの名前: " + doctype.name); // "html"
    </script>
</body>
</html>
```

### DOCTYPEの詳細を取得
```javascript
if (document.doctype) {
    console.log("DOCTYPE名: " + document.doctype.name); // "html"
    console.log("公開ID: " + document.doctype.publicId); // ""
    console.log("システムID: " + document.doctype.systemId); // ""
}
```

## 説明
DocumentTypeを操作する際の一般的な落とし穴には、DOCTYPEが省略されている文書や、誤ったDOCTYPE宣言によってブラウザが期待通りに動作しないことがあります。特に、DOCTYPEがない場合、ブラウザはクイックモードで表示され、CSSやJavaScriptの動作に意図しない影響を与えることがあります。

また、DOCTYPEは文書の一番上に配置する必要があり、HTMLやXMLのバージョンに応じて適切な形式で記述することが求められます。

## 一文要約
DocumentTypeは、JavaScriptでHTMLやXML文書の種類を定義し、ブラウザに解析方法を指示する重要なオブジェクトです。