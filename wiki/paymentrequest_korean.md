<!--
Meta Description: # PaymentRequest: JavaScript로 결제 요청 처리하기 ## 개요 `PaymentRequest`는 웹 애플리케이션에서 결제 과정을 간소화하기 위해 제공되는 JavaScript API입니다. 사용자에게 결제 정보를 입력할 수 있는 UI를 제공하여, 다양...
Meta Keywords: paymentrequest, total, paymentresponse, error, javascript
-->

# PaymentRequest: JavaScript로 결제 요청 처리하기

## 개요
`PaymentRequest`는 웹 애플리케이션에서 결제 과정을 간소화하기 위해 제공되는 JavaScript API입니다. 사용자에게 결제 정보를 입력할 수 있는 UI를 제공하여, 다양한 결제 수단을 지원하고 결제 경험을 개선합니다.

## 문서화
### 목적
`PaymentRequest` API는 웹사이트 또는 웹 애플리케이션이 사용자로부터 결제 정보를 쉽게 요청하고 처리할 수 있도록 설계되었습니다. 이 API는 사용자에게 결제 과정에서의 편의성을 제공하며, 다양한 결제 수단을 통합할 수 있습니다.

### 사용법
`PaymentRequest` 객체를 생성하려면 결제 관련 정보를 포함하는 매개변수를 전달해야 합니다. 주된 매개변수는 `paymentMethods`, `details`, `options`입니다.

```javascript
const paymentRequest = new PaymentRequest(
    ['basic-card'], // 결제 수단
    {
        total: { label: 'Total', amount: 10.00 }, // 결제 총액
        displayItems: [
            { label: 'Item 1', amount: 5.00 },
            { label: 'Item 2', amount: 5.00 }
        ]
    },
    { requestPayerName: true, requestPayerEmail: true } // 추가 정보 요청
);
```

결제 요청을 보내려면 `show()` 메서드를 호출합니다. 이 메서드는 사용자의 결제 정보를 반환하는 Promise를 반환합니다.

```javascript
paymentRequest.show()
    .then(function(paymentResponse) {
        // 결제 성공 처리
        console.log(paymentResponse);
        paymentResponse.complete('success'); // 결제가 완료됨을 알림
    })
    .catch(function(error) {
        console.error('결제 오류:', error);
    });
```

## 예제
### 기본 사용법 예제
```javascript
const paymentRequest = new PaymentRequest(
    ['basic-card'],
    {
        total: { label: 'Total', amount: 20.00 }
    }
);

paymentRequest.show()
    .then(function(paymentResponse) {
        console.log('결제 정보:', paymentResponse);
        paymentResponse.complete('success');
    })
    .catch(function(error) {
        console.error('결제 오류:', error);
    });
```

### 여러 결제 수단 예제
```javascript
const paymentRequest = new PaymentRequest(
    [
        { supportedMethods: 'basic-card' },
        { supportedMethods: 'https://example.com/pay' }
    ],
    {
        total: { label: 'Total', amount: 50.00 }
    }
);
```

## 설명
### 일반적인 실수 및 주의사항
- **HTTPS 요구 사항**: `PaymentRequest` API는 보안된 환경(HTTPS)에서만 작동합니다. 로컬 파일이나 HTTP 환경에서는 사용할 수 없습니다.
- **결제 수단 제한**: 모든 브라우저가 모든 결제 수단을 지원하는 것은 아닙니다. 사용하려는 결제 수단이 지원되는지 확인해야 합니다.
- **Promise 처리**: 결제 요청이 취소되거나 오류가 발생할 수 있으므로, 항상 `catch` 블록을 사용하여 오류를 처리해야 합니다.
- **결제 완료 처리**: 결제가 성공적으로 이루어진 후에는 반드시 `complete()` 메서드를 호출하여 결제가 완료되었음을 알려야 합니다.

## 한 줄 요약
`PaymentRequest`는 JavaScript를 사용하여 웹 애플리케이션에서 결제 요청을 간편하게 처리할 수 있는 API입니다.