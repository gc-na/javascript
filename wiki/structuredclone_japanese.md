<!--
Meta Description: # JavaScriptのstructuredCloneメソッド：オブジェクトを深くコピーするための完全ガイド ## 概要 `structuredClone`は、JavaScriptにおけるオブジェクトを深くコピーするためのメソッドです。このメソッドは、クロスオリジンのデータや特定の型（例えば、Da...
Meta Keywords: structuredclone, hobbies, original, reading, gaming
-->

# JavaScriptのstructuredCloneメソッド：オブジェクトを深くコピーするための完全ガイド

## 概要
`structuredClone`は、JavaScriptにおけるオブジェクトを深くコピーするためのメソッドです。このメソッドは、クロスオリジンのデータや特定の型（例えば、DateオブジェクトやMap）を含む複雑なオブジェクトの複製を可能にします。

## ドキュメンテーション
### 目的
`structuredClone`は、ネイティブなオブジェクトを含む任意のオブジェクトを安全にコピーするために設計されています。従来のコピー方法（`Object.assign`やスプレッド構文）では、オブジェクトの参照が共有されるため、元のオブジェクトの変更がコピーに影響を与えてしまいますが、`structuredClone`を使用することで、完全に独立したコピーを作成できます。

### 使用方法
`structuredClone`メソッドは次のように使用します：

```javascript
const clonedObject = structuredClone(originalObject);
```

### 詳細
- **引数**: 
  - `value`: コピーしたい任意のJavaScriptの値。
  
- **戻り値**: 
  - 深くコピーされた新しいオブジェクト。

- **サポートされる型**: 
  - `structuredClone`は、通常のオブジェクトの他に、Array、ArrayBuffer、Blob、File、Map、Set、Date、RegExp、TypedArrayなど、さまざまなデータ型をサポートしています。

- **例外**: 
  - `structuredClone`は、循環参照を持つオブジェクトや、Function、DOMノードを含むオブジェクトをコピーしようとすると、TypeErrorをスローします。

## 例
以下は、`structuredClone`の基本的な使用例です。

### 基本的な使用例

```javascript
const original = {
    name: "Alice",
    age: 30,
    hobbies: ["reading", "gaming"]
};

const clone = structuredClone(original);

console.log(clone); // { name: 'Alice', age: 30, hobbies: [ 'reading', 'gaming' ] }

// コピーは独立しているため、元のオブジェクトを変更してもクローンには影響しない
original.hobbies.push("hiking");
console.log(original.hobbies); // [ 'reading', 'gaming', 'hiking' ]
console.log(clone.hobbies);    // [ 'reading', 'gaming' ]
```

## 説明
`structuredClone`を使用する際の一般的な注意点や注意事項は以下の通りです。

- **循環参照**: 循環参照を持つオブジェクトをコピーしようとすると、TypeErrorが発生します。循環参照を事前に処理する必要があります。
  
- **非対応の型**: 関数やDOMノードなど、`structuredClone`がサポートしていない型をコピーしようとすると、エラーが発生します。これらの型を扱う際は、他の方法を検討してください。

- **型の保持**: `structuredClone`は、DateオブジェクトをDateオブジェクトとして、MapをMapとして保持します。これにより、データの整合性が保たれます。

## 一文要約
`structuredClone`は、JavaScriptにおいてオブジェクトを深くコピーするための強力なメソッドで、ネイティブなデータ型を正確に保持しながら新しいインスタンスを作成します。