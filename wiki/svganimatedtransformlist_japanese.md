<!--
Meta Description: # SVGAnimatedTransformList: JavaScript における SVG のアニメーション変形リスト ## 概要 SVGAnimatedTransformList は、SVG（Scalable Vector Graphics）内でアニメーションの変形を管理するためのオブジェクト...
Meta Keywords: svg, svganimatedtransformlist, transform, baseval, javascript
-->

# SVGAnimatedTransformList: JavaScript における SVG のアニメーション変形リスト

## 概要
SVGAnimatedTransformList は、SVG（Scalable Vector Graphics）内でアニメーションの変形を管理するためのオブジェクトです。このオブジェクトは、SVG 要素に適用される変形のリストを保持し、アニメーションを通じて変形を動的に変更することを可能にします。

## ドキュメンテーション
### 目的
SVGAnimatedTransformList は、SVG 要素の変形をアニメーションさせるための便利な方法を提供します。特に、複数の変形を持つ要素に対して、変形のリストを操作することが可能です。

### 使用法
SVGAnimatedTransformList は、主に SVG 要素の `transform` 属性と連携して使用されます。以下のプロパティを持っています。

- **baseVal**: 基本の変形リストを返すプロパティ。
- **animVal**: アニメーション中の変形リストを返すプロパティ。

これらのプロパティを利用することで、アニメーションの開始や停止、変形の追加や削除を行うことができます。

### 詳細
SVGAnimatedTransformList を利用する際は、次のような手順を踏むことが一般的です：

1. **SVG 要素の取得**: ドキュメントから対象の SVG 要素を取得します。
2. **変形リストの取得**: `transform.baseVal` または `transform.animVal` を使用して変形リストを取得します。
3. **変形の追加**: `SVGTransform` オブジェクトを作成し、変形リストに追加します。

## 例
以下は、SVGAnimatedTransformList を使用した基本的な例です。

```javascript
// SVG 要素を取得
const svgElement = document.getElementById("mySvgElement");

// 変形リストを取得
const transformList = svgElement.transform.baseVal;

// 新しい変形を作成
const newTransform = svgElement.ownerSVGElement.createSVGTransform();
newTransform.setTranslate(100, 100);

// 変形リストに追加
transformList.appendItem(newTransform);
```

この例では、SVG 要素に対して平行移動の変形を追加しています。

## 説明
SVGAnimatedTransformList を使用する際の一般的な注意点：

- **アニメーションの同期**: アニメーションを行う際には、`animVal` と `baseVal` の値が異なる場合があります。これにより、意図しない変形が見られることがありますので、アニメーションの完了を確認することが重要です。
- **サポートされているブラウザ**: SVG とそのアニメーション機能は、すべてのブラウザで均一にサポートされているわけではありません。特に古いブラウザでは、SVG の挙動が異なることがあります。

## 一文の要約
SVGAnimatedTransformList は、SVG 要素のアニメーション変形を管理し、動的な視覚効果を提供するための JavaScript オブジェクトです。