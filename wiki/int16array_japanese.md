<!--
Meta Description: # Int16Array: JavaScriptにおける16ビット整数配列の理解 ## 概要 `Int16Array`は、JavaScriptのTyped Arraysの一種で、16ビットの符号付き整数の配列を扱うためのオブジェクトです。主にバイナリデータを効率的に操作するために使用されます。 ##...
Meta Keywords: int16array, const, new, javascript, subarray
-->

# Int16Array: JavaScriptにおける16ビット整数配列の理解

## 概要
`Int16Array`は、JavaScriptのTyped Arraysの一種で、16ビットの符号付き整数の配列を扱うためのオブジェクトです。主にバイナリデータを効率的に操作するために使用されます。

## ドキュメンテーション
`Int16Array`は、特に数値データの処理を行う際に、メモリ効率が良く、高速なアクセスを提供します。以下にその詳細を示します。

### 目的
`Int16Array`は、16ビットの符号付き整数を効率的に格納するために設計されており、バイナリデータの操作や、特定のデータフォーマットとのやり取りに役立ちます。

### 使用法
`Int16Array`は以下の方法で作成できます。

1. **配列の作成**:
   ```javascript
   const int16Array = new Int16Array(length);
   ```

2. **既存の配列からの作成**:
   ```javascript
   const int16ArrayFromArray = new Int16Array([1, 2, 3]);
   ```

3. **ArrayBufferからの作成**:
   ```javascript
   const buffer = new ArrayBuffer(8); // 8バイトのバッファ
   const int16ArrayFromBuffer = new Int16Array(buffer);
   ```

### プロパティとメソッド
- **length**: 配列の要素数を返します。
- **set()**: 他の配列またはTyped Arrayの値を設定します。
- **subarray()**: 指定した範囲の要素を持つ新しい配列を返します。

## 例
以下は`Int16Array`の基本的な使用例です。

```javascript
// 新しいInt16Arrayを作成
const int16Array = new Int16Array(5);

// 値を設定
int16Array[0] = 1000;
int16Array[1] = -2000;
int16Array[2] = 3000;

// 配列の内容の表示
console.log(int16Array); // Int16Array(5) [ 1000, -2000, 3000, 0, 0 ]

// 配列の長さ
console.log(int16Array.length); // 5

// サブアレイの作成
const subArray = int16Array.subarray(1, 3);
console.log(subArray); // Int16Array(2) [ -2000, 3000 ]
```

## 説明
`Int16Array`を使用する際の一般的な注意点や落とし穴は以下の通りです。

- **範囲外の値**: `Int16Array`は16ビットの符号付き整数を扱うため、-32768から32767の範囲外の値を設定すると、オーバーフローが発生します。たとえば、32768を設定すると、-32768として扱われます。
- **メモリ管理**: Typed Arrayは`ArrayBuffer`に基づいているため、バッファのサイズを適切に管理することが重要です。

## 一文での要約
`Int16Array`は、JavaScriptで16ビットの符号付き整数を効率的に扱うためのTyped Arrayです。