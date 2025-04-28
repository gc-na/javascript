<!--
Meta Description: # JavaScriptにおけるWeakMapの完全ガイド ## 概要 WeakMapは、オブジェクトをキーとして使用し、ガーベジコレクションの対象となる弱い参照を保持するコレクションです。これにより、メモリ使用量を削減し、オブジェクトのライフサイクルを管理しやすくします。 ## ドキュメンテーショ...
Meta Keywords: weakmap, obj1, weakmapは, console, log
-->

# JavaScriptにおけるWeakMapの完全ガイド

## 概要
WeakMapは、オブジェクトをキーとして使用し、ガーベジコレクションの対象となる弱い参照を保持するコレクションです。これにより、メモリ使用量を削減し、オブジェクトのライフサイクルを管理しやすくします。

## ドキュメンテーション

### 目的
WeakMapは、オブジェクトをキーとして、任意の値を関連付けるための特別なマップです。WeakMapのキーは弱い参照であり、キーが他の参照を持たれていない場合に自動的にガーベジコレクションされるため、メモリリークを防ぎます。

### 使用法
WeakMapは、`new WeakMap()`でインスタンスを作成します。WeakMapは以下のメソッドを持っています：

- **set(key, value)**: 指定したキーに値を設定します。
- **get(key)**: 指定したキーに関連付けられた値を取得します。
- **has(key)**: 指定したキーがWeakMapに存在するかどうかをチェックします。
- **delete(key)**: 指定したキーとその関連付けられた値を削除します。

### 詳細
- WeakMapのキーはオブジェクトでなければなりません。プリミティブ値（数値、文字列、ブール値など）は使用できません。
- WeakMapはイテラブルではないため、全てのキーや値を列挙することはできません。
- WeakMapは、キーが他の場所で参照されなくなると、そのエントリは自動的に削除されます。

## 例

### 基本的な使用例

```javascript
// WeakMapの作成
const weakmap = new WeakMap();

// オブジェクトの作成
const obj1 = {};
const obj2 = {};

// 値の設定
weakmap.set(obj1, 'value1');
weakmap.set(obj2, 'value2');

// 値の取得
console.log(weakmap.get(obj1)); // 'value1'
console.log(weakmap.get(obj2)); // 'value2'

// 存在確認
console.log(weakmap.has(obj1)); // true
console.log(weakmap.has(obj2)); // true

// 削除
weakmap.delete(obj1);
console.log(weakmap.has(obj1)); // false
```

## 説明
WeakMapを使用する際にはいくつかの注意点があります。

- **キーの制限**: WeakMapのキーは必ずオブジェクトでなければならず、プリミティブな値は使用できません。
- **ガーベジコレクション**: オブジェクトがWeakMapの外で参照されなくなると、そのエントリは自動的に削除されます。これにより、意図しないデータの保持が防げます。
- **イテラブルではない**: WeakMapはイテレーションをサポートしていないため、全てのエントリを列挙することはできません。この特性は、WeakMapがメモリ使用の最適化に貢献しています。

## 一文要約
WeakMapは、オブジェクトをキーとして使用し、ガーベジコレクションを利用してメモリ管理を効率化するためのコレクションです。