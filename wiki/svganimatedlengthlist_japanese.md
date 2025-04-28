<!--
Meta Description: # SVGAnimatedLengthList に関する完全ガイド ## 概要 `SVGAnimatedLengthList` は、SVG（Scalable Vector Graphics）要素で使用されるアニメーション可能な長さのリストを表すインターフェースです。このインターフェースは、SVGの長...
Meta Keywords: svganimatedlengthlist, baseval, const, animval, polyline
-->

# SVGAnimatedLengthList に関する完全ガイド

## 概要
`SVGAnimatedLengthList` は、SVG（Scalable Vector Graphics）要素で使用されるアニメーション可能な長さのリストを表すインターフェースです。このインターフェースは、SVGの長さ属性が時間の経過とともに変化することを可能にし、アニメーション効果を実現します。

## ドキュメンテーション
### 目的
`SVGAnimatedLengthList` は、SVG要素における長さのリストのアニメーションをサポートします。これにより、長さの変更が滑らかにアニメーション化され、視覚的な効果を高めます。

### 使用法
`SVGAnimatedLengthList` は、主に以下の2つのプロパティで構成されています：
- `baseVal`: デフォルトの長さリストを示します。これは、アニメーションが適用されていない場合の値です。
- `animVal`: 現在のアニメーションの値を示します。アニメーションが進行するにつれて、この値が変化します。

これらのプロパティは、次のように使用できます。

```javascript
const svgElement = document.getElementById("mySvgElement");
const animatedLengthList = svgElement.getAttribute("myLengthList") as SVGAnimatedLengthList;

// デフォルトの長さリストを取得
const baseVal = animatedLengthList.baseVal;

// 現在のアニメーション値を取得
const animVal = animatedLengthList.animVal;
```

### 詳細
`SVGAnimatedLengthList` は、SVGの要素（例えば、`<path>`や`<polyline>`）の長さ属性に関連しています。アニメーションを使用することで、ユーザーインターフェースをより動的にし、インタラクションを向上させることができます。ブラウザによってサポートされているため、広く利用可能です。

## 例
以下は、`SVGAnimatedLengthList` を使用した基本的な例です。

```html
<svg width="100" height="100">
  <polyline id="myPolyline" points="10,10 50,50 90,10" stroke="black" fill="none" />
</svg>

<script>
  const polyline = document.getElementById("myPolyline");
  const lengthList = polyline.getAttribute("points") as SVGAnimatedLengthList;

  // デフォルトのポイントを変更
  lengthList.baseVal.appendItem("70,70");
  console.log(lengthList.baseVal);
</script>
```

## 説明
`SVGAnimatedLengthList` を使用する際の一般的な注意点は以下の通りです。

- **ブラウザ互換性**: 古いブラウザではサポートされていない場合があります。常に最新のブラウザでテストすることをお勧めします。
- **アニメーションの管理**: アニメーションのステートを適切に管理しないと、意図しない動作が生じる可能性があります。特に、`baseVal` と `animVal` の状態を把握しておくことが重要です。
- **複雑なアニメーション**: 複数の長さリストを同時にアニメーションさせる場合、アニメーションのタイミングや順序を慎重に設計する必要があります。

## ワンライナー概要
`SVGAnimatedLengthList` は、SVG要素の長さ属性をアニメーション化するためのインターフェースです。