<!--
Meta Description: # BigUint64Array: JavaScriptにおける64ビット符号なし整数の配列 ## 概要 `BigUint64Array`は、JavaScriptにおいて64ビットの符号なし整数の配列を扱うためのTyped Arrayの一つです。この配列は、ビット演算や大規模な整数計算を必要とするア...
Meta Keywords: biguint64array, arr, const, new, javascript
-->

# BigUint64Array: JavaScriptにおける64ビット符号なし整数の配列

## 概要
`BigUint64Array`は、JavaScriptにおいて64ビットの符号なし整数の配列を扱うためのTyped Arrayの一つです。この配列は、ビット演算や大規模な整数計算を必要とするアプリケーションにおいて特に有用です。

## ドキュメンテーション
`BigUint64Array`は、64ビットの符号なし整数を効率的に格納し、操作するための配列構造を提供します。このデータ型は、特にビット演算や高精度の整数計算を必要とする場合に役立ちます。

### 使用方法
`BigUint64Array`は、次の方法で初期化できます：

1. 空の配列を作成する:
   ```javascript
   const arr = new BigUint64Array(5); // 5つの要素を持つ空の配列
   ```

2. 他の配列やTyped Arrayから初期化する:
   ```javascript
   const arr = new BigUint64Array([1n, 2n, 3n]);
   ```

3. バッファから初期化する:
   ```javascript
   const buffer = new ArrayBuffer(16); // 16バイトのバッファ
   const arr = new BigUint64Array(buffer);
   ```

### 詳細
- `BigUint64Array`の各要素は、64ビットの符号なし整数（0から2^64-1までの範囲）です。
- 配列のサイズは、`length`プロパティで確認できます。
- 配列へのアクセスは、標準的なインデックスを使用します。
- 配列は、Typed Arrayの特性を持っており、バイナリデータの操作に最適化されています。

## 例
以下に、`BigUint64Array`の基本的な使用例を示します。

### 空の配列の作成
```javascript
const arr = new BigUint64Array(3);
console.log(arr); // BigUint64Array(3) [ 0n, 0n, 0n ]
```

### 配列の初期化
```javascript
const arr = new BigUint64Array([10n, 20n, 30n]);
console.log(arr); // BigUint64Array(3) [ 10n, 20n, 30n ]
```

### 要素へのアクセスと変更
```javascript
const arr = new BigUint64Array(2);
arr[0] = 100n;
arr[1] = 200n;
console.log(arr[0]); // 100n
console.log(arr[1]); // 200n
```

## 説明
`BigUint64Array`を使用する際の一般的な注意点は以下の通りです：

- `BigUint64Array`の要素に割り当てる値は、必ず`BigInt`型である必要があります。通常の数値（Number型）を使用すると自動的に変換されません。
- 配列のサイズは固定されているため、サイズを変更することはできません。新しいサイズの配列を作成する必要があります。
- `BigUint64Array`は、実行環境によってはサポートされていない場合があります。最新のブラウザやNode.jsを使用することをお勧めします。

## 一文要約
`BigUint64Array`は、JavaScriptにおいて64ビットの符号なし整数を効率的に扱うためのTyped Arrayです。