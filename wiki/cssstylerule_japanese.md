<!--
Meta Description: # CSSStyleRule: JavaScriptにおけるスタイルルールの操作 ## 概要 `CSSStyleRule`は、JavaScriptを使用してCSSスタイルルールを操作するためのオブジェクトです。このオブジェクトは、CSSスタイルシート内の特定のスタイルルールを表し、ルールの選択子やプ...
Meta Keywords: cssstylerule, cssrule, style, document, stylesheets
-->

# CSSStyleRule: JavaScriptにおけるスタイルルールの操作

## 概要
`CSSStyleRule`は、JavaScriptを使用してCSSスタイルルールを操作するためのオブジェクトです。このオブジェクトは、CSSスタイルシート内の特定のスタイルルールを表し、ルールの選択子やプロパティをプログラムから取得・設定することができます。

## ドキュメント
### 機能
`CSSStyleRule`は、CSSスタイルシートから特定のスタイルルールを取得し、操作するために使用されます。このオブジェクトは、スタイルシートのルールを動的に変更したり、確認したりすることができます。

### 使用法
`CSSStyleRule`は通常、`document.styleSheets`を介してアクセスされるスタイルシートから取得されます。スタイルルールを取得するには、次のようにします。

```javascript
const styleSheet = document.styleSheets[0]; // 最初のスタイルシートを取得
const cssRule = styleSheet.cssRules[0]; // 最初のCSSルールを取得
if (cssRule instanceof CSSStyleRule) {
    console.log(cssRule.selectorText); // ルールの選択子を表示
    console.log(cssRule.style.cssText); // ルールのスタイルを表示
}
```

### 詳細
`CSSStyleRule`オブジェクトは、以下のプロパティとメソッドを提供します。

- **selectorText**: ルールの選択子を取得または設定します。
- **style**: ルールに関連付けられたスタイルオブジェクトを取得します。
- **cssText**: ルールを文字列として取得または設定します。

これらのプロパティを使用することで、スタイルの変更やルールの追加、削除が容易に行えます。

## 例
以下に`CSSStyleRule`を使用した基本的な例を示します。

```javascript
// 最初のスタイルシートから最初のCSSスタイルルールを取得
const styleSheet = document.styleSheets[0];
const cssRule = styleSheet.cssRules[0]; 

// 選択子を表示
console.log(cssRule.selectorText); // "h1"

// スタイルを変更
cssRule.style.color = 'red';
cssRule.style.fontSize = '20px';

// 変更後のスタイルを表示
console.log(cssRule.style.cssText); // "color: red; font-size: 20px;"
```

## 説明
`CSSStyleRule`を使用する際の一般的な落とし穴や注意点は以下の通りです。

- **スタイルシートの存在**: スタイルシートが存在しない場合、`document.styleSheets`は空の配列を返します。そのため、必ずスタイルシートが存在することを確認してください。
- **異なるブラウザの互換性**: 一部の古いブラウザでは、`CSSStyleRule`の一部の機能がサポートされていない場合があります。最新のブラウザでのテストを推奨します。
- **動的な変更の影響**: スタイルを動的に変更した場合、他のスタイルルールや要素に影響が出る可能性があるため、慎重に操作してください。

## 一文要約
`CSSStyleRule`は、JavaScriptを通じてCSSスタイルルールを操作し、スタイルの動的変更を可能にするオブジェクトです。