<!--
Meta Description: # PaymentAddress: 자바스크립트에서의 결제 주소 처리 ## 개요 `PaymentAddress`는 자바스크립트에서 결제 API와 함께 사용되는 객체로, 결제 정보를 담고 있는 주소를 표현합니다. 이 객체는 웹 애플리케이션에서 결제 프로세스를 개선하고 사용자 ...
Meta Keywords: paymentaddress, 정보를, 객체는, paymentrequest, 사용됩니다
-->

# PaymentAddress: 자바스크립트에서의 결제 주소 처리

## 개요
`PaymentAddress`는 자바스크립트에서 결제 API와 함께 사용되는 객체로, 결제 정보를 담고 있는 주소를 표현합니다. 이 객체는 웹 애플리케이션에서 결제 프로세스를 개선하고 사용자 경험을 향상시키기 위해 설계되었습니다.

## 문서화
`PaymentAddress` 객체는 결제 관련 주소 정보를 표시하는 데 사용됩니다. 이 객체는 사용자의 배송지 또는 청구지 주소를 포함하여 결제 프로세스에서 필요한 여러 속성을 제공합니다. 

### 목적
- 결제 시스템에서 주소 정보를 표준화하여 관리할 수 있도록 돕습니다.
- 사용자에게 자동 완성된 주소 입력 기능을 제공하여 편리함을 증가시킵니다.

### 사용법
`PaymentAddress` 객체는 `PaymentRequest` API의 일부로 사용됩니다. 다음은 주요 속성입니다:

- `recipient`: 수신자 이름(예: "홍길동")
- `addressLine`: 주소의 첫 번째 줄(예: "서울시 강남구")
- `city`: 도시(예: "서울")
- `country`: 국가 코드(예: "KR")
- `postalCode`: 우편번호(예: "06100")
- `region`: 주 또는 지역(예: "서울특별시")

이 객체는 `PaymentRequest`를 생성할 때 결제 주소 정보를 넘겨주는 데 사용됩니다.

## 예제
다음은 `PaymentAddress` 객체의 기본 사용 예입니다.

```javascript
const paymentAddress = new PaymentAddress({
    recipient: '홍길동',
    addressLine: ['서울시 강남구'],
    city: '서울',
    country: 'KR',
    postalCode: '06100',
    region: '서울특별시'
});

// PaymentRequest 생성
const paymentRequest = new PaymentRequest(
    ['basic-card'],
    {
        total: { label: '총액', amount: '10000' },
        displayItems: [],
        shippingOptions: []
    },
    {
        requestShipping: true,
        shippingAddress: paymentAddress
    }
);
```

## 설명
`PaymentAddress` 객체를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **필수 속성**: 모든 속성이 필수는 아니지만, 결제 프로세스에 필요한 최소한의 정보를 제공해야 합니다.
- **브라우저 호환성**: `PaymentRequest` API와 `PaymentAddress` 객체는 모든 브라우저에서 지원되지 않을 수 있으므로, 호환성을 확인해야 합니다.
- **사용자 경험**: 주소 입력 시 자동 완성 기능이 제공되므로, 사용자의 편리함을 고려하여 적절한 속성을 설정하는 것이 중요합니다.

## 한 줄 요약
`PaymentAddress`는 자바스크립트에서 결제 API를 통해 주소 정보를 처리하는 객체입니다.