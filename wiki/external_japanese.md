<!--
Meta Description: # JavaScriptにおける「external」の完全ガイド ## 概要 JavaScriptの「external」は、Webブラウザが外部リソース、特に外部JavaScriptファイルを参照する際に使用されます。この機能を利用することで、コードの再利用性が高まり、ページの読み込み速度を向上させ...
Meta Keywords: script, src, html, body, external
-->

# JavaScriptにおける「external」の完全ガイド

## 概要
JavaScriptの「external」は、Webブラウザが外部リソース、特に外部JavaScriptファイルを参照する際に使用されます。この機能を利用することで、コードの再利用性が高まり、ページの読み込み速度を向上させることができます。

## ドキュメンテーション
### 目的
「external」は、JavaScriptのコードをHTMLファイルから分離するための手法です。これにより、複数のHTMLファイルで同じJavaScriptコードを共有することができ、メンテナンスが容易になります。

### 使用法
外部JavaScriptファイルをHTMLに組み込むには、`<script>`タグを使用し、`src`属性を指定します。この`src`属性は、外部ファイルのURLを指します。

```html
<script src="path/to/your/script.js"></script>
```

### 詳細
- **ファイルの場所**: `src`には絶対パスまたは相対パスを指定できます。
- **読み込みのタイミング**: `<script>`タグの位置によって、JavaScriptの実行タイミングが変わります。通常、`<body>`タグの終了前に配置することが推奨されます。
- **非同期読み込み**: `async`属性を追加することで、スクリプトを非同期に読み込むことができ、ページのパフォーマンスを向上させることが可能です。

```html
<script src="path/to/your/script.js" async></script>
```

## 例
### 基本的な使用例
1. 外部JavaScriptファイルを通常の方法で読み込む:
   ```html
   <html>
   <head>
       <script src="script.js"></script>
   </head>
   <body>
       <h1>Hello World</h1>
   </body>
   </html>
   ```

2. 非同期で外部JavaScriptファイルを読み込む:
   ```html
   <html>
   <head>
       <script src="script.js" async></script>
   </head>
   <body>
       <h1>Hello World</h1>
   </body>
   </html>
   ```

## 説明
### 一般的な落とし穴
- **パスの指定ミス**: `src`に指定したパスが正しくないと、スクリプトが読み込まれず、機能しないことがあります。
- **依存関係**: 複数の外部スクリプトがある場合、依存関係に注意が必要です。例えば、jQueryを使用するスクリプトは、jQueryが先に読み込まれている必要があります。
- **キャッシュ**: ブラウザが外部ファイルをキャッシュするため、変更を即座に反映させるには、ファイル名にバージョン番号を付けることが推奨されます。

## 一文要約
JavaScriptの「external」は、Webページで外部JavaScriptファイルを読み込むための手法であり、コードの再利用性とページのパフォーマンス向上に寄与します。