<!--
Meta Description: # SVGNumberとは？JavaScriptにおけるSVG数値の操作方法 ## 概要 SVGNumberは、JavaScriptにおけるSVG（Scalable Vector Graphics）で使用される数値型です。このオブジェクトは、SVGの属性やスタイルに関連する数値を扱うために特化されて...
Meta Keywords: rect, circle, width, const, document
-->

# SVGNumberとは？JavaScriptにおけるSVG数値の操作方法

## 概要
SVGNumberは、JavaScriptにおけるSVG（Scalable Vector Graphics）で使用される数値型です。このオブジェクトは、SVGの属性やスタイルに関連する数値を扱うために特化されており、特にSVGの描画や変形において重要な役割を果たします。

## ドキュメント
SVGNumberは、`SVGSVGElement`やその他のSVG要素で使われる数値を表現するためのオブジェクトです。主に、SVGの数値属性（例えば、`x`、`y`、`width`、`height`など）を安全に操作するために利用されます。

### 使用目的
- SVG要素の数値属性を操作する際に、型安全を提供します。
- 数値の単位（例えば、ピクセルやパーセント）を考慮することなく、計算を行うことができます。

### 使用方法
SVGNumberは通常、SVG要素の数値プロパティにアクセスすることによって生成されます。以下の手順で利用できます。

1. SVG要素を作成または取得します。
2. 対象のSVG属性にアクセスし、SVGNumberを取得します。
3. SVGNumberの値を変更、または取得します。

```javascript
// SVG要素の取得
const svgElement = document.querySelector('svg');

// SVGNumberの取得
const svgNumber = svgElement.getCTM().a; // 例: 行列の最初の要素を取得
```

## 例
以下は、SVGNumberの基本的な使用例です。

### 例1: SVGNumberの取得と表示
```javascript
const rect = document.createElementNS("http://www.w3.org/2000/svg", "rect");
rect.setAttribute("width", "100");
rect.setAttribute("height", "100");
document.querySelector('svg').appendChild(rect);

// width属性を取得
const width = rect.width.baseVal.value; // 100
console.log(width); // 100
```

### 例2: SVGNumberの値の変更
```javascript
const circle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
circle.setAttribute("r", "50");
document.querySelector('svg').appendChild(circle);

// 半径を変更
circle.r.baseVal.value = 75;
console.log(circle.r.baseVal.value); // 75
```

## 説明
SVGNumberを使う際の一般的な落とし穴や注意点は以下の通りです。

- SVGNumberの値は、直接数値として扱うことはできません。必ず`baseVal`を使用してアクセスする必要があります。
- SVGNumberは単位を持たないため、計算を行う際には、単位を考慮する必要があります。
- SVG要素がDOMに追加されていないと、SVGNumberの値にアクセスできないことがあります。

## 一文要約
SVGNumberは、JavaScriptにおいてSVGの数値属性を安全に操作するための特化したオブジェクトです。