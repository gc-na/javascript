<!--
Meta Description: # SVGGradientElement: JavaScriptにおけるSVGグラデーションの操作 ## 概要 `SVGGradientElement`は、SVG（Scalable Vector Graphics）においてグラデーションを定義するための要素です。JavaScriptを使用してSVGの...
Meta Keywords: svggradientelement, stop, 200, svg, lineargradient
-->

# SVGGradientElement: JavaScriptにおけるSVGグラデーションの操作

## 概要
`SVGGradientElement`は、SVG（Scalable Vector Graphics）においてグラデーションを定義するための要素です。JavaScriptを使用してSVGのグラデーションを操作し、視覚的なデザインを強化することができます。

## ドキュメンテーション
### 概要
`SVGGradientElement`は、SVG内でリニア（線形）およびラジアル（放射状）グラデーションを定義するための基本的な要素です。この要素は、`<linearGradient>`や`<radialGradient>`のようなタグとしてDOMに追加され、色の遷移を視覚的に表現します。

### 使用法
JavaScriptを使用して`SVGGradientElement`を操作するには、以下の手順を実行します。

1. **SVG要素の作成**: SVGコンテナを作成し、必要なグラデーション要素を追加します。
2. **グラデーションの定義**: `SVGGradientElement`を使用してグラデーションを定義します。
3. **要素への適用**: 定義したグラデーションをSVGの描画要素に適用します。

### 詳細
- **属性**: `SVGGradientElement`は、`gradientUnits`、`id`、`x1`、`y1`、`x2`、`y2`などの属性を持ち、グラデーションの設定を調整できます。
- **色のストップ**: グラデーションの色の変更は、`<stop>`要素を使用して行います。これにより、特定の位置で色を指定できます。

## 例
以下は、リニアグラデーションを使用した基本的な例です。

```html
<svg width="200" height="200">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="200" height="200" fill="url(#grad1)" />
</svg>
```

このコードでは、左から右に黄色から赤へのグラデーションが定義され、四角形に適用されています。

## 説明
- **一般的な落とし穴**: グラデーションを適用する際、`url(#grad1)`の`id`が正しく指定されていることを確認してください。間違ったIDを使用すると、グラデーションが表示されません。
- **ブラウザ互換性**: SVGは一般的にモダンブラウザでサポートされていますが、古いブラウザでは表示に問題が生じることがあります。

## 一文の要約
`SVGGradientElement`は、JavaScriptを使ってSVG内でグラデーションを定義および操作するための要素です。