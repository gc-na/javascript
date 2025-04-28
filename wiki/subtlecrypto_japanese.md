<!--
Meta Description: # SubtleCrypto：JavaScriptにおける暗号化APIの使い方 ## 概要 SubtleCryptoは、Web Cryptography APIの一部であり、JavaScriptを使用して安全な暗号化、署名、ハッシュ計算を行うためのインターフェースです。このAPIは、ブラウザ環境での...
Meta Keywords: const, crypto, subtlecryptoは, subtle, encrypt
-->

# SubtleCrypto：JavaScriptにおける暗号化APIの使い方

## 概要
SubtleCryptoは、Web Cryptography APIの一部であり、JavaScriptを使用して安全な暗号化、署名、ハッシュ計算を行うためのインターフェースです。このAPIは、ブラウザ環境でのデータ保護を提供し、セキュリティの強化に役立ちます。

## ドキュメント
SubtleCryptoは、以下の主な機能を提供します：

1. **暗号化と復号化**：データを安全に暗号化し、必要に応じて復号化することができます。
2. **署名と検証**：データの整合性を保つためにデジタル署名を作成し、検証することができます。
3. **ハッシュ計算**：データのハッシュ値を計算することで、データの一貫性や整合性を確認することができます。

### 使用方法
SubtleCryptoは、`window.crypto.subtle`オブジェクトを通じてアクセスできます。以下のメソッドを使用して操作を実行します：

- `encrypt()`
- `decrypt()`
- `sign()`
- `verify()`
- `digest()`
- `generateKey()`
- `importKey()`
- `exportKey()`

### 詳細
SubtleCryptoは、PromiseベースのAPIであり、非同期操作を行います。これにより、UIスレッドがブロックされることなく、暗号化処理を実行できます。すべてのメソッドは、必要なパラメータを受け取り、成功時には結果を返します。

## 例
以下は、SubtleCryptoを使ってテキストをSHA-256でハッシュ化する基本的な例です：

```javascript
const text = "Hello, World!";
const encoder = new TextEncoder();
const data = encoder.encode(text);

crypto.subtle.digest("SHA-256", data).then(hash => {
    console.log(new Uint8Array(hash));
});
```

暗号化と復号化の例：

```javascript
const key = await crypto.subtle.generateKey(
    {
        name: "AES-GCM",
        length: 256,
    },
    true,
    ["encrypt", "decrypt"]
);

const iv = crypto.getRandomValues(new Uint8Array(12));
const ciphertext = await crypto.subtle.encrypt(
    {
        name: "AES-GCM",
        iv: iv,
    },
    key,
    data
);

const decrypted = await crypto.subtle.decrypt(
    {
        name: "AES-GCM",
        iv: iv,
    },
    key,
    ciphertext
);
```

## 説明
### 一般的な落とし穴
- **非同期処理の理解**：SubtleCryptoのメソッドはすべてPromiseを返すため、正しいエラーハンドリングを行うことが重要です。
- **鍵の管理**：生成した鍵を適切に管理し、必要に応じてインポート・エクスポートする必要があります。

### 注意点
- ブラウザの互換性を確認することが重要です。SubtleCryptoは比較的新しいAPIであるため、古いブラウザではサポートされていない可能性があります。
- 一部のアルゴリズムは、特定の用途に対して適していない場合があります。使用する前に、目的に合ったアルゴリズムを選択してください。

## 一文要約
SubtleCryptoは、JavaScriptにおける安全な暗号化、署名、ハッシュ計算を実現するための強力なAPIです。