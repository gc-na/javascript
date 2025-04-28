<!--
Meta Description: # JavaScriptにおける「Number」の完全ガイド ## 概要 JavaScriptの「Number」は、数値データを扱うための基本的なデータ型です。この型は整数や浮動小数点数を含み、数値演算や数値の変換、比較などの操作をサポートします。 ## ドキュメンテーション ### 目的 「Num...
Meta Keywords: number, let, nan, console, log
-->

# JavaScriptにおける「Number」の完全ガイド

## 概要
JavaScriptの「Number」は、数値データを扱うための基本的なデータ型です。この型は整数や浮動小数点数を含み、数値演算や数値の変換、比較などの操作をサポートします。

## ドキュメンテーション
### 目的
「Number」型は、数値の計算やデータの処理を行うために不可欠です。JavaScriptでは、数値は「Number」オブジェクトに包まれていますが、基本的にはプリミティブなデータ型として扱われます。

### 使用法
JavaScriptで「Number」を使用する際は、数値を直接リテラルとして記述するか、`Number()` コンストラクタを利用して他の型から数値に変換します。

```javascript
// 数値リテラル
let a = 42;         // 整数
let b = 3.14;      // 浮動小数点数

// Numberコンストラクタを使用
let c = Number("123"); // 文字列から数値に変換
```

### 詳細
- **数値の演算**: 加算、減算、乗算、除算などの基本的な演算が可能です。
- **特殊値**: `Infinity`（無限大）、`-Infinity`（負の無限大）、`NaN`（数値ではない）などの特別な値も存在します。
- **型変換**: 他のデータ型（文字列、真偽値など）を数値に変換する際に、`Number()`メソッドや`parseInt()`、`parseFloat()`などの関数が利用できます。

## 例
以下は、JavaScriptにおける「Number」の基本的な使用例です。

```javascript
// 基本的な算術演算
let x = 10;
let y = 2;
console.log(x + y); // 12
console.log(x - y); // 8
console.log(x * y); // 20
console.log(x / y); // 5

// 数値の変換
let strNum = "456";
let num = Number(strNum);
console.log(num); // 456

// NaNの扱い
let invalidNum = Number("abc");
console.log(invalidNum); // NaN
```

## 説明
「Number」を使用する際の一般的な注意点や落とし穴には以下があります。

- **浮動小数点の精度**: JavaScriptの数値は64ビットの浮動小数点形式で表現されるため、一部の数値計算で誤差が生じることがあります。例えば、`0.1 + 0.2`は`0.30000000000000004`となります。
- **NaNの特性**: `NaN`は自己と等しくないため、`NaN === NaN`は`false`になります。`NaN`が生成された場合は、`isNaN()`関数を使ってチェックする必要があります。
- **型の自動変換**: JavaScriptは弱い型付けの言語であるため、数値と文字列を混ぜて計算する際に自動的に型変換が行われることがあります。これにより予期しない結果が生じることがあります。

## 一文要約
JavaScriptの「Number」は、数値データを扱うための基本的なデータ型で、演算や型変換を通じて強力な数値処理を提供します。