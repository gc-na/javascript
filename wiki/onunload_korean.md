<!--
Meta Description: # JavaScript의 onunload 이벤트: 페이지 종료 시 실행되는 코드 ## 개요 `onunload` 이벤트는 사용자가 웹 페이지를 떠날 때 발생하는 이벤트로, 페이지 종료 시 특정 작업을 수행할 수 있도록 도와줍니다. 이 이벤트는 사용자가 페이지를 닫거나 다...
Meta Keywords: onunload, 이벤트는, 페이지를, 있습니다, 사용자가
-->

# JavaScript의 onunload 이벤트: 페이지 종료 시 실행되는 코드

## 개요
`onunload` 이벤트는 사용자가 웹 페이지를 떠날 때 발생하는 이벤트로, 페이지 종료 시 특정 작업을 수행할 수 있도록 도와줍니다. 이 이벤트는 사용자가 페이지를 닫거나 다른 페이지로 이동할 때 트리거됩니다.

## 문서화
### 목적
`onunload` 이벤트는 주로 세션 종료, 데이터 저장, 사용자에게 알림을 표시하는 등의 작업을 수행하기 위해 사용됩니다. 예를 들어, 사용자가 페이지를 떠날 때 경고 메시지를 표시하거나 마지막 데이터 전송을 수행할 수 있습니다.

### 사용법
`onunload` 이벤트는 `window` 객체에 직접 할당하거나 HTML 요소의 속성으로 지정할 수 있습니다. 다음은 두 가지 방법의 예입니다.

#### 방법 1: JavaScript를 통해 이벤트 핸들러 추가
```javascript
window.onunload = function() {
    console.log("페이지를 떠나고 있습니다.");
};
```

#### 방법 2: HTML 속성 사용
```html
<body onunload="alert('페이지를 떠납니다!');">
    ...
</body>
```

### 세부사항
- `onunload` 이벤트는 페이지가 완전히 종료될 때 발생합니다.
- 이 이벤트는 비동기 작업(예: AJAX 요청)을 완료할 시간을 충분히 주지 않으므로, 비동기 작업을 처리할 때 주의해야 합니다.
- 브라우저의 보안 정책으로 인해, `onunload` 이벤트에서 사용자 인터페이스를 차단할 수 있는 작업(예: 팝업 창 열기)은 제한될 수 있습니다.

## 예제
예제 1: 사용자에게 페이지 이탈 경고 표시
```javascript
window.onunload = function() {
    return "정말로 페이지를 떠나시겠습니까?";
};
```

예제 2: 마지막 데이터 저장
```javascript
window.onunload = function() {
    // 마지막 데이터 저장 로직
    saveUserData();
};
```

## 설명
- `onunload` 이벤트는 페이지가 종료될 때 실행되므로, 비동기 요청의 완료를 보장하지 않습니다. 즉, 이 이벤트에서 비동기 작업이 완료되지 않을 수 있습니다.
- 사용자가 페이지를 떠날 때, 경고 메시지를 표시할 경우, 대화 상자가 표시되지만, 이를 무시하고 계속 진행할 수 있습니다.
- 모든 브라우저에서 `onunload`의 동작이 다를 수 있으므로, 크로스 브라우저 호환성에 주의해야 합니다.

## 한 줄 요약
`onunload` 이벤트는 사용자가 웹 페이지를 떠날 때 특정 작업을 수행할 수 있게 해주는 JavaScript 이벤트입니다.