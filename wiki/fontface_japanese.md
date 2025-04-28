<!--
Meta Description: # FontFace: JavaScriptでのフォント管理の新しい方法 ## 概要 `FontFace`は、Webフォントをプログラム的に定義し、ブラウザに読み込ませるためのインターフェースです。この機能を使用することで、開発者は動的にフォントを追加し、カスタムスタイルを適用することができます。 ...
Meta Keywords: fontface, error, document, font, fonts
-->

# FontFace: JavaScriptでのフォント管理の新しい方法

## 概要
`FontFace`は、Webフォントをプログラム的に定義し、ブラウザに読み込ませるためのインターフェースです。この機能を使用することで、開発者は動的にフォントを追加し、カスタムスタイルを適用することができます。

## ドキュメンテーション
### 目的
`FontFace`を使用することで、開発者はCSSに依存することなく、JavaScriptから直接フォントを操作できます。この機能は、特に動的なWebアプリケーションや、フォントのカスタマイズが多いプロジェクトで役立ちます。

### 使用法
`FontFace`を使用するためには、以下の手順に従います。

1. `FontFace`オブジェクトを作成します。
2. `load`メソッドを使用してフォントを読み込みます。
3. 読み込んだフォントを`document.fonts`に追加します。

#### 構文
```javascript
const font = new FontFace('FontName', 'url(font.woff2)');
font.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'FontName';
}).catch(function(error) {
    console.error('フォントの読み込みに失敗しました:', error);
});
```

## 例
### 基本的な使用例
以下は、`FontFace`を使用してカスタムフォントを読み込む基本的なコード例です。

```javascript
const myFont = new FontFace('MyFont', 'url(myfont.woff2)');

myFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'MyFont, sans-serif';
}).catch(function(error) {
    console.error('フォントの読み込みに失敗しました:', error);
});
```

### 複数フォントの読み込み
複数のフォントを同時に読み込むことも可能です。

```javascript
const fonts = [
    new FontFace('FontOne', 'url(font1.woff2)'),
    new FontFace('FontTwo', 'url(font2.woff2)')
];

Promise.all(fonts.map(font => font.load()))
    .then(loadedFonts => {
        loadedFonts.forEach(font => document.fonts.add(font));
        document.body.style.fontFamily = 'FontOne, FontTwo, sans-serif';
    })
    .catch(error => console.error('フォントの読み込みに失敗しました:', error));
```

## 説明
### 注意点
- `FontFace`は非同期的にフォントを読み込むため、読み込みが完了する前にフォントを使用しようとすると、デフォルトフォントが表示されることがあります。
- フォントのURLが正しいか、またはファイルが正しくサーバーにアップロードされているか確認してください。
- ブラウザの互換性に注意が必要です。一部の古いブラウザでは`FontFace`がサポートされていない場合があります。

### Gotchas
- フォントの読み込みに失敗した場合、`catch`ブロックを利用してエラーハンドリングを行うことが重要です。
- CORSポリシーにより、外部フォントを読み込む場合は、適切なCORS設定が必要になることがあります。

## 一文要約
`FontFace`は、JavaScriptを使用してWebフォントを動的に定義し、ブラウザに読み込ませるための強力なインターフェースです。