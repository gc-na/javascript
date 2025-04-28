<!--
Meta Description: # 자바스크립트에서 "opener"의 이해와 활용 ## 개요 `opener`는 자바스크립트에서 현재 창을 연 상위 창을 참조하는 속성입니다. 주로 팝업 창을 다룰 때 사용되며, 이 기능을 통해 부모 창과의 상호작용이 가능합니다. ## 문서화 ### 목적 `opener`...
Meta Keywords: opener, 창에서, popup, 있습니다, 자바스크립트에서
-->

# 자바스크립트에서 "opener"의 이해와 활용

## 개요
`opener`는 자바스크립트에서 현재 창을 연 상위 창을 참조하는 속성입니다. 주로 팝업 창을 다룰 때 사용되며, 이 기능을 통해 부모 창과의 상호작용이 가능합니다.

## 문서화
### 목적
`opener` 속성은 자바스크립트에서 현재 창을 연 부모 창의 참조를 제공합니다. 이는 팝업 창이 부모 창과 데이터를 주고받거나, 부모 창을 조작할 수 있도록 합니다.

### 사용법
`opener` 속성은 전역 `window` 객체의 속성으로 사용할 수 있습니다. 팝업 창에서 `opener`를 통해 부모 창의 JavaScript 함수나 변수에 접근할 수 있습니다.

### 세부 사항
- `opener`는 팝업 창에서만 의미가 있으며, 일반적인 브라우저 탭에서는 사용되지 않습니다.
- 부모 창이 닫힐 경우, `opener`는 `null`을 반환합니다.
- `opener`를 통해 부모 창의 DOM 요소에 접근할 수 있지만, 보안상의 이유로 같은 출처 정책(Same-Origin Policy)이 적용됩니다.

## 예제
### 기본 사용 예제
```javascript
// 부모 창에서 팝업을 열기
function openPopup() {
    window.open('popup.html', 'popup', 'width=600,height=400');
}

// 팝업 창에서 부모 창의 함수 호출
// popup.html 내의 JavaScript
if (opener) {
    opener.alert('부모 창에서 호출된 알림');
}
```

### 부모 창에서 데이터 보내기
```javascript
// 부모 창에서 팝업을 열 때 데이터 전달
function openPopupWithData() {
    const popup = window.open('popup.html', 'popup', 'width=600,height=400');
    popup.data = { message: '안녕하세요, 부모 창에서 팝업으로 데이터 전송!' };
}

// 팝업 창에서 데이터 사용
if (opener && opener.data) {
    console.log(opener.data.message);
}
```

## 설명
- **공통적인 문제점**: 팝업 차단기 때문에 `window.open`의 호출이 실패할 수 있습니다. 사용자는 팝업 차단기를 해제해야 합니다.
- **안전성**: `opener`를 사용하여 부모 창의 내용을 변경하는 것은 사용자의 브라우저 보안 설정에 따라 제한될 수 있습니다.
- **브라우저 지원**: 대부분의 현대 브라우저에서 지원되지만, 구형 브라우저에서는 호환성 문제가 발생할 수 있습니다.

## 한 줄 요약
`opener`는 자바스크립트에서 팝업 창이 부모 창에 접근할 수 있도록 해주는 속성입니다.