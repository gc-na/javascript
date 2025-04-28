<!--
Meta Description: # SVGAnimatedNumber: JavaScriptにおけるSVGアニメーションの数値タイプ ## 概要 `SVGAnimatedNumber`は、SVG（Scalable Vector Graphics）で使用されるアニメーション数値を表現するためのインターフェースです。このインターフェ...
Meta Keywords: svganimatednumber, circle, animval, svg, baseval
-->

# SVGAnimatedNumber: JavaScriptにおけるSVGアニメーションの数値タイプ

## 概要
`SVGAnimatedNumber`は、SVG（Scalable Vector Graphics）で使用されるアニメーション数値を表現するためのインターフェースです。このインターフェースは、アニメーション中に変化する数値を扱うために使用され、JavaScriptを用いてSVG要素の動的なプロパティを制御する際に重要です。

## ドキュメンテーション
`SVGAnimatedNumber`は、特定の数値プロパティがアニメーションされている場合、そのプロパティの現在の値とアニメーションの初期値および最終値を提供します。このインターフェースは、SVG要素のアニメーションにおいて、アニメーションの開始時点、終了時点、および現在の値を管理します。

### プロパティ
- **baseVal**: アニメーションの基準値を示す`Number`型のプロパティ。
- **animVal**: 現在のアニメーションの値を示す`Number`型のプロパティ。

### 使用方法
`SVGAnimatedNumber`は主にSVG要素のアニメーション属性に関連付けられています。たとえば、`<circle>`要素の半径をアニメーションする際に使用されます。JavaScriptからアクセスすることで、現在のアニメーションの状態を取得したり、更新したりできます。

## 例
以下は、`SVGAnimatedNumber`を使用してSVGの円の半径をアニメーションする基本的な例です。

```html
<svg width="100" height="100">
  <circle id="myCircle" cx="50" cy="50" r="20" fill="red">
    <animate attributeName="r" from="20" to="50" dur="2s" repeatCount="indefinite" />
  </circle>
</svg>

<script>
  const circle = document.getElementById('myCircle');
  const radius = circle.r;

  console.log('Base Value:', radius.baseVal); // アニメーションの基準値
  console.log('Animated Value:', radius.animVal); // 現在のアニメーション値
</script>
```

## 説明
`SVGAnimatedNumber`を使用する際の一般的な落とし穴には、アニメーションが完了する前に`animVal`の値を取得しようとすることが含まれます。アニメーションが開始された直後に値を取得すると、期待した値が得られない場合があります。また、アニメーションが終了した後に`baseVal`を更新することで、次回のアニメーションに影響を与える可能性があるため、注意が必要です。

### 注意点
- `animVal`はアニメーションの進行状況に依存しているため、アニメーションが終了するまで安定した値を取得することはできません。
- JavaScriptでのアニメーション制御には、`requestAnimationFrame`を使用することで、パフォーマンスを向上させることができます。

## 一行要約
`SVGAnimatedNumber`は、SVGアニメーションにおける数値プロパティの基準値と現在の値を管理するインターフェースです。