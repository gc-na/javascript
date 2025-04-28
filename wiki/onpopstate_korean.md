<!--
Meta Description: # onpopstate: JavaScript의 히스토리 API 이벤트 처리 ## 개요 `onpopstate`는 JavaScript의 히스토리 API에서 발생하는 이벤트로, 사용자가 브라우저의 뒤로 가기 또는 앞으로 가기 버튼을 클릭할 때 발생합니다. 이 이벤트는 웹 애...
Meta Keywords: onpopstate, event, 이벤트, 브라우저의, 이벤트는
-->

# onpopstate: JavaScript의 히스토리 API 이벤트 처리

## 개요
`onpopstate`는 JavaScript의 히스토리 API에서 발생하는 이벤트로, 사용자가 브라우저의 뒤로 가기 또는 앞으로 가기 버튼을 클릭할 때 발생합니다. 이 이벤트는 웹 애플리케이션의 상태를 관리하는 데 유용합니다.

## 문서화
### 목적
`onpopstate` 이벤트는 브라우저의 세션 히스토리에 있는 엔트리의 상태 객체를 반환합니다. 이 이벤트를 사용하여 사용자가 페이지 내비게이션을 할 때 애플리케이션의 상태를 업데이트할 수 있습니다.

### 사용법
`onpopstate` 이벤트는 `window` 객체에 바인딩할 수 있습니다. 아래의 구문을 사용하여 이벤트 핸들러를 등록할 수 있습니다.

```javascript
window.onpopstate = function(event) {
    // 이벤트 핸들러 코드
};
```

- `event.state`: 현재 상태 객체를 나타냅니다. `pushState` 또는 `replaceState` 메서드로 설정된 객체입니다.

### 세부 사항
- `onpopstate` 이벤트는 `pushState` 또는 `replaceState` 메서드를 호출한 후에 브라우저의 히스토리에서 상태가 변경될 때 발생합니다.
- 페이지가 로드될 때 페이지의 초기 상태가 `popstate` 이벤트로 발생할 수 있습니다.
- 사용자가 URL을 직접 입력하거나 링크를 클릭하여 페이지를 새로 고침할 때도 이 이벤트가 발생할 수 있습니다.

## 예제
아래는 `onpopstate` 이벤트를 사용하는 기본적인 예제입니다.

```javascript
// 상태 객체를 추가
history.pushState({page: 1}, "Title 1", "?page=1");

// 이벤트 핸들러 등록
window.onpopstate = function(event) {
    if (event.state) {
        console.log("현재 페이지:", event.state.page);
    } else {
        console.log("초기 상태");
    }
};

// 페이지를 뒤로 이동할 때 상태를 확인
```

## 설명
`onpopstate` 이벤트를 사용할 때 주의해야 할 점은 다음과 같습니다:

- 페이지가 로드될 때 초기 상태가 설정되지 않는 경우, `event.state`는 `null`이 됩니다.
- 여러 개의 상태를 푸시할 경우, `onpopstate` 이벤트는 각 상태에 대해 정확히 한 번씩 발생합니다. 따라서 상태 관리를 제대로 구현해야 합니다.
- 브라우저의 히스토리 스택이 변경된 경우에만 이 이벤트가 발생하므로, 다른 방법으로 상태를 변경할 경우에는 추가적인 이벤트 처리가 필요합니다.

## 한 줄 요약
`onpopstate`는 브라우저의 히스토리에서 페이지 내비게이션이 발생할 때 상태 객체를 처리하는 JavaScript 이벤트입니다.