<!--
Meta Description: # MediaList: JavaScriptにおけるメディアリストの完全ガイド ## 概要 MediaListは、CSSメディアクエリに関連するメディアタイプと条件のリストを操作するためのインターフェースです。JavaScriptを用いて、スタイルシートに適用されるメディア条件を動的に管理すること...
Meta Keywords: medialist, medialistは, const, stylesheet, length
-->

# MediaList: JavaScriptにおけるメディアリストの完全ガイド

## 概要
MediaListは、CSSメディアクエリに関連するメディアタイプと条件のリストを操作するためのインターフェースです。JavaScriptを用いて、スタイルシートに適用されるメディア条件を動的に管理することができます。

## ドキュメンテーション
### 目的
MediaListは、CSSのメディアクエリを操作するための便利なツールを提供します。主に、スタイルシートに関連するメディア条件を取得、追加、削除するために使用されます。

### 使用法
MediaListは、`document.styleSheets`のプロパティを通じてアクセスできます。各スタイルシートには、`media`プロパティがあり、これを参照することでMediaListにアクセスできます。

```javascript
const styleSheet = document.styleSheets[0]; // 最初のスタイルシートを取得
const mediaList = styleSheet.media; // MediaListを取得
```

### 詳細
MediaListオブジェクトには、次の重要なメソッドとプロパティがあります。

- **length**: 現在のメディア条件の数を返します。
- **item(index)**: 指定されたインデックスにあるメディア条件を返します。
- **appendMedium(medium)**: 新しいメディア条件をリストに追加します。
- **deleteMedium(medium)**: 指定されたメディア条件をリストから削除します。

## 例
以下はMediaListの基本的な使用例です。

```javascript
// スタイルシートの取得
const styleSheet = document.styleSheets[0];

// メディアリストの取得
const mediaList = styleSheet.media;

// メディア条件の数をログ出力
console.log(mediaList.length); // メディア条件の数を表示

// メディア条件を追加
mediaList.appendMedium('print');
console.log(mediaList.item(mediaList.length - 1)); // 新しく追加したメディア条件を表示

// メディア条件を削除
mediaList.deleteMedium('print');
console.log(mediaList.length); // メディア条件の数を表示
```

## 説明
MediaListを使用する際の一般的な注意点:

- **ブラウザの互換性**: MediaListはすべての主要なブラウザでサポートされていますが、古いバージョンのブラウザでは期待通りに動作しない可能性があります。
- **スタイルシートの順序**: 複数のスタイルシートがある場合、どのスタイルシートに対して操作を行っているのかを常に確認してください。
- **動的変更の影響**: メディア条件を動的に変更することで、ページのスタイルに即座に影響を与えるため、注意して使用する必要があります。

## 一文要約
MediaListは、CSSメディア条件を操作するためのJavaScriptのインターフェースで、スタイルシートの動的な管理を可能にします。