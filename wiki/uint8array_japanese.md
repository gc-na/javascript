<!--
Meta Description: # Uint8Array: JavaScriptにおける8ビット符号なし整数配列の詳細ガイド ## 概要 `Uint8Array`は、JavaScriptで8ビットの符号なし整数の配列を扱うためのTypedArrayの一種です。この型の配列は、効率的なメモリ管理やバイナリデータの操作に適しています。...
Meta Keywords: uint8array, const, new, javascript, arr
-->

# Uint8Array: JavaScriptにおける8ビット符号なし整数配列の詳細ガイド

## 概要
`Uint8Array`は、JavaScriptで8ビットの符号なし整数の配列を扱うためのTypedArrayの一種です。この型の配列は、効率的なメモリ管理やバイナリデータの操作に適しています。

## ドキュメンテーション
`Uint8Array`は、データバッファを扱うための高パフォーマンスな方法を提供します。以下にその目的と使用方法を詳述します。

### 目的
- バイナリデータの操作
- WebAPIとのインターフェース（例：Canvas、WebGLなど）
- データの効率的なストレージと転送

### 使用方法
`Uint8Array`を生成する方法は複数あります：

1. **指定したサイズの配列を作成する**:
   ```javascript
   const array = new Uint8Array(10); // 長さ10のUint8Arrayを作成
   ```

2. **既存の配列からコピーする**:
   ```javascript
   const arr = [1, 2, 3];
   const array = new Uint8Array(arr); // arrの内容を持つUint8Arrayを作成
   ```

3. **ArrayBufferから生成する**:
   ```javascript
   const buffer = new ArrayBuffer(10);
   const array = new Uint8Array(buffer); // ArrayBufferからUint8Arrayを作成
   ```

### プロパティとメソッド
- **プロパティ**:
  - `length`: 配列の長さを返します。

- **メソッド**:
  - `set()`: 他の配列やTypedArrayから値を設定します。
  - `subarray()`: 新しいUint8Arrayを作成し、元の配列の指定した範囲を参照します。

## 例
以下に`Uint8Array`の基本的な使用例を示します。

```javascript
// 新しいUint8Arrayを作成
const uint8 = new Uint8Array(5);
uint8[0] = 255; // 値を設定
console.log(uint8); // Uint8Array(5) [255, 0, 0, 0, 0]

// 配列からUint8Arrayを作成
const arr = [1, 2, 3, 4, 5];
const uint8FromArr = new Uint8Array(arr);
console.log(uint8FromArr); // Uint8Array(5) [1, 2, 3, 4, 5]

// subarrayを使用
const subArray = uint8FromArr.subarray(1, 4);
console.log(subArray); // Uint8Array(3) [2, 3, 4]
```

## 説明
`Uint8Array`を使用する際の一般的な落とし穴や注意点は以下の通りです。

- **値の範囲**: `Uint8Array`は0から255までの値しか保持できません。それを超える値を設定すると、自動的にラップアラウンドが発生します。例：`uint8[0] = 256;`は`0`になります。
- **メモリ管理**: `Uint8Array`はArrayBufferに基づいているため、メモリ消費に注意が必要です。大きなデータを扱う際は、適切にサイズを管理しましょう。

## 一文要約
`Uint8Array`は、JavaScriptで効率的に8ビットの符号なし整数を扱うためのTypedArrayです。