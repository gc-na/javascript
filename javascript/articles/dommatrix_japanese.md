<!--
Meta Description: # DOMMatrix: JavaScriptにおける2Dおよび3D変換のためのクラス ## 概要 `DOMMatrix`は、Web APIの一部であり、2Dおよび3Dの行列変換を扱うためのクラスです。このクラスは、CSS変換やSVG変換を簡単に扱うための強力なツールを提供します。 ## ドキュメン...
Meta Keywords: matrix, dommatrix, let, new, javascript
-->

# DOMMatrix: JavaScriptにおける2Dおよび3D変換のためのクラス

## 概要
`DOMMatrix`は、Web APIの一部であり、2Dおよび3Dの行列変換を扱うためのクラスです。このクラスは、CSS変換やSVG変換を簡単に扱うための強力なツールを提供します。

## ドキュメンテーション
`DOMMatrix`は、変換行列を生成し、操作するためのインターフェースを提供します。これにより、2Dおよび3Dの変換を簡単に実行し、オブジェクトの位置、回転、拡大縮小を制御できます。

### 目的
- 2Dおよび3D変換行列の生成と操作を簡略化します。
- CSSとSVGで使用される変換を統一的に扱えます。

### 使用法
`DOMMatrix`のインスタンスは、次のように作成できます。

```javascript
let matrix = new DOMMatrix();
```

また、既存の行列をコピーすることも可能です。

```javascript
let existingMatrix = new DOMMatrix('matrix(1, 0, 0, 1, 0, 0)');
let matrixCopy = new DOMMatrix(existingMatrix);
```

### プロパティ
- **a**: X軸の拡大縮小。
- **b**: Y軸の傾き。
- **c**: X軸の傾き。
- **d**: Y軸の拡大縮小。
- **e**: X軸の移動。
- **f**: Y軸の移動。

### メソッド
- **invertSelf()**: 行列を逆行列に変換します。
- **multiply()**: 別の行列と掛け算をします。
- **rotateSelf()**: 行列を回転させます。
- **translateSelf()**: 行列を移動させます。

## 例
### 基本的な使用例

```javascript
// 新しいDOMMatrixを作成
let matrix = new DOMMatrix();

// 行列に変換を適用
matrix.translateSelf(50, 100);
matrix.rotateSelf(45);

// 行列のプロパティをログに出力
console.log(matrix.a, matrix.b, matrix.c, matrix.d, matrix.e, matrix.f);
```

### 既存の行列の操作

```javascript
let initialMatrix = new DOMMatrix('matrix(1, 0, 0, 1, 0, 0)');
let transformedMatrix = initialMatrix.translate(20, 30);
console.log(transformedMatrix);
```

## 説明
`DOMMatrix`を使用する際の一般的な注意点として、行列のプロパティが変更されると、元の行列が変わることに留意してください。また、行列の計算は数学的に複雑であり、特に複数の変換を連続して適用する場合は、順序に注意が必要です。

## 一文要約
`DOMMatrix`は、JavaScriptで2Dおよび3Dの変換行列を簡単に生成し操作するためのクラスです。