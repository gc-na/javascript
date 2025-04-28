<!--
Meta Description: # WebGLRenderingContext: JavaScriptでの3Dグラフィックス描画 ## 概要 `WebGLRenderingContext`は、JavaScriptを使用してWeb上で3Dおよび2Dグラフィックスを描画するためのインターフェースです。このコンテキストは、HTML5の`...
Meta Keywords: canvas, webglrenderingcontext, webgl, getcontext, const
-->

# WebGLRenderingContext: JavaScriptでの3Dグラフィックス描画

## 概要
`WebGLRenderingContext`は、JavaScriptを使用してWeb上で3Dおよび2Dグラフィックスを描画するためのインターフェースです。このコンテキストは、HTML5の`<canvas>`要素を使用して、GPUを活用した高性能なグラフィックスを実現します。

## ドキュメント
### 目的
`WebGLRenderingContext`は、WebGLを用いてハードウェアアクセラレーションされたグラフィックスを生成するためのAPIです。このコンテキストを通じて、開発者はシェーダーを使用して複雑なグラフィックスを描画したり、テクスチャを利用したりすることができます。

### 使用方法
1. **キャンバスの作成**: `HTML`で`<canvas>`要素を作成します。
2. **コンテキストの取得**: JavaScriptで`getContext()`メソッドを使用して、`WebGLRenderingContext`を取得します。
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const gl = canvas.getContext('webgl');
   ```
3. **シェーダーの作成**: 頂点シェーダーとフラグメントシェーダーを作成し、コンパイルします。
4. **バッファの設定**: 頂点データを保持するためのバッファを作成します。
5. **描画**: `drawArrays()`または`drawElements()`メソッドを使用して、描画を行います。

### 詳細
- **プロパティ**: `WebGLRenderingContext`には、`clearColor()`, `viewport()`, `enable()`, `disable()`など、様々なプロパティとメソッドがあります。
- **エラーハンドリング**: WebGLは、描画エラーを識別するためのエラーチェック機能を提供します。`getError()`メソッドを使用してエラーを取得できます。
- **ブラウザサポート**: 最新のブラウザは、WebGLをサポートしていますが、一部の古いブラウザでは制限があります。

## 例
以下は、基本的なWebGLの使用例です。

```html
<canvas id="myCanvas" width="500" height="500"></canvas>
<script>
   const canvas = document.getElementById('myCanvas');
   const gl = canvas.getContext('webgl');

   if (!gl) {
       console.log("WebGL not supported, falling back on experimental-webgl");
       gl = canvas.getContext('experimental-webgl');
   }

   gl.clearColor(0.0, 0.0, 0.0, 1.0); // 背景色を黒に設定
   gl.clear(gl.COLOR_BUFFER_BIT); // カラーバッファをクリア
</script>
```

## 説明
- **パフォーマンス**: WebGLはGPUを使用するため、CPUベースの描画よりも高速です。ただし、リソースの管理が重要です。
- **互換性**: WebGLでは、異なるブラウザ間の動作の違いに注意が必要です。特に、シェーダーのサポートやエラーハンドリングに関する互換性が影響します。
- **デバッグ**: シェーダーのデバッグは難しいことがあります。`OES_standard_derivatives`拡張を利用して、デバッグを容易にすることができます。

## 一文要約
`WebGLRenderingContext`は、JavaScriptを使用して高性能な3Dグラフィックスを描画するためのWebGLインターフェースです。