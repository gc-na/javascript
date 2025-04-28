<!--
Meta Description: # onpageshow: JavaScript의 페이지 표시 이벤트 ## 개요 `onpageshow`는 JavaScript에서 페이지가 표시될 때 발생하는 이벤트로, 특히 브라우저의 세션 히스토리 상태와 관련된 작업을 처리하는 데 유용합니다. 이 이벤트는 페이지가 처음 ...
Meta Keywords: 페이지가, onpageshow, event, 이벤트는, 있습니다
-->

# onpageshow: JavaScript의 페이지 표시 이벤트

## 개요
`onpageshow`는 JavaScript에서 페이지가 표시될 때 발생하는 이벤트로, 특히 브라우저의 세션 히스토리 상태와 관련된 작업을 처리하는 데 유용합니다. 이 이벤트는 페이지가 처음 로드되거나 다시 로드될 때 발생하며, 사용자 경험을 향상시키기 위한 다양한 기능을 구현할 수 있습니다.

## 문서화

### 목적
`onpageshow` 이벤트는 브라우저가 페이지를 보여줄 때 발생합니다. 이 이벤트는 페이지가 로드될 때와 세션 히스토리에서 다시 불러올 때 모두 발생하며, 이로 인해 페이지의 상태를 관리하는 데 유용합니다.

### 사용법
`onpageshow` 이벤트는 `window` 객체에 바인딩하여 사용할 수 있습니다. 이벤트 리스너를 추가하여 페이지가 표시될 때 특정 코드를 실행하도록 설정할 수 있습니다.

```javascript
window.onpageshow = function(event) {
    // 페이지가 표시될 때 실행되는 코드
    console.log("페이지가 표시되었습니다.");
    
    // event.persisted가 true일 경우, 페이지가 캐시에서 로드됨을 의미
    if (event.persisted) {
        console.log("페이지가 캐시에서 로드되었습니다.");
    }
};
```

### 세부 사항
- `onpageshow` 이벤트는 `Event` 객체를 인자로 받으며, 이 객체에는 `persisted`라는 속성이 포함되어 있습니다. 이 속성은 페이지가 캐시에서 로드되었는지 여부를 나타냅니다.
- 이벤트는 페이지가 처음 로드될 때와 브라우저의 '뒤로 가기' 버튼이나 '앞으로 가기' 버튼을 클릭하여 페이지를 탐색할 때 모두 발생합니다.
- `onpageshow`와 유사한 이벤트인 `onload`와는 다르게, `onpageshow`는 브라우저의 세션 히스토리와 밀접하게 연관되어 있습니다.

## 예제

### 기본 사용 예
```javascript
window.onpageshow = function(event) {
    alert("페이지가 표시되었습니다!");
};
```

### 캐시에서 로드된 페이지 확인 예
```javascript
window.onpageshow = function(event) {
    if (event.persisted) {
        console.log("이전 페이지가 캐시에서 로드되었습니다.");
    } else {
        console.log("새롭게 로드된 페이지입니다.");
    }
};
```

## 설명
- **일반적인 문제점**: `onpageshow` 이벤트는 페이지가 캐시에서 로드될 때와 새로 로드될 때 모두 발생하므로, 이를 정확히 구분하여 처리하는 것이 중요합니다. `event.persisted` 속성을 활용하여 페이지의 로드 상태를 확인하는 것이 좋습니다.
- **호환성**: 대부분의 최신 브라우저에서 `onpageshow`는 지원되지만, 이 이벤트가 모든 브라우저에서 동일하게 작동하지 않을 수 있으므로, 테스트가 필요합니다.
- **성능 고려**: 페이지가 자주 표시될 수 있는 경우, 이벤트 핸들러 내에서의 복잡한 연산은 성능 저하를 초래할 수 있습니다. 가능한 간단한 작업을 수행하는 것이 좋습니다.

## 한 줄 요약
`onpageshow`는 JavaScript에서 페이지가 표시될 때 발생하는 이벤트로, 페이지의 상태를 관리하는 데 유용합니다.