<!--
Meta Description: # DOMPointReadOnly: JavaScriptにおける不変点オブジェクト ## 概要 `DOMPointReadOnly`は、Web APIの一部として提供される不変の2Dおよび3Dポイントを表すオブジェクトです。このオブジェクトは、主に2Dグラフィックスや3Dグラフィックスの操作にお...
Meta Keywords: dompointreadonly, point, dompoint, console, これは
-->

# DOMPointReadOnly: JavaScriptにおける不変点オブジェクト

## 概要
`DOMPointReadOnly`は、Web APIの一部として提供される不変の2Dおよび3Dポイントを表すオブジェクトです。このオブジェクトは、主に2Dグラフィックスや3Dグラフィックスの操作において、位置や方向を表現するために使用されます。

## ドキュメント
`DOMPointReadOnly`は、`DOMPoint`オブジェクトの不変バージョンであり、作成後にそのプロパティを変更することはできません。これは、特定のポイントを安全に保持し、意図しない変更を防ぐために役立ちます。

### 主な特性
- **不変性**: プロパティ（`x`, `y`, `z`, `w`）は読み取り専用で、オブジェクトが生成された後は変更できません。
- **構造**: `DOMPointReadOnly`は、次のようなプロパティを持ちます。
  - `x`: X座標
  - `y`: Y座標
  - `z`: Z座標（3Dの場合）
  - `w`: 透視投影用のウィンドウ座標（デフォルトは1）

### 使用法
`DOMPointReadOnly`は、`DOMPoint`インスタンスを生成することで得られます。以下のようにして使用します。

```javascript
let point = new DOMPoint(10, 20, 30, 1);
let readOnlyPoint = point.toJSON(); // DOMPointReadOnlyとして扱われる
```

## 例
以下は、`DOMPointReadOnly`の基本的な使用例です。

```javascript
// DOMPointの作成
const point = new DOMPoint(5, 10);

// DOMPointReadOnlyのプロパティの利用
console.log(point.x); // 5
console.log(point.y); // 10

// プロパティの変更を試みる
try {
    point.x = 15; // エラーが発生します
} catch (e) {
    console.error('プロパティは変更できません:', e);
}
```

## 説明
`DOMPointReadOnly`に関して注意すべき点は、オブジェクト自体が不変であるため、プロパティの再代入ができないことです。これは、アプリケーションの状態を予測可能に保つのに役立ちます。また、2Dおよび3Dでの正確なグラフィックス計算を行う際にも重要です。

### よくある落とし穴
- `DOMPointReadOnly`を理解する上での一般的な誤解は、オブジェクトの不変性を誤って解釈することです。プロパティを変更しようとするとエラーが発生しますので、作成されたインスタンスをそのまま使用することをお勧めします。
- `toJSON()`メソッドを使用することで、`DOMPoint`を`DOMPointReadOnly`に変換できますが、その際に元のオブジェクトは変更されません。

## 一文要約
`DOMPointReadOnly`は、JavaScriptにおける不変の2Dおよび3Dポイントを表現するオブジェクトであり、安全なグラフィックス計算をサポートします。