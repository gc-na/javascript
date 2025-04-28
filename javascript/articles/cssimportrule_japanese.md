<!--
Meta Description: # CSSImportRule（CSSImportRule）に関する完全ガイド ## 概要 CSSImportRuleは、JavaScriptを通じてCSSの@importルールを操作するためのインターフェースです。このルールは、スタイルシートの中で他のスタイルシートをインポートする際に使用されます...
Meta Keywords: stylesheet, cssimportruleは, css, importrule, cssimportrule
-->

# CSSImportRule（CSSImportRule）に関する完全ガイド

## 概要
CSSImportRuleは、JavaScriptを通じてCSSの@importルールを操作するためのインターフェースです。このルールは、スタイルシートの中で他のスタイルシートをインポートする際に使用されます。

## ドキュメント
CSSImportRuleは、CSSの@import文を表現するためのオブジェクトです。このルールを使用することで、JavaScriptからスタイルシートを動的に操作したり、インポートされたリソースの管理が可能になります。

### プロパティ
- **href**: インポートされるスタイルシートのURLを取得または設定します。
- **media**: インポートされたスタイルシートが適用されるメディアタイプを取得または設定します。
- **styleSheet**: インポートされたスタイルシートのCSSStyleSheetオブジェクトを取得します。

### メソッド
CSSImportRuleには特定のメソッドはありませんが、CSSOM（CSS Object Model）を通じて他のスタイルシートへのアクセスや操作が可能です。

## 例
以下は、CSSImportRuleを使用して@importルールを操作する基本的な例です。

```javascript
// スタイルシートを作成
const styleSheet = document.styleSheets[0];

// @importルールを追加
styleSheet.insertRule('@import url("styles.css");', styleSheet.cssRules.length);

// 最初のCSSImportRuleを取得
const importRule = styleSheet.cssRules[0];

// インポートされたスタイルシートのhrefを取得
console.log(importRule.href); // "styles.css"

// mediaプロパティを設定
importRule.media = 'screen and (max-width: 600px)';
```

## 説明
CSSImportRuleを使用する際の一般的な注意点：
- **互換性**: CSSImportRuleはすべてのブラウザでサポートされているわけではありません。特に古いブラウザでは問題が発生することがあります。ブラウザの互換性を確認することが重要です。
- **スタイルの適用順序**: インポートされたスタイルシートは、元のスタイルシートの後に適用されるため、スタイルの重複や優先順位に注意が必要です。
- **動的操作**: JavaScriptでスタイルシートを動的に変更する場合、CSSImportRuleの変更が他のスタイルに影響を与える可能性があるため、慎重に実装する必要があります。

## 一文要約
CSSImportRuleは、JavaScriptを使用してCSSの@importルールを操作するためのインターフェースです。