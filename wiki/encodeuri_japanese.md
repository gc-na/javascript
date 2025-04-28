<!--
Meta Description: # JavaScriptにおけるencodeURI関数の使い方と特徴 ## 概要 `encodeURI`は、JavaScriptにおいてURI（Uniform Resource Identifier）をエンコードするための関数です。この関数は、特定の文字をURIで使用できる形式に変換し、URLの一部...
Meta Keywords: encodeuri, uri, javascript, const, https
-->

# JavaScriptにおけるencodeURI関数の使い方と特徴

## 概要
`encodeURI`は、JavaScriptにおいてURI（Uniform Resource Identifier）をエンコードするための関数です。この関数は、特定の文字をURIで使用できる形式に変換し、URLの一部として安全に使用できるようにします。

## ドキュメンテーション
### 目的
`encodeURI`は、特定の文字をエスケープしてURIを標準的な形式に整えるために使用されます。これにより、URIが正しく解釈され、特定の文字が誤って解釈されることを防ぎます。

### 使用法
`encodeURI`の基本的な構文は次の通りです。

```javascript
encodeURI(uri)
```

- **uri**: エンコードしたい文字列（URI）。

### 詳細
`encodeURI`は、以下の文字をエスケープしますが、予約された文字はそのまま残します。エスケープされる文字には、例えばスペース（空白）、特定の記号（例：#、%、&など）が含まれます。予約された文字には、コロン（:）、スラッシュ（/）、クエスチョンマーク（?）などがあります。

## 例
以下に`encodeURI`の基本的な使用例を示します。

```javascript
const uri = "https://example.com/日本語のページ?query=テスト";
const encodedURI = encodeURI(uri);
console.log(encodedURI);
// 出力: https://example.com/%E6%97%A5%E6%9C%AC%E8%AA%9E%E3%81%AE%E3%83%9A%E3%83%BC%E3%82%B8?query=%E3%83%86%E3%82%B9%E3%83%88
```

## 説明
`encodeURI`を使用する際の一般的な落とし穴は、エンコードの必要がない予約文字を誤ってエスケープしてしまうことです。例えば、URLのスラッシュ（/）やコロン（:）は、URIの構造に必要なため、エンコードしない方が良いです。また、特定のアプリケーションやAPIで期待される形式に合わせてエンコードする必要がある場合もありますので、注意が必要です。

## 一文要約
`encodeURI`は、JavaScriptでURIを安全にエンコードするための関数であり、特定の文字をエスケープしてURIの正しい解釈を助けます。