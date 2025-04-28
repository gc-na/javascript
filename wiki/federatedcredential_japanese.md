<!--
Meta Description: # FederatedCredential: JavaScriptにおける連合認証の利用 ## 概要 `FederatedCredential`は、Web認証APIの一部であり、ユーザーが外部の認証プロバイダーを通じてログインすることを容易にするためのインターフェースです。この機能は、シングルサイン...
Meta Keywords: federatedcredential, credentialmanager, get, credential, console
-->

# FederatedCredential: JavaScriptにおける連合認証の利用

## 概要
`FederatedCredential`は、Web認証APIの一部であり、ユーザーが外部の認証プロバイダーを通じてログインすることを容易にするためのインターフェースです。この機能は、シングルサインオン(SSO)を実現し、ユーザーの認証情報を安全に管理します。

## ドキュメンテーション
### 目的
`FederatedCredential`は、Webアプリケーションが外部の認証プロバイダー（例: Google、Facebookなど）の認証情報を利用できるようにするために設計されています。これにより、ユーザーは複数のアカウントを持たずに、簡単にサービスにアクセスできます。

### 使用法
`FederatedCredential`は、`CredentialManager`インターフェースの一部として使用されます。以下の手順で利用します。

1. `CredentialManager`インスタンスを作成します。
2. `get()`メソッドを使用して、ユーザーの認証情報を取得します。
3. 認証情報を使用して、アプリケーションへのアクセスを管理します。

### 詳細
- **プロパティ**:
  - `id`: ユーザーの識別子。
  - `name`: ユーザーの表示名。
  - `iconURL`: ユーザーのアイコンURL。

- **メソッド**:
  - `get()`: ユーザーの認証情報を取得するメソッド。

## 例
以下は、`FederatedCredential`を使用した基本的なコード例です。

```javascript
async function loginWithFederatedCredential() {
    const credentialManager = navigator.credentials;

    try {
        const credential = await credentialManager.get({
            federated: {
                providers: ['https://accounts.google.com'],
            },
        });

        if (credential) {
            console.log(`Logged in as: ${credential.name}`);
            // ここでアプリケーションのアクセスを管理します
        } else {
            console.log('認証が失敗しました。');
        }
    } catch (err) {
        console.error('エラー:', err);
    }
}
```

## 説明
- **一般的な落とし穴**:
  - `FederatedCredential`は、すべてのブラウザでサポートされているわけではありません。最新のブラウザでの動作確認が必要です。
  - ユーザーが選択したプロバイダーによっては、正しい認証情報が取得できない場合があります。
  
- **注意点**:
  - セキュリティ上の理由から、HTTPS接続が必要です。
  - ユーザーのプライバシーを尊重し、必要な範囲内でのみ情報を収集してください。

## 一文要約
`FederatedCredential`は、外部認証プロバイダーを通じてユーザーの認証情報を取得し、シングルサインオンを実現するためのJavaScriptインターフェースです。