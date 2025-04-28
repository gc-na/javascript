<!--
Meta Description: # FileList: JavaScriptにおけるファイルリストの取り扱い ## 概要 JavaScriptの`FileList`は、ユーザーがファイル入力要素を通じて選択したファイルのリストを表すオブジェクトです。このオブジェクトは、Webアプリケーションでファイル操作を行う際に非常に重要な役割...
Meta Keywords: filelist, files, file, fileinput, const
-->

# FileList: JavaScriptにおけるファイルリストの取り扱い

## 概要
JavaScriptの`FileList`は、ユーザーがファイル入力要素を通じて選択したファイルのリストを表すオブジェクトです。このオブジェクトは、Webアプリケーションでファイル操作を行う際に非常に重要な役割を果たします。

## ドキュメント
### 目的
`FileList`オブジェクトは、HTMLの`<input type="file">`要素を使用して選択されたファイルの集合を保持します。ユーザーが複数のファイルを選択した場合でも、その全てのファイルにアクセスすることが可能です。

### 使用法
`FileList`は、特定のHTML要素から取得されます。以下は基本的な使用法です。

1. `<input type="file">`要素をHTMLに追加します。`multiple`属性を使用することで、複数のファイルを選択可能にします。
   ```html
   <input type="file" id="fileInput" multiple>
   ```

2. JavaScriptで、選択されたファイルにアクセスします。
   ```javascript
   const inputElement = document.getElementById('fileInput');

   inputElement.addEventListener('change', (event) => {
       const fileList = event.target.files; // FileListオブジェクトを取得
       console.log(fileList);
   });
   ```

### 詳細
`FileList`は、`File`オブジェクトの配列のように振る舞い、以下のようなプロパティとメソッドを持っています。

- **length**: `FileList`に含まれるファイルの数を返します。
- **item(index)**: 指定したインデックスのファイルを返します。

`File`オブジェクトは、各ファイルに関する情報（ファイル名、サイズ、タイプなど）を持っています。

## 例
### 基本的な使用例
```html
<input type="file" id="fileInput" multiple>
<script>
document.getElementById('fileInput').addEventListener('change', function(event) {
    const files = event.target.files;
    for (let i = 0; i < files.length; i++) {
        console.log(`ファイル名: ${files[i].name}, サイズ: ${files[i].size} bytes`);
    }
});
</script>
```

### 画像ファイルのプレビュー
```html
<input type="file" id="fileInput" multiple accept="image/*">
<div id="preview"></div>
<script>
document.getElementById('fileInput').addEventListener('change', function(event) {
    const files = event.target.files;
    const preview = document.getElementById('preview');
    preview.innerHTML = ''; // プレビューをクリア

    for (let i = 0; i < files.length; i++) {
        const img = document.createElement('img');
        img.src = URL.createObjectURL(files[i]);
        img.width = 100; // サムネイルサイズ
        preview.appendChild(img);
    }
});
</script>
```

## 説明
`FileList`を使用する際の一般的な落とし穴には、以下のようなものがあります。

- **空のリスト**: ユーザーがファイルを選択しない場合、`FileList`は空になります。そのため、ファイルの存在を確認するロジックが必要です。
- **ファイルのサイズ**: 大きなファイルを選択した場合、ブラウザのパフォーマンスに影響を及ぼすことがあります。ファイルサイズを確認し、適切に処理することが重要です。

## 一文要約
`FileList`は、HTMLのファイル入力要素を通じてユーザーが選択したファイルの集合を管理するJavaScriptオブジェクトです。