<!--
Meta Description: # SVGFECompositeElement - JavaScriptでの使用方法と解説 ## 概要 `SVGFECompositeElement`は、SVG（Scalable Vector Graphics）のフィルタ要素の一部であり、2つの入力画像を組み合わせるために使用されます。この要素は、...
Meta Keywords: fecomposite, svgfecompositeelement, svg, in2, filter
-->

# SVGFECompositeElement - JavaScriptでの使用方法と解説

## 概要
`SVGFECompositeElement`は、SVG（Scalable Vector Graphics）のフィルタ要素の一部であり、2つの入力画像を組み合わせるために使用されます。この要素は、JavaScriptを使用してSVGのフィルタ効果を操作する際に重要です。

## ドキュメンテーション
`SVGFECompositeElement`は、SVGのフィルタ効果の一部として、異なる合成方法を使用して、2つのフィルタ入力を組み合わせることができます。主に、以下の属性を持ちます。

- **in**: 最初の入力画像のIDを指定します。
- **in2**: 2番目の入力画像のIDを指定します。
- **operator**: 入力画像を組み合わせる方法を指定します。利用可能なオペレーターには、`over`, `in`, `out`, `atop`, `xor`, `arithmetic`などがあります。
- **result**: 合成結果の出力名を指定します。

### 使用方法
`SVGFECompositeElement`は、通常、SVGのフィルタ定義内で使用されます。JavaScriptを使用して、動的にこの要素を作成したり、属性を変更したりすることが可能です。

```javascript
// SVGフィルタ要素を作成
const svgFilter = document.createElementNS("http://www.w3.org/2000/svg", "filter");
const feComposite = document.createElementNS("http://www.w3.org/2000/svg", "feComposite");

// 属性を設定
feComposite.setAttribute("in", "SourceGraphic");
feComposite.setAttribute("in2", "SourceAlpha");
feComposite.setAttribute("operator", "over");
feComposite.setAttribute("result", "compositeResult");

// フィルタに追加
svgFilter.appendChild(feComposite);
```

## 例
以下は、`SVGFECompositeElement`の基本的な使用例です。

```html
<svg width="200" height="200">
  <defs>
    <filter id="myFilter">
      <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
      <feComposite in="SourceGraphic" in2="blurResult" operator="over" result="compositeResult" />
    </filter>
  </defs>
  <rect x="10" y="10" width="100" height="100" fill="red" filter="url(#myFilter)" />
</svg>
```

この例では、赤い四角形に対してぼかし効果を適用し、その結果を合成しています。

## 説明
`SVGFECompositeElement`を使用する際の一般的な落とし穴と注意点：

- **入力の順序**: `in`と`in2`の指定順序に注意してください。誤った順序は意図しない結果を生む可能性があります。
- **フィルタの参照**: フィルタを適用する際に、正しいフィルタIDを指定することが重要です。間違ったIDは効果を無効にします。
- **ブラウザ互換性**: 一部の古いブラウザでは、SVGフィルタのサポートが制限されているため、最新のブラウザでのテストを推奨します。

## 一文での要約
`SVGFECompositeElement`は、SVGフィルタ内で2つの入力画像を異なる方法で組み合わせるための要素です。