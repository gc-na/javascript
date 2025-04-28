<!--
Meta Description: # BeforeUnloadEvent: 자바스크립트에서 페이지 떠나기 전에 처리하는 방법 ## 개요 BeforeUnloadEvent는 사용자가 웹 페이지를 떠나기 전에 이벤트를 처리할 수 있도록 해주는 JavaScript 이벤트입니다. 이 이벤트는 사용자가 페이지를 닫거...
Meta Keywords: 페이지를, 사용자가, 떠나기, beforeunload, message
-->

# BeforeUnloadEvent: 자바스크립트에서 페이지 떠나기 전에 처리하는 방법

## 개요
BeforeUnloadEvent는 사용자가 웹 페이지를 떠나기 전에 이벤트를 처리할 수 있도록 해주는 JavaScript 이벤트입니다. 이 이벤트는 사용자가 페이지를 닫거나 새 페이지로 이동할 때 발생하며, 사용자가 변경 사항을 저장하지 않고 페이지를 떠나는 것을 방지할 수 있는 기회를 제공합니다.

## 문서화
BeforeUnloadEvent는 브라우저가 사용자가 페이지를 떠나려고 할 때 발생하는 `beforeunload` 이벤트와 밀접한 관련이 있습니다. 이 이벤트는 사용자가 페이지를 떠나기 전에 확인 메시지를 표시하여 중요한 데이터를 잃지 않도록 도와줍니다.

### 목적
- 사용자가 페이지를 떠나기 전에 저장되지 않은 변경 사항에 대한 경고를 표시합니다.
- 사용자가 의도치 않게 페이지를 떠나는 것을 방지합니다.

### 사용법
이벤트 리스너를 사용하여 `beforeunload` 이벤트를 등록합니다. 다음은 기본적인 사용법입니다:

```javascript
window.addEventListener('beforeunload', function (event) {
    // 사용자에게 보여줄 메시지
    const message = '변경 사항이 저장되지 않았습니다. 정말로 페이지를 떠나시겠습니까?';
    
    // Chrome, Firefox 등에서 사용자에게 메시지를 표시
    event.returnValue = message; // 표준
    return message; // 일부 브라우저에서 필요
});
```

## 예제
다음은 `beforeunload` 이벤트를 사용하는 간단한 예제입니다:

```javascript
window.addEventListener('beforeunload', function (event) {
    const message = '작성 중인 내용이 있습니다. 정말로 페이지를 떠나시겠습니까?';
    
    event.returnValue = message; // 경고 메시지 표시
    return message; // 일부 브라우저의 호환성 제공
});
```

## 설명
- **브라우저 지원**: `beforeunload` 이벤트는 대부분의 현대 브라우저에서 지원되지만, 각 브라우저는 사용자에게 보여줄 메시지의 커스터마이징을 제한할 수 있습니다.
- **사용자 경험**: 이 이벤트를 남용하면 사용자 경험이 나빠질 수 있으므로, 반드시 필요한 경우에만 사용해야 합니다. 예를 들어, 사용자가 입력한 데이터가 중요한 경우에만 경고를 표시하는 것이 좋습니다.
- **비동기 작업**: 비동기 작업이 진행 중일 경우, 사용자가 페이지를 떠나기 전에 이러한 작업이 완료되지 않을 수 있으므로 주의해야 합니다.

## 한 줄 요약
BeforeUnloadEvent는 사용자가 웹 페이지를 떠나기 전에 경고 메시지를 표시하여 데이터 손실을 방지하는 JavaScript 이벤트입니다.