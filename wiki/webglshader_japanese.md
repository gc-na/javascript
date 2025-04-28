<!--
Meta Description: # WebGLShader (ウェブGLシェーダー) - JavaScriptにおける重要なコンポーネント ## 概要 WebGLShaderは、WebGL APIで使用されるシェーダープログラムの基本的な構成要素です。シェーダーは、グラフィックスパイプライン内で実行される小さなプログラムであり、主...
Meta Keywords: shader, const, webglshaderは, createshader, shadersource
-->

# WebGLShader (ウェブGLシェーダー) - JavaScriptにおける重要なコンポーネント

## 概要
WebGLShaderは、WebGL APIで使用されるシェーダープログラムの基本的な構成要素です。シェーダーは、グラフィックスパイプライン内で実行される小さなプログラムであり、主に頂点シェーダーとフラグメントシェーダーの2種類があります。これらは、3Dグラフィックスを描画する際に、頂点の処理やピクセルの色付けを行います。

## ドキュメンテーション
WebGLShaderは、WebGLコンテキストにおいてシェーダーを定義するためのオブジェクトです。シェーダーは、GLSL（OpenGL Shading Language）で記述され、WebGLコンテキストに関連付けられた後、描画操作を行うために使用されます。

- **目的**: WebGLShaderは、グラフィックスの描画に必要なシェーダープログラムを作成するために使用されます。
- **使用法**:
  1. シェーダーオブジェクトを作成するには、`gl.createShader(type)`メソッドを使用します。`type`は、`gl.VERTEX_SHADER`または`gl.FRAGMENT_SHADER`のいずれかを指定します。
  2. GLSLコードをシェーダーオブジェクトにセットするには、`gl.shaderSource(shader, source)`メソッドを呼び出します。
  3. シェーダーをコンパイルするには、`gl.compileShader(shader)`を使用します。
  4. コンパイルが成功したかどうかを確認するには、`gl.getShaderParameter(shader, gl.COMPILE_STATUS)`を使用します。
  5. シェーダーの情報ログを取得するには、`gl.getShaderInfoLog(shader)`を利用します。

## 例
以下は、頂点シェーダーとフラグメントシェーダーを作成する基本的な例です。

```javascript
// WebGLコンテキストの取得
const canvas = document.getElementById("canvas");
const gl = canvas.getContext("webgl");

// 頂点シェーダーの作成
const vertexShaderSource = `
    attribute vec4 a_position;
    void main() {
        gl_Position = a_position;
    }
`;
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

// フラグメントシェーダーの作成
const fragmentShaderSource = `
    void main() {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // 赤色
    }
`;
const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);
```

## 説明
WebGLShaderを使用する際の一般的な落とし穴や注意点は以下の通りです。

- **コンパイルエラー**: GLSLコードに誤りがあると、シェーダーは正常にコンパイルされません。`gl.getShaderInfoLog(shader)`を使ってエラーメッセージを確認することが重要です。
- **シェーダーのリンク**: シェーダーをプログラムにリンクする際、頂点シェーダーとフラグメントシェーダーの間で一致しない属性や uniform があると、描画が正しく行われない場合があります。
- **リソース管理**: 使用が終わったシェーダーは、`gl.deleteShader(shader)`を使って適切に解放することが推奨されます。

## 一文要約
WebGLShaderは、WebGLにおけるグラフィックス描画のためのシェーダープログラムを定義する重要な要素です。