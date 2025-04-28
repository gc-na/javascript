<!--
Meta Description: # Trusted Types: JavaScriptにおける安全なDOM操作のための新しい機能 ## 概要 Trusted Typesは、WebアプリケーションにおけるDOM操作をより安全にするためのJavaScript機能です。この機能は、XSS（クロスサイトスクリプティング）攻撃を防ぐことを目...
Meta Keywords: trusted, const, policy, createhtml, typesは
-->

# Trusted Types: JavaScriptにおける安全なDOM操作のための新しい機能

## 概要
Trusted Typesは、WebアプリケーションにおけるDOM操作をより安全にするためのJavaScript機能です。この機能は、XSS（クロスサイトスクリプティング）攻撃を防ぐことを目的としており、信頼できるデータのみをDOMに挿入できるようにします。

## ドキュメント
### 目的
Trusted Typesは、開発者が信頼できるコンテンツを定義し、そのコンテンツのみがDOMに挿入されることを保証するためのAPIを提供します。これにより、悪意のあるスクリプトがDOMに不正に挿入されるリスクを軽減します。

### 使用法
1. **Trusted Typeの作成**: `TrustedTypePolicy`を使用して新しいポリシーを作成します。
2. **ポリシーの適用**: 作成したポリシーを使用して、信頼できるコンテンツを生成します。
3. **DOMへの挿入**: 信頼できるコンテンツのみがDOMに挿入されるようにします。

```javascript
// TrustedTypePolicyの作成
const policy = trustedTypes.createPolicy('default', {
  createHTML: (input) => {
    return input; // ここでは信頼できるHTMLを返す
  },
});

// 信頼できるHTMLの生成
const safeHTML = policy.createHTML('<div>Hello, World!</div>');

// DOMへの挿入
document.body.innerHTML = safeHTML;
```

## 例
### 基本的な使用例
```javascript
// TrustedTypePolicyの作成
const policy = trustedTypes.createPolicy('myPolicy', {
  createHTML: (input) => input, // 入力をそのまま返す
});

// 信頼できるHTMLを生成
const trustedHTML = policy.createHTML('<p>安全なコンテンツ</p>');
document.body.innerHTML = trustedHTML; // DOMに挿入
```

### 不正な挿入を防ぐ
```javascript
// 不正なHTML入力
const unsafeInput = '<script>alert("XSS");</script>';
const trustedHTML = policy.createHTML(unsafeInput); // これは安全ではない
document.body.innerHTML = trustedHTML; // エラーが発生する
```

## 説明
### 一般的な落とし穴
- **ポリシーの未作成**: Trusted Typesを使用する前に、ポリシーを必ず作成する必要があります。ポリシーがない場合、デフォルトの動作は許可されず、エラーが発生します。
- **信頼できないデータの直接挿入**: 信頼できないデータを直接DOMに挿入すると、XSS攻撃のリスクが高まります。必ず、ポリシーを通じて安全なデータを挿入してください。

### 追加の注意点
- Trusted Typesは、すべてのブラウザでサポートされているわけではありません。ブラウザの互換性を確認してから実装を行うことをお勧めします。
- 開発者は、ポリシーを適切に設計し、必要な場面でのみ信頼できるデータを生成するように心掛けるべきです。

## 一文の要約
Trusted Typesは、JavaScriptにおいてDOM操作を安全に行うための仕組みであり、悪意のあるスクリプトの挿入を防ぐための信頼できるコンテンツの利用を促進します。