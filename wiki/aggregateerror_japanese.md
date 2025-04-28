<!--
Meta Description: # AggregateError: JavaScriptにおけるエラーの集約 ## 概要 `AggregateError`は、複数のエラーをひとつにまとめて扱うためのエラーオブジェクトです。主に、`Promise.any()`メソッドの失敗時に発生し、複数のPromiseの結果から生じたエラーを集約...
Meta Keywords: aggregateerror, error, promise, errors, any
-->

# AggregateError: JavaScriptにおけるエラーの集約

## 概要
`AggregateError`は、複数のエラーをひとつにまとめて扱うためのエラーオブジェクトです。主に、`Promise.any()`メソッドの失敗時に発生し、複数のPromiseの結果から生じたエラーを集約して提供します。

## ドキュメント
`AggregateError`は、複数のエラーを効率的に処理するための特別なエラークラスです。通常のエラーとは異なり、`AggregateError`は複数のエラーを配列として保持します。これにより、異常が発生した際に、どのエラーが発生したのかを一度に確認することができます。

### 使用法
```javascript
class AggregateError extends Error {
    constructor(errors, message) {
        super(message);
        this.errors = errors;
    }
}
```

- **parameters**
  - `errors`: 一つ以上のエラーオブジェクトを含む配列。
  - `message`: エラーの説明を含む文字列（オプション）。

### 目的
`AggregateError`は、特に非同期処理において、複数のPromiseのエラーを集約し、ユーザーに対して詳細な情報を提供することを目的としています。

## 例
### 基本的な使用例
```javascript
async function example() {
    const promises = [
        Promise.reject(new Error('エラー1')),
        Promise.reject(new Error('エラー2')),
        Promise.reject(new Error('エラー3'))
    ];

    try {
        await Promise.any(promises);
    } catch (err) {
        if (err instanceof AggregateError) {
            console.log(err.errors); // [ Error: エラー1, Error: エラー2, Error: エラー3 ]
        } else {
            console.error(err);
        }
    }
}

example();
```

このコードでは、3つのPromiseがすべて拒否されます。`Promise.any()`はすべてのPromiseが失敗した場合に`AggregateError`をスローし、各エラーを配列として提供します。

## 説明
### 一般的な落とし穴
- **エラー処理の不備**: `AggregateError`は複数のエラーを処理するために設計されていますが、すべてのエラーを確認せずに放置すると、問題の根本的な理解が不足します。
- **メッセージのカスタマイズ**: `AggregateError`のメッセージはオプションですが、具体的なエラーメッセージを設定することで、デバッグの際に役立ちます。

### 注意点
- `AggregateError`は、ECMAScript 2021以降の仕様で追加されたため、それ以前の環境では利用できません。
- `Promise.any()`を使用する際、すべてのPromiseが拒否された場合にのみ`AggregateError`が発生します。

## 一文要約
`AggregateError`は、複数のエラーを集約して処理し、詳細なエラーメッセージを提供するJavaScriptのエラーオブジェクトです。