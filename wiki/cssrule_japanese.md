<!--
Meta Description: # CSSRule: JavaScriptでのスタイルルール操作 ## 概要 `CSSRule`は、JavaScriptを使用してCSSスタイルシートのルールを表現、操作するためのインターフェースです。このオブジェクトは、CSSのルールにアクセスし、変更することで、動的なスタイルの適用が可能になりま...
Meta Keywords: cssrule, firstrule, selectortext, stylesheet, 例えば
-->

# CSSRule: JavaScriptでのスタイルルール操作

## 概要
`CSSRule`は、JavaScriptを使用してCSSスタイルシートのルールを表現、操作するためのインターフェースです。このオブジェクトは、CSSのルールにアクセスし、変更することで、動的なスタイルの適用が可能になります。

## ドキュメンテーション
`CSSRule`は、CSSスタイルシートの各ルールを表すオブジェクトです。CSSのスタイルルール（例えば、セレクタやプロパティ）は、`CSSRule`のインスタンスとしてJavaScriptから操作できます。これにより、開発者は動的にスタイルを変更したり、ルールを追加したりすることができます。

### 主なプロパティとメソッド
- **type**: ルールのタイプを示す数値。例えば、`CSSStyleRule`や`CSSMediaRule`など。
- **selectorText**: CSSルールのセレクタを取得または設定します。
- **style**: ルールに関連付けられたスタイルプロパティの集合を取得します。

### 使用例
`CSSRule`を使用する際は、まずスタイルシートを取得し、その中のルールにアクセスします。以下に基本的な使用例を示します。

## 例
```javascript
// スタイルシートを取得
const styleSheet = document.styleSheets[0];

// 最初のルールにアクセス
const firstRule = styleSheet.cssRules[0];

// ルールのセレクタをログに出力
console.log(firstRule.selectorText);

// セレクタを変更
firstRule.selectorText = '.new-class';

// スタイルを変更
firstRule.style.color = 'red';
```

## 説明
`CSSRule`を使用する際の一般的な注意点：
- スタイルシートは、同じオリジンポリシーに従う必要があります。他のドメインからのスタイルシートにはアクセスできません。
- ルールを変更することができるのは、CSSのルールが`styleSheet`に存在する場合のみです。存在しないルールを変更しようとするとエラーが発生します。
- `CSSRule`のタイプを確認することで、特定のルールに対する操作を適切に行うことができます。

## 一文要約
`CSSRule`は、JavaScriptを通じてCSSスタイルルールを操作するための強力なインターフェースです。