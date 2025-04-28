<!--
Meta Description: # JavaScriptにおけるイテレーター（Iterator）とは ## 概要 JavaScriptのイテレーターは、コレクション（配列、オブジェクトなど）の要素を順に処理するためのオブジェクトです。イテレーターは、データ構造を効率的に走査するための標準的な方法を提供します。 ## ドキュメンテー...
Meta Keywords: value, iterator, done, next, const
-->

# JavaScriptにおけるイテレーター（Iterator）とは

## 概要
JavaScriptのイテレーターは、コレクション（配列、オブジェクトなど）の要素を順に処理するためのオブジェクトです。イテレーターは、データ構造を効率的に走査するための標準的な方法を提供します。

## ドキュメンテーション
イテレーターは、特定のプロトコルに従うオブジェクトです。イテレーターを使用すると、コレクション内の要素に対して、次の要素を取得するための関数を通じてアクセスできます。これは、`next()`メソッドを使用して要素を1つずつ取得する仕組みです。

### イテレーターの目的
- **データの走査**: コレクション内の要素を順に処理するための簡単な方法を提供します。
- **抽象化**: コレクションの内部構造を隠蔽し、統一的なインターフェースを提供します。

### イテレーターの使用法
イテレーターは、主に以下の方法で使用されます。

1. **カスタムイテレーターの作成**: オブジェクトが自分自身のイテレーターを持つようにすることができます。
2. **標準イテレーターの利用**: 配列などの組み込みコレクションは、デフォルトでイテレーターをサポートしています。

### イテレーターのプロトコル
イテレーターは、以下のメソッドを持つ必要があります。
- `next()`: 次の要素を返すメソッドで、オブジェクトを返します。オブジェクトは`value`（要素の値）と`done`（イテレーションが完了したかどうかを示す真偽値）のプロパティを持ちます。

## 例
### 基本的な使用例
```javascript
// 配列のイテレーターを取得
const array = [1, 2, 3];
const iterator = array[Symbol.iterator]();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

### カスタムイテレーターの作成
```javascript
function CustomIterable() {
    this.values = [10, 20, 30];
}

CustomIterable.prototype[Symbol.iterator] = function() {
    let index = 0;
    const values = this.values;
    return {
        next: function() {
            return index < values.length ? 
                { value: values[index++], done: false } : 
                { value: undefined, done: true };
        }
    };
};

const customIterable = new CustomIterable();
for (const value of customIterable) {
    console.log(value); // 10, 20, 30
}
```

## 説明
### よくある落とし穴
- **`done`プロパティの理解**: `done`が`true`の場合、イテレーションは完了しており、次の呼び出しで`value`は`undefined`になります。
- **反復可能なオブジェクトとの混同**: イテレーターは反復可能なオブジェクト（Iterable）とは異なります。反復可能なオブジェクトは、イテレーターを返す`Symbol.iterator`メソッドを持っていますが、イテレーター自体はそのプロトタイプの一部ではありません。

## 一文要約
JavaScriptのイテレーターは、コレクションの要素を順に処理するための標準的な手法であり、データ構造の内部を隠蔽したインターフェースを提供します。