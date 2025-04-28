<!--
Meta Description: # JavaScriptのdecodeURI関数：URIデコードの手法 ## 概要 `decodeURI`は、JavaScriptでエンコードされたURI（Uniform Resource Identifier）をデコードするために使用される組み込み関数です。この関数は、URIの一部として使用される...
Meta Keywords: decodeuri, encodeduri, const, javascript, この関数は
-->

# JavaScriptのdecodeURI関数：URIデコードの手法

## 概要
`decodeURI`は、JavaScriptでエンコードされたURI（Uniform Resource Identifier）をデコードするために使用される組み込み関数です。この関数は、URIの一部として使用される特殊な文字を元の形式に戻す役割を果たします。

## ドキュメンテーション
### 目的
`decodeURI`は、URIのエンコードされた部分をデコードし、元の文字列を復元するために使用されます。特に、ウェブアプリケーションやAPIから取得したエンコードされたURIを扱う際に便利です。

### 使用法
`decodeURI`関数は、以下の構文で使用します。

```javascript
decodeURI(encodedURI);
```

- **引数**: 
  - `encodedURI`（String）: デコードしたいエンコードされたURIを指定します。
  
- **戻り値**: 
  - デコードされたURIを表す文字列。

### 詳細
`decodeURI`は、URI標準に従ってエンコードされた文字列に適用されます。URI中の特定の文字（例：スペース、ピリオド、スラッシュなど）は、エンコード時に特別な形式（%記号に続く16進数）で表現されます。この関数は、それらのエンコードされた形式を人間が読める形式に戻します。

ただし、エンコードされたURIの中に含まれる特別な文字（`#`, `?`, `&`など）は、URIの構造を保つためにデコードされずに残ります。

## 例
以下に`decodeURI`の基本的な使用例を示します。

```javascript
const encodedURI = "https%3A%2F%2Fexample.com%2Fpath%3Fquery%3Dtest";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // "https://example.com/path?query=test"
```

```javascript
const encodedURI2 = "Hello%20World%21";
const decodedURI2 = decodeURI(encodedURI2);
console.log(decodedURI2); // "Hello World!"
```

## 説明
`decodeURI`を使用する際に注意すべき点はいくつかあります。

1. **完全なURIのデコード**: `decodeURI`はURI全体をデコードするため、部分的なデコードが必要な場合は`decodeURIComponent`を使用するべきです。
2. **不正なエンコーディング**: 無効なエンコード形式（例えば、%が次の2桁の16進数でない場合）を含むURIをデコードしようとすると、`URIError`がスローされます。
3. **特別な文字の扱い**: デコードされた結果に含まれる特別な文字（`#`, `?`, `&`など）は注意が必要で、これらは本来のURI構造に影響を与える可能性があります。

## 一文要約
`decodeURI`は、エンコードされたURIを元の形式にデコードするためのJavaScript関数です。