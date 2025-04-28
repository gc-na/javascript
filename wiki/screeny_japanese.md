<!--
Meta Description: # JavaScriptにおけるscreenYプロパティの完全ガイド ## 概要 `screenY`プロパティは、ブラウザウィンドウのスクリーン上でのマウスポインタのY座標を取得するために使用されます。このプロパティは、ユーザーのデバイスにおけるマウスの位置を絶対的な値として提供します。 ## ドキ...
Meta Keywords: screeny, event, mousemove, javascript, addeventlistener
-->

# JavaScriptにおけるscreenYプロパティの完全ガイド

## 概要
`screenY`プロパティは、ブラウザウィンドウのスクリーン上でのマウスポインタのY座標を取得するために使用されます。このプロパティは、ユーザーのデバイスにおけるマウスの位置を絶対的な値として提供します。

## ドキュメント
### 目的
`screenY`は、マウスポインタが画面上でどこにあるかを知るための便利な方法です。このプロパティは、イベントオブジェクト内に含まれており、特にマウスイベント（`mousedown`, `mouseup`, `mousemove`など）で利用されます。

### 使用法
`screenY`は、以下の方法で使用できます：

```javascript
element.addEventListener('mousemove', function(event) {
    console.log(event.screenY);
});
```

このコードは、`mousemove`イベントが発生したときにマウスポインタのY座標をコンソールに表示します。

### 詳細
- **型:** `number`
- **返り値:** スクリーンのトップからマウスポインタまでのピクセル数
- **互換性:** すべての主要なブラウザでサポートされています。

## 例
以下は、`screenY`の基本的な使用例です。

### 例1: マウスのY座標を表示
```javascript
document.addEventListener('mousemove', function(event) {
    console.log('マウスのY座標: ' + event.screenY);
});
```

### 例2: Y座標に基づいて要素の位置を変更
```javascript
const box = document.getElementById('box');

document.addEventListener('mousemove', function(event) {
    box.style.top = event.screenY + 'px';
});
```

## 説明
- **共通の落とし穴:**
  - `screenY`は、ブラウザウィンドウのスクリーン上の位置を表すため、ウィンドウがスクリーンの異なる位置に移動した場合、値が変わることがあります。
  - スクロールした場合、`screenY`は変わらず、`clientY`を使用することで、ビューポート内の相対的な位置を得ることができます。

- **追加の注意点:**
  - `screenY`は、ユーザーのデバイスの物理的な画面座標に基づいているため、異なるデバイスで異なる値を持つ可能性があります。
  - タッチデバイスでは、マウスイベントは発生しないため、タッチイベントを使用する必要があります。

## 一文要約
`screenY`プロパティは、マウスポインタのY座標をスクリーン上で取得するためのJavaScriptの機能です。