<!--
Meta Description: # Int8Array: JavaScriptにおける符号付き8ビット整数配列 ## 概要 `Int8Array`は、JavaScriptにおける符号付き8ビット整数の配列を扱うためのTyped Arrayの一つです。この型の配列は、-128から127の範囲の整数を効率的に格納および操作することがで...
Meta Keywords: int8array, const, new, buffer, numbers
-->

# Int8Array: JavaScriptにおける符号付き8ビット整数配列

## 概要
`Int8Array`は、JavaScriptにおける符号付き8ビット整数の配列を扱うためのTyped Arrayの一つです。この型の配列は、-128から127の範囲の整数を効率的に格納および操作することができます。

## ドキュメンテーション
### 目的
`Int8Array`は、バイナリデータを扱う際に、特に数値データの効率的な保存と操作を可能にします。主にWebGLや音声処理、画像処理などのアプリケーションにおいて使用されます。

### 使用方法
`Int8Array`は、次のように作成できます。

1. **配列からの生成**:
   ```javascript
   const int8Array = new Int8Array([10, -20, 30]);
   ```

2. **長さを指定して生成**:
   ```javascript
   const int8Array = new Int8Array(5); // 長さ5の配列を生成
   ```

3. **ArrayBufferからの生成**:
   ```javascript
   const buffer = new ArrayBuffer(8);
   const int8Array = new Int8Array(buffer);
   ```

### 詳細
- **要素数**: `Int8Array`の要素数は、インスタンスを作成する際の引数に基づいて決定されます。
- **メソッド**: `Int8Array`は、一般的な配列メソッド（例: `map`, `forEach`, `filter`）を利用できます。
- **プロパティ**:
  - `length`: 配列の要素数を返します。
  - `buffer`: 元の`ArrayBuffer`を返します。

## 例
以下は、`Int8Array`の基本的な使用例です。

```javascript
// 1. 配列から生成
const numbers = new Int8Array([1, -2, 3, -4]);
console.log(numbers); // Int8Array(4) [ 1, -2, 3, -4 ]

// 2. 配列の要素を変更
numbers[0] = 10;
console.log(numbers[0]); // 10

// 3. 配列の長さを取得
console.log(numbers.length); // 4

// 4. ArrayBufferを使用
const buffer = new ArrayBuffer(4);
const int8ArrayFromBuffer = new Int8Array(buffer);
int8ArrayFromBuffer[0] = 127;
console.log(int8ArrayFromBuffer); // Int8Array(4) [ 127, 0, 0, 0 ]
```

## 説明
`Int8Array`を使用する際の一般的な落とし穴や注意点：

- **範囲制限**: `Int8Array`は-128から127の範囲内の整数しか扱えません。この範囲を超える値を代入すると、自動的にオーバーフローまたはアンダーフローが発生します。
- **オブジェクトとの互換性**: `Int8Array`は通常のJavaScript配列とは異なり、特定のメソッドやプロパティが制限されているため、通常の配列メソッドを使用する際は注意が必要です。
- **パフォーマンス**: Typed Arrayは、通常の配列よりもメモリの使用量が少なく、パフォーマンスが向上する場合がありますが、型の制約により一部の柔軟性が失われます。

## 一行要約
`Int8Array`は、JavaScriptにおいて効率的に符号付き8ビット整数を扱うためのTyped Arrayです。