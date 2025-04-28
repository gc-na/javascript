<!--
Meta Description: # WebGLProgram: JavaScriptにおけるWebGLプログラムの理解 ## 概要 `WebGLProgram`は、WebGL APIでシェーダープログラムを表現するオブジェクトです。シェーダープログラムは、GPUで実行されるコードであり、頂点とフラグメントの処理を行います。このオブ...
Meta Keywords: webglprogram, const, program, void, vertexshader
-->

# WebGLProgram: JavaScriptにおけるWebGLプログラムの理解

## 概要
`WebGLProgram`は、WebGL APIでシェーダープログラムを表現するオブジェクトです。シェーダープログラムは、GPUで実行されるコードであり、頂点とフラグメントの処理を行います。このオブジェクトを使用することで、WebGLを通じて3Dグラフィックスを描画する際の効率的なシェーダー管理が可能になります。

## ドキュメンテーション
`WebGLProgram`は、`WebGLRenderingContext`の`createProgram()`メソッドで作成され、シェーダーオブジェクト（`WebGLShader`）をリンクしてプログラムを構築します。これにより、GPUがシェーダーを実行できるようになります。

### 使用法
1. **シェーダーの作成**: プログラムにリンクするための頂点シェーダーとフラグメントシェーダーを作成します。
2. **プログラムの作成**: `createProgram()`メソッドを使用して新しい`WebGLProgram`を作成します。
3. **シェーダーの添付**: `attachShader()`メソッドを使って、シェーダーをプログラムに添付します。
4. **リンクの実行**: `linkProgram()`メソッドでプログラムをリンクし、使用可能な状態にします。
5. **プログラムの使用**: `useProgram()`メソッドを使用して、描画時にこのプログラムを使用します。

### 例
以下は、`WebGLProgram`を使用した基本的な例です。

```javascript
// WebGLコンテキストの取得
const canvas = document.getElementById('myCanvas');
const gl = canvas.getContext('webgl');

// シェーダーソース
const vertexShaderSource = `
    attribute vec4 a_position;
    void main(void) {
        gl_Position = a_position;
    }
`;

const fragmentShaderSource = `
    void main(void) {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // 赤色
    }
`;

// シェーダーの作成
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);

// プログラムの作成とリンク
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// プログラムを使用
gl.useProgram(program);
```

## 説明
`WebGLProgram`を使用する際の一般的な落とし穴として、シェーダーのコンパイルエラーやプログラムのリンクエラーがあります。`getShaderParameter()`や`getProgramParameter()`メソッドを使用して、エラーの詳細を確認することが重要です。また、シェーダーのソースコードが正しい構文であることを確認し、必要な属性やユニフォームが正しく設定されているかどうかも注意が必要です。

## 一文の要約
`WebGLProgram`は、WebGLでGPUを活用するためのシェーダープログラムを管理する重要なオブジェクトです。