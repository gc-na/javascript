<!--
Meta Description: # SVGLinearGradientElement: JavaScriptでのSVGの線形グラデーションの扱い ## 概要 `SVGLinearGradientElement`は、SVG（Scalable Vector Graphics）における線形グラデーションを定義するための要素です。この要素...
Meta Keywords: stop, 100, opacity, 300, svglineargradientelement
-->

# SVGLinearGradientElement: JavaScriptでのSVGの線形グラデーションの扱い

## 概要
`SVGLinearGradientElement`は、SVG（Scalable Vector Graphics）における線形グラデーションを定義するための要素です。この要素は、色の移行を滑らかに表現するために利用され、グラフィックや図形に豊かなビジュアルを加えます。

## ドキュメント
`SVGLinearGradientElement`は、SVG内で線形グラデーションを作成するためのインターフェースです。主に以下のプロパティやメソッドを持っています。

### プロパティ
- **x1, y1, x2, y2**: グラデーションの開始点と終了点を指定するためのプロパティ。これにより、グラデーションの方向を決定します。
- **gradientUnits**: グラデーションの単位を指定します。`userSpaceOnUse`または`objectBoundingBox`のいずれかを設定可能です。
- **spreadMethod**: グラデーションの広がり方を指定します。`pad`, `reflect`, `repeat`のいずれかを選択します。

### 使用方法
`SVGLinearGradientElement`を使用する際には、まずSVG要素を作成し、その中に`<linearGradient>`要素を定義します。次に、`<stop>`要素を使用して色の階調を設定します。

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

## 例
以下は、`SVGLinearGradientElement`を用いた基本的な使用例です。

### 例1: 簡単な線形グラデーション
```html
<svg width="300" height="300">
  <defs>
    <linearGradient id="myGradient" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:blue;stop-opacity:1" />
      <stop offset="100%" style="stop-color:green;stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect x="0" y="0" width="300" height="300" fill="url(#myGradient)" />
</svg>
```

### 例2: グラデーションの広がり方を指定
```html
<svg width="300" height="300">
  <defs>
    <linearGradient id="grad2" x1="0%" y1="0%" x2="100%" y2="100%" spreadMethod="reflect">
      <stop offset="0%" style="stop-color:red;stop-opacity:1" />
      <stop offset="50%" style="stop-color:yellow;stop-opacity:1" />
      <stop offset="100%" style="stop-color:blue;stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect x="0" y="0" width="300" height="300" fill="url(#grad2)" />
</svg>
```

## 説明
`SVGLinearGradientElement`を使用する際の一般的な注意点には以下があります。

- **単位の設定**: `gradientUnits`を適切に設定しないと、意図しないグラデーションの表示になることがあります。
- **色の透明度**: `stop-opacity`を正しく設定しないと、色の移行が不自然に見えることがあります。
- **ブラウザ互換性**: 一部の古いブラウザでは、SVG要素のサポートが不十分な場合がありますので、テストを行うことが重要です。

## 一文要約
`SVGLinearGradientElement`は、JavaScriptを用いてSVG内で線形グラデーションを定義し、視覚的なエフェクトを加えるための要素です。