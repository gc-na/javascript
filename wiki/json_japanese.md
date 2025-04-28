<!--
Meta Description: # JavaScriptにおけるJSON（JavaScript Object Notation）の完全ガイド ## 概要 JSON（JavaScript Object Notation）は、軽量で人間にも読みやすいデータ交換フォーマットです。JavaScriptオブジェクトの表現に基づいており、デー...
Meta Keywords: json, const, name, age, javascript
-->

# JavaScriptにおけるJSON（JavaScript Object Notation）の完全ガイド

## 概要
JSON（JavaScript Object Notation）は、軽量で人間にも読みやすいデータ交換フォーマットです。JavaScriptオブジェクトの表現に基づいており、データの保存や送信に広く利用されています。

## ドキュメンテーション
### 目的
JSONは、データ構造を簡潔に表現するためのフォーマットであり、特にウェブアプリケーションにおいてサーバーとクライアント間でデータをやり取りする際に使用されます。

### 使用法
JSONは、以下のように構造化されたデータを持つことができます：
- オブジェクト `{}`（キーと値のペア）
- 配列 `[]`（値のリスト）

### 詳細
JavaScriptでは、JSONデータを扱うために主に次の2つのメソッドが提供されています。
- `JSON.stringify()`: JavaScriptのオブジェクトをJSON文字列に変換します。
- `JSON.parse()`: JSON文字列をJavaScriptのオブジェクトに変換します。

```javascript
const obj = { name: "太郎", age: 30 };

// オブジェクトをJSON文字列に変換
const jsonString = JSON.stringify(obj); // '{"name":"太郎","age":30}'

// JSON文字列をオブジェクトに変換
const parsedObj = JSON.parse(jsonString); // { name: "太郎", age: 30 }
```

## 例
以下は、JSONを使用する基本的な例です。

### JSONオブジェクトの作成と変換
```javascript
const user = {
    name: "花子",
    age: 25,
    hobbies: ["読書", "映画鑑賞"]
};

// オブジェクトをJSONに変換
const userJson = JSON.stringify(user);
console.log(userJson); // {"name":"花子","age":25,"hobbies":["読書","映画鑑賞"]}

// JSONをオブジェクトに変換
const userObj = JSON.parse(userJson);
console.log(userObj.name); // 花子
```

## 説明
### 一般的な落とし穴
- **文字列のエスケープ**: JSON文字列内での特定の文字（例：ダブルクォートやバックスラッシュ）はエスケープする必要があります。そうしないと、パースエラーが発生します。
  
- **日付の扱い**: JavaScriptのDateオブジェクトはJSONには直接変換できません。日付は通常、ISO 8601形式の文字列として保存する必要があります。

- **undefinedや関数**: JSONは、`undefined`や関数を扱えません。これらの値はJSONに含めることができず、変換時に無視されます。

### 注意点
- JSONはUTF-8エンコーディングを推奨します。
- JSONデータは、HTTP通信でよく使用されるフォーマットであり、APIとのやり取りでも広く使われています。

## 一文要約
JSONは、JavaScriptオブジェクトを軽量なデータ交換フォーマットに変換するための標準形式です。