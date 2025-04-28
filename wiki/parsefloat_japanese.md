<!--
Meta Description: # JavaScriptのparseFloat関数：数値文字列を浮動小数点数に変換する方法 ## 概要 `parseFloat`は、JavaScriptにおける組み込み関数で、文字列を浮動小数点数に変換します。この関数は数値として解釈できる部分を文字列から抽出し、対応する数値を返します。 ## ドキ...
Meta Keywords: parsefloat, console, log, nan, javascript
-->

# JavaScriptのparseFloat関数：数値文字列を浮動小数点数に変換する方法

## 概要
`parseFloat`は、JavaScriptにおける組み込み関数で、文字列を浮動小数点数に変換します。この関数は数値として解釈できる部分を文字列から抽出し、対応する数値を返します。

## ドキュメント
### 目的
`parseFloat`は、与えられた文字列の最初の数値部分を解析し、浮動小数点数として返すために使用されます。数値以外の文字が最初に現れると、その時点での解析を終了します。

### 使用法
```javascript
parseFloat(string)
```

### パラメーター
- `string`（必須）：解析したい文字列。数値として解釈できる部分が含まれている必要があります。

### 戻り値
- 文字列から解析された浮動小数点数。数値として解釈できない場合は`NaN`（Not-a-Number）を返します。

### 注意事項
- `parseFloat`は、数値の前に空白がある場合でも正しく動作します。
- 解析できる文字列がない場合や、最初の文字が数値でない場合は、`NaN`が返されます。

## 例
### 基本の使用例
```javascript
console.log(parseFloat("3.14")); // 出力: 3.14
console.log(parseFloat("   42.5abc")); // 出力: 42.5
console.log(parseFloat("abc42.5")); // 出力: NaN
console.log(parseFloat("100")); // 出力: 100
console.log(parseFloat("0.001")); // 出力: 0.001
```

## 説明
`parseFloat`を使用する際の一般的な注意点は以下の通りです。

- **数値以外の文字**: 解析は数値の最初の部分で終了します。たとえば、`parseFloat("123abc")`は`123`を返しますが、`parseFloat("abc123")`は`NaN`を返します。
- **空白の扱い**: 文字列の先頭に空白がある場合でも、`parseFloat`は正しく数値を解析します。
- **小数点の形式**: 文化によっては小数点の表現が異なる場合がありますが、`parseFloat`は標準的なドット形式（`.`）を使用するため、他の形式（例: カンマ（`,`））は正しく解析されません。

## 一文の要約
`parseFloat`は、文字列を解析して浮動小数点数に変換するJavaScriptの組み込み関数です。