<!--
Meta Description: # CSSStyleSheet: JavaScriptでのスタイルシート操作 ## 概要 `CSSStyleSheet`は、JavaScriptを使用してCSSスタイルシートを操作するためのオブジェクトです。このオブジェクトを利用することで、動的にスタイルを追加、変更、削除することが可能です。 ##...
Meta Keywords: stylesheet, cssstylesheet, document, stylesheets, const
-->

# CSSStyleSheet: JavaScriptでのスタイルシート操作

## 概要
`CSSStyleSheet`は、JavaScriptを使用してCSSスタイルシートを操作するためのオブジェクトです。このオブジェクトを利用することで、動的にスタイルを追加、変更、削除することが可能です。

## ドキュメント
`CSSStyleSheet`は、CSSスタイルシートに関連する情報を管理するためのインターフェースです。主に以下のプロパティとメソッドを提供します。

### 主なプロパティ
- **cssRules**: スタイルシート内のすべてのCSSルールのリストを含む配列です。
- **insertRule()**: スタイルシートに新しいルールを追加します。
- **deleteRule()**: 指定されたインデックスのルールを削除します。

### 使用法
`CSSStyleSheet`オブジェクトは、通常、`document.styleSheets`コレクションを介してアクセスされます。以下は、基本的な使用法の流れです。

```javascript
// スタイルシートを取得
const styleSheet = document.styleSheets[0];

// 新しいルールを追加
styleSheet.insertRule('body { background-color: lightblue; }', styleSheet.cssRules.length);

// 既存のルールを削除
styleSheet.deleteRule(0);
```

## 例
以下は、`CSSStyleSheet`を使用した簡単な例です。

### スタイルの追加
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.insertRule('.highlight { color: red; }', styleSheet.cssRules.length);
```

### スタイルの削除
```javascript
const styleSheet = document.styleSheets[0];
// 0番目のルールを削除
styleSheet.deleteRule(0);
```

### ルールの変更
```javascript
const styleSheet = document.styleSheets[0];
const rules = styleSheet.cssRules;

// ルールを変更
if (rules.length > 0) {
    rules[0].style.color = 'blue';
}
```

## 説明
`CSSStyleSheet`を使用する際の一般的な注意点として、以下の点があります。

- **ブラウザ互換性**: 一部の古いブラウザでは、`insertRule`や`deleteRule`メソッドがサポートされていないことがあります。最新のブラウザを使用することを推奨します。
- **特定のスタイルシートへのアクセス**: 複数のスタイルシートが存在する場合、インデックスを使用して特定のスタイルシートを選択する必要があります。意図しないスタイルシートを操作しないよう注意が必要です。
  
## 一文要約
`CSSStyleSheet`は、JavaScriptを用いてCSSスタイルシートを動的に操作するための強力なインターフェースです。