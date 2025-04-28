<!--
Meta Description: # JavaScriptのSymbol: ユニークな識別子の作成と使用 ## 概要 JavaScriptにおける`Symbol`は、ユニークで変更不可能な識別子を生成するためのデータ型です。主にオブジェクトのプロパティを定義する際に、名前の衝突を避ける目的で使用されます。 ## ドキュメント `Sy...
Meta Keywords: symbol, const, sym1, sym2, console
-->

# JavaScriptのSymbol: ユニークな識別子の作成と使用

## 概要
JavaScriptにおける`Symbol`は、ユニークで変更不可能な識別子を生成するためのデータ型です。主にオブジェクトのプロパティを定義する際に、名前の衝突を避ける目的で使用されます。

## ドキュメント
`Symbol`はECMAScript 2015（ES6）で導入されたもので、次の特徴を持っています。

### 目的
- プロパティ名の衝突を避けるためにユニークな識別子を作成します。
- オブジェクトのプライベートプロパティを作成する手段として機能します。

### 使用法
`Symbol`を生成するには、`Symbol()`関数を呼び出します。以下は基本的な構文です。

```javascript
const mySymbol = Symbol('description');
```

ここで、`description`はオプションの文字列で、デバッグ時に使用される説明になりますが、`Symbol`自体には影響しません。

### 詳細
- `Symbol`はプリミティブ型であり、他のデータ型と混同することはありません。
- 各`Symbol`はユニークであり、同じ引数で生成された`Symbol`も異なるものとして扱われます。
- `Symbol`はオブジェクトのプロパティキーとして利用可能です。

## 例
以下は、`Symbol`の基本的な使用例です。

```javascript
const sym1 = Symbol('example');
const sym2 = Symbol('example');

console.log(sym1 === sym2); // false

const obj = {
    [sym1]: 'value1',
    [sym2]: 'value2'
};

console.log(obj[sym1]); // 'value1'
console.log(obj[sym2]); // 'value2'
```

## 説明
`Symbol`にはいくつかの注意点があります。

- **ユニーク性**: 同じ説明を持つ`Symbol`は異なるものであるため、比較する際には注意が必要です。
- **可視性**: `Symbol`で定義されたプロパティは通常のループ（例えば`for...in`）では見えません。`Object.getOwnPropertySymbols()`メソッドを使用することで取得できます。
- **グローバルシンボル**: `Symbol.for()`メソッドを使用すると、グローバルなシンボルを作成し、同じシンボルを再利用することができます。

## 一文の要約
JavaScriptの`Symbol`は、ユニークで変更不可能な識別子を生成し、プロパティ名の衝突を防ぐために使用されるデータ型です。