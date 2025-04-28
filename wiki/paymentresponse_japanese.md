<!--
Meta Description: # PaymentResponse: JavaScriptにおける決済応答の詳細 ## 概要 `PaymentResponse`は、Web Payment APIの一部であり、ウェブアプリケーションが支払い処理を行う際に、決済情報を受け取るためのオブジェクトです。このオブジェクトは、ユーザーが支払い...
Meta Keywords: paymentresponse, paymentrequest, basic, card, console
-->

# PaymentResponse: JavaScriptにおける決済応答の詳細

## 概要
`PaymentResponse`は、Web Payment APIの一部であり、ウェブアプリケーションが支払い処理を行う際に、決済情報を受け取るためのオブジェクトです。このオブジェクトは、ユーザーが支払いを行った後に、ブラウザから返される情報を格納します。

## ドキュメンテーション
`PaymentResponse`オブジェクトは、支払いの詳細を提供し、アプリケーションが支払い処理を続行するために必要な情報を含みます。このオブジェクトは、`PaymentRequest`インターフェースと共に使用され、リクエストが成功した場合に、決済情報が返されます。

### 主なプロパティ
- `methodName`: 支払い方式の名前（例: "basic-card", "paypal"）。
- `details`: 支払い方式に特有の詳細情報を含むオブジェクト。
- `shippingAddress`: ユーザーの配送先住所。
- `payerEmail`: 支払いを行ったユーザーのメールアドレス（オプション）。
- `billingAddress`: 請求先住所（オプション）。

### メソッド
- `complete(status)`: 支払い処理を完了します。`status`は、`'success'`、`'fail'`、または`'unknown'`のいずれかを指定します。

## 例
以下は、`PaymentResponse`を使用した基本的な例です。

```javascript
// PaymentRequestを作成
const paymentRequest = new PaymentRequest(["basic-card"], {
  total: { label: "合計", amount: "10.00" }
});

// 支払いを開始
paymentRequest.show().then(function(paymentResponse) {
  // 返されたPaymentResponseを利用
  console.log(paymentResponse.methodName); // "basic-card"
  console.log(paymentResponse.details); // 支払いの詳細情報

  // 支払い処理を完了
  paymentResponse.complete("success");
}).catch(function(err) {
  console.error("支払いエラー:", err);
});
```

## 説明
`PaymentResponse`を使用する際の一般的な落とし穴や注意点があります。以下にいくつか挙げます。

- **ブラウザの対応状況**: `PaymentResponse`はすべてのブラウザでサポートされているわけではありません。最新のブラウザのサポート状況を確認することが重要です。
- **セキュリティ**: ユーザーの支払い情報を扱うため、HTTPSでの通信が必須です。
- **エラーハンドリング**: `show()`メソッドは、ユーザーが支払いをキャンセルした場合や、他のエラーが発生した場合にPromiseを拒否します。適切にエラーハンドリングを行うことが重要です。

## 一文要約
`PaymentResponse`は、Web Payment APIを通じて支払い情報を受け取るためのJavaScriptオブジェクトであり、決済処理をサポートします。