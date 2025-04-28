<!--
Meta Description: # FileSystemDirectoryHandle: JavaScriptにおけるファイルシステムディレクトリハンドルの完全ガイド ## 概要 `FileSystemDirectoryHandle`は、Web APIの一部であり、ユーザーのファイルシステム内のディレクトリを操作するためのインター...
Meta Keywords: filesystemdirectoryhandle, options, await, name, showdirectorypicker
-->

# FileSystemDirectoryHandle: JavaScriptにおけるファイルシステムディレクトリハンドルの完全ガイド

## 概要
`FileSystemDirectoryHandle`は、Web APIの一部であり、ユーザーのファイルシステム内のディレクトリを操作するためのインターフェースです。この機能は、Webアプリケーションがユーザーのファイルシステムと安全に対話できるようにすることを目的としています。

## ドキュメンテーション
### 概要
`FileSystemDirectoryHandle`は、ユーザーが選択したディレクトリを表すオブジェクトで、ディレクトリ内のファイルやサブディレクトリへのアクセスを提供します。このインターフェースは、主に`showDirectoryPicker()`メソッドを使用して取得されます。

### 使用方法
1. **ディレクトリの選択**: ユーザーにディレクトリを選択させるために、`window.showDirectoryPicker()`メソッドを使用します。このメソッドは、Promiseを返し、成功した場合は選択されたディレクトリの`FileSystemDirectoryHandle`を返します。

2. **ファイルやサブディレクトリの操作**: `FileSystemDirectoryHandle`を使用して、ディレクトリ内のファイルを取得したり、新しいファイルやディレクトリを作成したり、削除したりすることができます。

### 詳細
- **メソッド**:
  - `getFileHandle(name, options)`: 指定された名前のファイルハンドルを取得します。
  - `getDirectoryHandle(name, options)`: 指定された名前のサブディレクトリハンドルを取得します。
  - `removeEntry(name, options)`: 指定された名前のファイルまたはディレクトリを削除します。
  - `queryPermission(options)`: このディレクトリハンドルに対するアクセス権限の状態を確認します。

- **オプション**: いくつかのメソッドは、オプションを受け入れます。例えば、`options`には、ファイルを取得する際に存在しない場合の動作を指定することができます。

## 例
```javascript
async function selectDirectory() {
    try {
        const directoryHandle = await window.showDirectoryPicker();
        console.log(`選択されたディレクトリ: ${directoryHandle.name}`);

        const fileHandle = await directoryHandle.getFileHandle('example.txt', { create: true });
        const writable = await fileHandle.createWritable();
        await writable.write('Hello, File System!');
        await writable.close();
    } catch (error) {
        console.error('エラー:', error);
    }
}

selectDirectory();
```

## 説明
`FileSystemDirectoryHandle`を使用する際の一般的な落とし穴には以下のようなものがあります：
- **ブラウザのサポート**: このAPIは、すべてのブラウザでサポートされているわけではないため、使用前に互換性を確認する必要があります。
- **セキュリティモデル**: ユーザーから明示的な許可を得る必要があり、許可がない場合はディレクトリにアクセスできません。
- **非同期処理**: これらのメソッドはPromiseを返すため、適切に非同期処理を行わないとエラーが発生する可能性があります。

## 一文の要約
`FileSystemDirectoryHandle`は、Webアプリケーションがユーザーのファイルシステム内のディレクトリを安全に操作するためのインターフェースです。