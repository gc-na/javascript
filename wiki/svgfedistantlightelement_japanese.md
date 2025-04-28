<!--
Meta Description: # SVGFEDistantLightElement: JavaScriptにおけるSVG遠方光源要素の解説 ## 概要 SVGFEDistantLightElementは、SVGフィルター効果の一部として使用される要素で、遠方からの光源を定義します。この要素は、SVGのフィルターを使用して描画され...
Meta Keywords: elevation, svgfedistantlightelementは, azimuth, distantlight, svg
-->

# SVGFEDistantLightElement: JavaScriptにおけるSVG遠方光源要素の解説

## 概要
SVGFEDistantLightElementは、SVGフィルター効果の一部として使用される要素で、遠方からの光源を定義します。この要素は、SVGのフィルターを使用して描画されたオブジェクトに対する照明効果をシミュレートするために重要です。

## ドキュメンテーション
### 目的
SVGFEDistantLightElementは、フィルター効果における遠方光源の位置を指定するために使用されます。これにより、オブジェクトの外観に陰影を加え、より立体的な表現を実現します。

### 使用法
- **プロパティ**
  - `azimuth`: 光源の方位角を指定します。0度は右、90度は上、180度は左、270度は下を指します。
  - `elevation`: 光源の高さを指定します。0度は水平、90度は垂直を意味します。

- **構文**
  ```javascript
  const distantLight = document.createElementNS("http://www.w3.org/2000/svg", "feDistantLight");
  distantLight.setAttribute("azimuth", "45");
  distantLight.setAttribute("elevation", "30");
  ```

### 詳細
SVGFEDistantLightElementは、SVGフィルター機能の一部であり、特に`feDiffuseLighting`や`feSpecularLighting`と組み合わせて使用されます。これにより、オブジェクトに光が当たる様子をリアルに表現でき、視覚的に魅力的な結果を得ることができます。

## 例
以下は、SVGFEDistantLightElementを使用した基本的な例です。

```html
<svg width="200" height="200">
  <defs>
    <filter id="lighting">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="5">
        <feDistantLight azimuth="45" elevation="30"/>
      </feDiffuseLighting>
    </filter>
  </defs>
  <rect x="10" y="10" width="180" height="180" fill="blue" filter="url(#lighting)"/>
</svg>
```
上記の例では、青い四角形に対して遠方光源を使った拡散照明効果が適用されます。

## 説明
- **一般的な落とし穴**
  - `azimuth`や`elevation`の値が不適切な場合、意図した効果が得られないことがあります。特に、`elevation`が0度の場合、光源はオブジェクトの面と平行になり、陰影が得られません。
  - SVGフィルターの使用は、ブラウザのサポートによって異なる場合があります。特に古いブラウザでは、期待通りの結果が得られないことがあります。

## 一文要約
SVGFEDistantLightElementは、SVGフィルター効果において遠方からの光源を定義し、オブジェクトにリアルな照明効果を与えるための重要な要素です。