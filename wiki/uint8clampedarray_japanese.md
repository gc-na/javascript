<!--
Meta Description: # Uint8ClampedArray: JavaScriptの高精度な整数配列 ## 概要 `Uint8ClampedArray`は、JavaScriptにおいて、0から255の範囲の整数を格納するための配列です。特に、画像データ処理やグラフィックスアプリケーションにおいて、値をクリッピング（制限...
Meta Keywords: uint8clampedarray, 255, let, new, javascript
-->

# Uint8ClampedArray: JavaScriptの高精度な整数配列

## 概要
`Uint8ClampedArray`は、JavaScriptにおいて、0から255の範囲の整数を格納するための配列です。特に、画像データ処理やグラフィックスアプリケーションにおいて、値をクリッピング（制限）する必要がある場合に使用されます。

## ドキュメンテーション
`Uint8ClampedArray`は、TypedArrayの一種であり、各要素が8ビットの符号なし整数（0〜255）である配列を作成します。要素に対して指定された値が範囲外の場合、値は自動的に最小値または最大値にクリップされます。

### 使用法
`Uint8ClampedArray`は、以下のように生成することができます：

```javascript
// 新しいUint8ClampedArrayを作成
let array = new Uint8ClampedArray(length);
```

ここで、`length`は配列の長さを指定します。また、配列を初期化するために、既存の配列や配列バッファを引数として渡すこともできます。

### コンストラクタの例

```javascript
// 長さ5のUint8ClampedArrayを作成
let clampedArray = new Uint8ClampedArray(5); // [0, 0, 0, 0, 0]

// 配列を初期化
let initializedArray = new Uint8ClampedArray([256, 128, -10, 300]); // [255, 128, 0, 255]
```

## 例
以下は、`Uint8ClampedArray`の基本的な使用例です。

```javascript
// 画像データのピクセル値を扱う例
let imageData = new Uint8ClampedArray([10, 20, 300, -5]);

console.log(imageData); // 出力: Uint8ClampedArray(4) [ 10, 20, 255, 0 ]
```

## 説明
`Uint8ClampedArray`を使用する際の一般的な注意点として、次のようなものがあります。

- **数値のクリッピング**: 値が0未満の場合は0に、255を超える場合は255に自動的に修正されるため、特定の範囲に収める必要があるデータ処理に適しています。
- **パフォーマンス**: TypedArrayであるため、通常のJavaScript配列よりもメモリ効率が良く、数値計算において高速です。

### よくある落とし穴
- `Uint8ClampedArray`への直接代入時に、意図しないクリッピングが発生することがあります。たとえば、`array[0] = 256;`は、`array[0]`を255にクリップします。
- サイズが明示的に指定されない場合、初期化された要素はすべて0になります。

## 一文要約
`Uint8ClampedArray`は、0から255の範囲の整数を格納し、値が範囲外の場合に自動的にクリッピングされるJavaScriptのTypedArrayです。