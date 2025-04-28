<!--
Meta Description: # ShadowRoot: JavaScriptにおけるシャドウDOMの使用法 ## 概要 `ShadowRoot`は、Webコンポーネントの技術の一部であり、HTML要素に対してカプセル化されたDOMを提供します。この機能により、スタイルやスクリプトが親ドキュメントと衝突することなく、独立したコン...
Meta Keywords: shadowroot, const, hostelement, mode, html
-->

# ShadowRoot: JavaScriptにおけるシャドウDOMの使用法

## 概要
`ShadowRoot`は、Webコンポーネントの技術の一部であり、HTML要素に対してカプセル化されたDOMを提供します。この機能により、スタイルやスクリプトが親ドキュメントと衝突することなく、独立したコンポーネントを作成できます。

## ドキュメント
`ShadowRoot`は、Webコンポーネントを作成する際に使用されるインターフェースで、要素に対してシャドウDOMを作成し、管理するためのメソッドやプロパティを提供します。

### 目的
シャドウDOMは、スタイルや機能を他の部分から隔離することで、コンポーネントの再利用性を高め、開発の効率を向上させます。

### 使用法
`ShadowRoot`は、主に`Element.attachShadow()`メソッドを使用して作成されます。以下のように使用します。

```javascript
const hostElement = document.getElementById('host');
const shadowRoot = hostElement.attachShadow({ mode: 'open' });
```

ここで、`mode`はシャドウDOMの公開範囲を指定します。`'open'`の場合、シャドウDOMは外部からアクセス可能ですが、`'closed'`の場合、アクセスできません。

### 詳細
- `shadowRoot.innerHTML`: シャドウDOM内のHTMLコンテンツを取得または設定します。
- `shadowRoot.querySelector()`: シャドウDOM内の要素を選択します。

## 例
### 基本的な使用例
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>Shadow DOM Example</title>
</head>
<body>
    <div id="host"></div>
    <script>
        const hostElement = document.getElementById('host');
        const shadowRoot = hostElement.attachShadow({ mode: 'open' });
        
        shadowRoot.innerHTML = `
            <style>
                p {
                    color: blue;
                }
            </style>
            <p>これはシャドウDOM内のテキストです。</p>
        `;
    </script>
</body>
</html>
```

## 説明
- **一般的な落とし穴**: シャドウDOM内のスタイルは、親ドキュメントのスタイルに影響されないため、意図したスタイルが適用されないことがあります。特に、グローバルなCSSが意図した通りに動作しない場合があります。
- **アクセス制限**: `mode: 'closed'`で作成したシャドウDOMは、外部からアクセスできないため、デバッグが難しくなることがあります。

## 一文要約
`ShadowRoot`は、JavaScriptを使用してWebコンポーネントにカプセル化されたDOMを提供するためのインターフェースです。