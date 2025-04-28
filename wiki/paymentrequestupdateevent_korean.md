<!--
Meta Description: # PaymentRequestUpdateEvent: 자바스크립트에서의 결제 요청 업데이트 이벤트 ## 개요 `PaymentRequestUpdateEvent`는 웹 결제 API의 일부로, 결제 요청이 업데이트될 때 발생하는 이벤트입니다. 이 이벤트는 사용자가 결제 정보를...
Meta Keywords: paymentrequest, paymentrequestupdateevent, const, 이벤트, 요청이
-->

# PaymentRequestUpdateEvent: 자바스크립트에서의 결제 요청 업데이트 이벤트

## 개요
`PaymentRequestUpdateEvent`는 웹 결제 API의 일부로, 결제 요청이 업데이트될 때 발생하는 이벤트입니다. 이 이벤트는 사용자가 결제 정보를 수정할 수 있도록 하며, 웹 애플리케이션이 결제 요청에 대한 변경 사항을 반영할 수 있게 해줍니다.

## 문서화
`PaymentRequestUpdateEvent`는 결제 요청이 업데이트될 때 발생하는 이벤트로, 개발자가 결제 요청의 세부정보를 업데이트하는 데 필요한 메소드를 호출할 수 있게 해줍니다. 이 이벤트는 주로 다음과 같은 목적을 가지고 사용됩니다:

- **결제 정보 업데이트**: 사용자가 결제 정보를 변경할 때, 예를 들어 배송 주소를 수정하는 경우, 이 이벤트를 통해 결제 요청을 업데이트할 수 있습니다.
- **상태 관리**: 결제 요청의 상태를 관리하고, 사용자에게 최신 정보를 제공하는 데 유용합니다.

### 사용법
`PaymentRequestUpdateEvent`는 `PaymentRequest` 인스턴스를 통해 발생합니다. 이벤트 리스너에서 이 이벤트를 수신하고, 결제 요청을 업데이트하기 위해 `updateWith()` 메소드를 호출합니다.

```javascript
const paymentRequest = new PaymentRequest(methodData, details);

paymentRequest.addEventListener('update', (event) => {
    // 결제 요청 업데이트 처리
    const updatedDetails = {...}; // 업데이트된 결제 세부정보
    event.updateWith(updatedDetails);
});
```

## 예제
다음은 `PaymentRequestUpdateEvent`를 사용하는 간단한 예제입니다.

```javascript
const methodData = [{
    supportedMethods: 'basic-card',
    data: {
        supportedNetworks: ['visa', 'mastercard']
    }
}];

const details = {
    total: {
        label: '총액',
        amount: '10.00'
    }
};

const paymentRequest = new PaymentRequest(methodData, details);

paymentRequest.addEventListener('update', (event) => {
    const updatedDetails = {
        total: {
            label: '총액',
            amount: '15.00' // 변경된 금액
        }
    };
    event.updateWith(updatedDetails);
});

// 결제 요청을 표시
paymentRequest.show().then((paymentResponse) => {
    // 결제 처리 코드
}).catch((err) => {
    console.log(err);
});
```

## 설명
`PaymentRequestUpdateEvent`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **이벤트 리스너**: `update` 이벤트 리스너는 결제 요청이 표시된 후 사용자 상호작용에 따라 호출됩니다. 따라서 결제 요청이 항상 업데이트되어야 하는 것은 아닙니다.
- **비동기 처리**: `updateWith()` 메소드는 비동기적으로 작동하므로, 업데이트가 완료될 때까지 기다려야 할 수 있습니다.
- **세부정보 유효성**: 업데이트하는 세부정보는 유효해야 하며, 그렇지 않을 경우 오류가 발생할 수 있습니다.

## 한 줄 요약
`PaymentRequestUpdateEvent`는 웹 결제 API에서 결제 요청의 업데이트를 처리하기 위한 이벤트로, 사용자의 결제 정보 변경을 지원합니다.