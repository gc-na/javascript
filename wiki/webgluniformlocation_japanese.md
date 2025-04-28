<!--
Meta Description: # WebGLUniformLocation: JavaScriptにおけるWebGLのユニフォームロケーション ## 概要 `WebGLUniformLocation`は、WebGLにおけるシェーダープログラムのユニフォーム変数の位置を表すオブジェクトです。これにより、JavaScriptからWe...
Meta Keywords: program, const, webgluniformlocation, ユニフォームロケーションの取得, getuniformlocation
-->

# WebGLUniformLocation: JavaScriptにおけるWebGLのユニフォームロケーション

## 概要
`WebGLUniformLocation`は、WebGLにおけるシェーダープログラムのユニフォーム変数の位置を表すオブジェクトです。これにより、JavaScriptからWebGLシェーダーにデータを送信する際に、ユニフォーム変数を効率的に管理できます。

## ドキュメンテーション
`WebGLUniformLocation`は、WebGLコンテキストでシェーダープログラムのユニフォーム変数の位置を示すために使用されます。ユニフォーム変数は、シェーダーの実行中にグラフィックスパイプラインにデータを供給するための手段であり、例えば色、変換行列、テクスチャサンプラーなどが含まれます。

### 目的
主に、シェーダープログラムに渡したいデータの位置を特定し、そのデータを設定するために使用されます。この情報を基に、WebGLは適切なデータをシェーダーに適用します。

### 使用方法
1. **ユニフォームロケーションの取得**: `gl.getUniformLocation(program, name)`メソッドを使用して、シェーダープログラムのユニフォーム変数のロケーションを取得します。
2. **ユニフォームの設定**: 取得したロケーションを使用して、`gl.uniform*`ファミリーのメソッドで値を設定します。

### 詳細
- `program`: シェーダープログラムオブジェクト。
- `name`: ユニフォーム変数の名前（シェーダー内で定義されたもの）。
- 戻り値: `WebGLUniformLocation`オブジェクト。無効な場合は`null`が返されます。

## 例
```javascript
// WebGLコンテキストを取得
const canvas = document.getElementById("myCanvas");
const gl = canvas.getContext("webgl");

// シェーダープログラムを作成
const vertexShaderSource = `...`; // 頂点シェーダーのソースコード
const fragmentShaderSource = `...`; // フラグメントシェーダーのソースコード
const program = createProgram(gl, vertexShaderSource, fragmentShaderSource);

// ユニフォームロケーションの取得
const uColorLocation = gl.getUniformLocation(program, "u_Color");

// シェーダープログラムの使用
gl.useProgram(program);

// ユニフォームの設定
gl.uniform4f(uColorLocation, 1.0, 0.0, 0.0, 1.0); // 赤色
```

## 説明
- **ユニフォームロケーションの取得**: ユニフォーム変数の名前が誤っている場合、`getUniformLocation`は`null`を返します。シェーダー内で正確に名前を確認してください。
- **データ型の不一致**: `gl.uniform*`メソッドを使用する際、データ型が期待する型と異なる場合、エラーが発生します。例えば、`gl.uniform1f`は浮動小数点数を期待します。
- **プログラムの使用前に設定**: シェーダープログラムを有効にする前にユニフォームを設定することはできません。`gl.useProgram(program)`を呼び出してから設定してください。

## 一文の要約
`WebGLUniformLocation`は、WebGLシェーダープログラムのユニフォーム変数の位置を管理し、データを効率的にシェーダーに送信するために使用される重要なオブジェクトです。