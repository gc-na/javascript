<!--
Meta Description: # SVGAnimatedRect: JavaScriptによるSVGのアニメーション矩形 ## 概要 `SVGAnimatedRect`は、SVG（Scalable Vector Graphics）でアニメーションされた矩形の属性を表すJavaScriptオブジェクトです。このオブジェクトは、矩形...
Meta Keywords: svganimatedrect, svg, width, height, rect
-->

# SVGAnimatedRect: JavaScriptによるSVGのアニメーション矩形

## 概要
`SVGAnimatedRect`は、SVG（Scalable Vector Graphics）でアニメーションされた矩形の属性を表すJavaScriptオブジェクトです。このオブジェクトは、矩形の位置やサイズをアニメーションさせるために使用され、SVG内で動的なビジュアルエフェクトを作成するのに役立ちます。

## ドキュメンテーション
### 目的
`SVGAnimatedRect`は、SVG要素の矩形の位置やサイズをアニメーションさせるためのインターフェースです。このオブジェクトは、特定の矩形属性（`x`, `y`, `width`, `height`）がアニメーション可能であることを示します。

### 使用法
`SVGAnimatedRect`オブジェクトは、主に以下の属性を持っています：
- `baseVal`: アニメーションされる前の基準値を持つ`DOMRect`オブジェクト。
- `animVal`: アニメーション後の現在の値を持つ`DOMRect`オブジェクト。

例えば、SVG要素の矩形を作成し、そのサイズや位置をアニメーションさせる際に、`SVGAnimatedRect`を活用できます。

### 詳細
`SVGAnimatedRect`は、SVG要素（例：`<rect>`）の属性に直接関連付けられています。アニメーションは、CSSアニメーションやSMIL（Synchronized Multimedia Integration Language）を使用して行うことができます。これにより、ユーザーはSVGの動的な表現を作成することが可能になります。

## 例
以下は、`SVGAnimatedRect`を使用した基本的な例です：

```html
<svg width="200" height="200">
  <rect id="animatedRect" x="10" y="10" width="50" height="50" fill="blue">
    <animate 
      attributeName="x" 
      from="10" 
      to="150" 
      dur="2s" 
      repeatCount="indefinite" />
  </rect>
</svg>
```

この例では、青い矩形がx座標を10から150にアニメーションします。

## 説明
- **共通の落とし穴**: アニメーションの開始値や終了値を間違えると、期待した動きにならないことがあります。特に、座標やサイズがSVGのビューに収まっているか確認することが重要です。
- **ブラウザの互換性**: SVGアニメーションは、ブラウザによって異なるサポート状況があるため、特に古いブラウザでは動作しないことがあります。最新のブラウザを使用することを推奨します。
- **パフォーマンス**: 大量のSVGアニメーションを使用すると、パフォーマンスに影響を与える可能性があります。アニメーションの数を最小限に抑えることが重要です。

## 一文要約
`SVGAnimatedRect`は、SVG内の矩形をアニメーションさせるためのJavaScriptオブジェクトで、動的なビジュアルエフェクトを実現します。