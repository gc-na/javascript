<!--
Meta Description: # WebGLActiveInfo: JavaScriptにおけるWebGLの詳細情報 ## 概要 `WebGLActiveInfo`は、WebGL APIにおいてシェーダープログラムのアクティブなシェーダー変数に関する情報を提供するオブジェクトです。このオブジェクトは、シェーダーにおける変数の名前...
Meta Keywords: activeinfo, const, size, program, name
-->

# WebGLActiveInfo: JavaScriptにおけるWebGLの詳細情報

## 概要
`WebGLActiveInfo`は、WebGL APIにおいてシェーダープログラムのアクティブなシェーダー変数に関する情報を提供するオブジェクトです。このオブジェクトは、シェーダーにおける変数の名前、型、サイズなどの属性を取得するために使用されます。

## ドキュメンテーション
`WebGLActiveInfo`は、シェーダーの変数に関する情報を表すオブジェクトで、以下のプロパティを持っています：

- `name`: 変数の名前を表す文字列。
- `type`: 変数のデータ型を示す整数。この値は、WebGLRenderingContextの型定数に対応しています。
- `size`: 変数が配列である場合の要素数を示す整数。

### 使用方法
`WebGLActiveInfo`オブジェクトは、`getActiveAttrib`や`getActiveUniform`メソッドを使用して取得します。これらのメソッドは、シェーダープログラムにおけるアクティブな属性またはユニフォームの情報を取得します。

```javascript
// WebGLコンテキストの取得
const canvas = document.createElement("canvas");
const gl = canvas.getContext("webgl");

// シェーダープログラムの作成とリンク
const program = gl.createProgram();
// シェーダーの作成とプログラムへのアタッチは省略

// アクティブな属性の取得
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
    const activeInfo = gl.getActiveAttrib(program, i);
    console.log(`Name: ${activeInfo.name}, Type: ${activeInfo.type}, Size: ${activeInfo.size}`);
}

// アクティブなユニフォームの取得
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numUniforms; i++) {
    const activeInfo = gl.getActiveUniform(program, i);
    console.log(`Name: ${activeInfo.name}, Type: ${activeInfo.type}, Size: ${activeInfo.size}`);
}
```

## 例
以下は、`WebGLActiveInfo`を使用してシェーダープログラムのアクティブな属性やユニフォーム情報を取得する基本的な例です。

```javascript
const canvas = document.createElement("canvas");
const gl = canvas.getContext("webgl");

// シェーダーの作成（省略）
// ...

// プログラムのリンク
gl.linkProgram(program);

// アクティブ属性の情報をログに出力
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
    const activeInfo = gl.getActiveAttrib(program, i);
    console.log(`Attribute Name: ${activeInfo.name}, Type: ${activeInfo.type}, Size: ${activeInfo.size}`);
}

// アクティブユニフォームの情報をログに出力
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numUniforms; i++) {
    const activeInfo = gl.getActiveUniform(program, i);
    console.log(`Uniform Name: ${activeInfo.name}, Type: ${activeInfo.type}, Size: ${activeInfo.size}`);
}
```

## 説明
`WebGLActiveInfo`を使用する際の一般的な落とし穴や注意点は以下の通りです：

- 属性やユニフォームの名前が変更される場合があります。例えば、シェーダーのコンパイラによって最適化されることがありますので、実際の名前が思ったものと異なる場合があります。
- 型は整数で返されるため、どのデータ型に対応しているかは、WebGLの定数（例：`gl.FLOAT`、`gl.INT`など）を参照する必要があります。
- 配列のサイズは、`size`プロパティで確認できますが、配列のサイズが1以上である場合、名前にインデックスが付加されることに注意が必要です（例: `myArray[0]`、`myArray[1]`）。

## 一文要約
`WebGLActiveInfo`は、シェーダープログラムのアクティブな変数に関する詳細情報を提供するWebGL APIのオブジェクトです。