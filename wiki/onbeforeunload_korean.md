<!--
Meta Description: # JavaScript의 onbeforeunload 이벤트: 페이지 이탈 확인하기 ## 개요 `onbeforeunload` 이벤트는 사용자가 웹 페이지를 떠나기 전에 사용자에게 경고 메시지를 표시할 수 있도록 해주는 JavaScript 이벤트입니다. 이 이벤트는 주로 ...
Meta Keywords: onbeforeunload, 사용자가, message, 페이지를, 이벤트는
-->

# JavaScript의 onbeforeunload 이벤트: 페이지 이탈 확인하기

## 개요
`onbeforeunload` 이벤트는 사용자가 웹 페이지를 떠나기 전에 사용자에게 경고 메시지를 표시할 수 있도록 해주는 JavaScript 이벤트입니다. 이 이벤트는 주로 사용자가 데이터를 잃어버리지 않도록 경고하는 데 사용됩니다.

## 문서화
### 목적
`onbeforeunload` 이벤트는 사용자가 페이지를 닫거나 새로 고치거나 다른 페이지로 이동할 때 발생합니다. 이 이벤트를 활용하면 사용자가 의도치 않게 중요한 정보를 잃지 않도록 경고 메시지를 표시할 수 있습니다.

### 사용법
`onbeforeunload` 이벤트는 `window` 객체에 속하며, 이벤트 핸들러를 등록하여 사용할 수 있습니다. 아래와 같은 형식으로 사용됩니다:

```javascript
window.onbeforeunload = function(event) {
    const message = "정말로 이 페이지를 떠나시겠습니까?";
    event.returnValue = message; // 표준 브라우저에서 경고 메시지 표시
    return message; // 구식 브라우저에서 사용
};
```

### 세부 정보
- 이벤트가 발생하면 사용자는 페이지를 떠나기 전에 경고 메시지를 보게 됩니다.
- 브라우저에 따라 기본 제공되는 메시지가 표시될 수 있으며, 사용자가 지정한 메시지는 무시될 수 있습니다.
- 이 이벤트는 사용자 경험에 영향을 미칠 수 있으므로 신중하게 사용해야 합니다.

## 예제
### 기본 사용 예제
다음은 `onbeforeunload` 이벤트를 사용하는 간단한 예제입니다:

```javascript
window.onbeforeunload = function(event) {
    const message = "변경 사항이 저장되지 않을 수 있습니다. 정말로 페이지를 떠나시겠습니까?";
    event.returnValue = message;
    return message;
};
```

### 조건부 사용 예제
특정 조건에서만 경고 메시지를 표시하는 방법입니다:

```javascript
let isFormDirty = false;

document.getElementById("myForm").addEventListener("change", function() {
    isFormDirty = true; // 폼이 변경되었음을 표시
});

window.onbeforeunload = function(event) {
    if (isFormDirty) {
        const message = "변경 사항이 저장되지 않았습니다. 정말로 페이지를 떠나시겠습니까?";
        event.returnValue = message;
        return message;
    }
};
```

## 설명
- `onbeforeunload` 이벤트는 모든 브라우저에서 지원되지만, 브라우저에 따라 다르게 동작할 수 있습니다. 특히, 사용자가 지정한 메시지가 무시될 수 있으니 주의해야 합니다.
- 사용자가 페이지를 떠날 때 보여지는 메시지는 사용자가 직접 수정할 수 없습니다. 보안상의 이유로 브라우저에서 제공하는 기본 메시지가 표시됩니다.
- 이 이벤트를 너무 자주 사용하면 사용자에게 불편을 줄 수 있으므로, 정말 필요한 경우에만 사용하는 것이 좋습니다.

## 한 줄 요약
`onbeforeunload` 이벤트는 사용자가 페이지를 떠날 때 경고 메시지를 표시하여 중요한 정보의 손실을 방지하는 JavaScript 기능입니다.