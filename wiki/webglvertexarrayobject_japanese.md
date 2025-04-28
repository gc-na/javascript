<!--
Meta Description: # WebGLVertexArrayObject: JavaScriptにおける高性能グラフィックスのための基礎 ## 概要 `WebGLVertexArrayObject`は、WebGLにおいて頂点データの状態を効率的に管理するためのオブジェクトです。これにより、複数のバッファと属性の設定を一元管...
Meta Keywords: const, webglvertexarrayobject, ext, oes_vertex_array_object, positionlocation
-->

# WebGLVertexArrayObject: JavaScriptにおける高性能グラフィックスのための基礎

## 概要
`WebGLVertexArrayObject`は、WebGLにおいて頂点データの状態を効率的に管理するためのオブジェクトです。これにより、複数のバッファと属性の設定を一元管理でき、描画パフォーマンスを向上させることができます。

## ドキュメンテーション
`WebGLVertexArrayObject`は、主に3Dグラフィックスを描画するために使用されます。これを利用することで、頂点バッファや属性の設定を簡素化し、描画処理を効率化できます。

### 目的
- 複数の頂点バッファと属性を管理する。
- 描画状態を簡単に切り替えることができる。
- パフォーマンス向上。

### 使用方法
1. **作成**: `getExtension`メソッドを使って`OES_vertex_array_object`拡張を取得し、`createVertexArray`メソッドで新しいVAOを作成します。
2. **バインド**: 作成したVAOを`bindVertexArray`メソッドでバインドします。
3. **設定**: 頂点バッファと属性を設定します。
4. **描画**: `drawArrays`または`drawElements`を使用して描画します。
5. **アンバインド**: 描画が終わったら`bindVertexArray(null)`でアンバインドします。

### 詳細
WebGLでは、デフォルトではVAOはサポートされていません。`OES_vertex_array_object`拡張を使用することで、VAOを利用できるようになります。これにより、異なる描画設定を迅速に切り替えることが可能となり、特に大量のオブジェクトを描画する際に有利です。

## 例
以下は、`WebGLVertexArrayObject`を使用した基本的な例です。

```javascript
const canvas = document.getElementById("myCanvas");
const gl = canvas.getContext("webgl");
const ext = gl.getExtension("OES_vertex_array_object");

const vao = ext.createVertexArrayOES();
ext.bindVertexArrayOES(vao);

// 頂点バッファの作成と設定
const vertexBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, vertexBuffer);
const vertices = new Float32Array([
    0, 1, 0,
    -1, -1, 0,
    1, -1, 0
]);
gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

// 頂点属性の設定
const positionLocation = gl.getAttribLocation(shaderProgram, "a_position");
gl.enableVertexAttribArray(positionLocation);
gl.vertexAttribPointer(positionLocation, 3, gl.FLOAT, false, 0, 0);

// 描画
gl.drawArrays(gl.TRIANGLES, 0, 3);

// アンバインド
ext.bindVertexArrayOES(null);
```

## 説明
- **共通の落とし穴**: VAOを使用する場合、必ず拡張機能がサポートされているか確認する必要があります。サポートされていないと、エラーが発生します。また、VAOをバインドする前に、適切なバッファをバインドしておくことが重要です。
- **注意点**: VAOはWebGL 2.0ではネイティブにサポートされているため、WebGL 1.0を使用している場合は、拡張機能を利用する必要があります。

## 一文の要約
`WebGLVertexArrayObject`は、WebGLにおいて効率的な頂点データの管理と描画を実現するための重要な機能です。