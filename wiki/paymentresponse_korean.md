<!--
Meta Description: # PaymentResponse: 자바스크립트에서의 결제 응답 처리 ## 개요 `PaymentResponse`는 JavaScript에서 결제 요청을 처리하기 위해 사용되는 객체로, 웹 결제 API의 일환으로 구현됩니다. 이 객체는 결제 세부정보를 포함하고 있으며, 결제...
Meta Keywords: paymentresponse, paymentrequest, 반환합니다, complete, console
-->

# PaymentResponse: 자바스크립트에서의 결제 응답 처리

## 개요
`PaymentResponse`는 JavaScript에서 결제 요청을 처리하기 위해 사용되는 객체로, 웹 결제 API의 일환으로 구현됩니다. 이 객체는 결제 세부정보를 포함하고 있으며, 결제 프로세스의 결과를 클라이언트 측에서 관리할 수 있도록 돕습니다.

## 문서화
`PaymentResponse` 객체는 결제 요청에 대한 응답을 나타내며, 결제 서비스에서 반환된 정보에 접근할 수 있는 방법을 제공합니다. 이 객체를 통해 개발자는 결제의 성공 여부, 결제 수단의 정보 및 사용자에게 제공된 추가적인 세부사항을 확인할 수 있습니다.

### 주요 속성 및 메서드
- **methodName**: 결제 방식의 이름을 반환합니다. 예를 들어, 'basic-card'와 같은 값이 들어올 수 있습니다.
- **details**: 결제 수단에 대한 세부 정보를 포함하는 객체입니다. 카드 번호와 같은 민감한 정보는 포함되지 않습니다.
- **shippingAddress**: 사용자가 결제 시 제공한 배송 주소를 반환합니다.
- **payerName**: 결제하는 사용자의 이름을 포함합니다.
- **complete()**: 결제가 성공적으로 처리된 후 호출하여 결제 프로세스를 완료합니다. 이 메서드는 Promise를 반환합니다.

## 예제
```javascript
// PaymentRequest 객체 생성
const paymentRequest = new PaymentRequest(['basic-card'], {
    total: {
        label: 'Total',
        amount: '10.00',
    },
});

// 결제 요청 표시 및 응답 처리
paymentRequest.show().then((paymentResponse) => {
    // 결제 응답 정보 출력
    console.log('결제 방식:', paymentResponse.methodName);
    console.log('결제 세부사항:', paymentResponse.details);
    
    // 결제 완료
    return paymentResponse.complete('success');
}).catch((error) => {
    console.error('결제 요청 중 오류 발생:', error);
});
```

## 설명
`PaymentResponse` 객체를 사용할 때 주의해야 할 점은 다음과 같습니다:
- **비동기 처리**: `paymentResponse.complete()` 메서드는 비동기적으로 처리되므로, 호출 후에 추가적인 작업을 수행하기 위해 Promise를 적절히 처리해야 합니다.
- **브라우저 호환성**: 모든 브라우저에서 결제 API를 지원하지 않으므로, 사용하기 전에 브라우저의 호환성을 확인해야 합니다.
- **보안**: 결제 정보를 처리할 때는 민감한 데이터가 노출되지 않도록 주의해야 하며, HTTPS 프로토콜을 사용하는 것이 필수입니다.

## 한 줄 요약
`PaymentResponse`는 JavaScript에서 결제 요청에 대한 응답을 처리하고 결제 세부정보에 접근할 수 있는 객체입니다.