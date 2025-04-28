<!--
Meta Description: # PopStateEvent: JavaScript의 상태 관리 이벤트 ## 개요 PopStateEvent는 JavaScript의 History API에서 중요한 역할을 하는 이벤트로, 사용자에게 브라우저의 세션 기록에서 상태가 변경되었음을 알리는 데 사용됩니다. 이 이...
Meta Keywords: popstate, event, state, 이벤트가, 사용자가
-->

# PopStateEvent: JavaScript의 상태 관리 이벤트

## 개요
PopStateEvent는 JavaScript의 History API에서 중요한 역할을 하는 이벤트로, 사용자에게 브라우저의 세션 기록에서 상태가 변경되었음을 알리는 데 사용됩니다. 이 이벤트는 주로 페이지의 히스토리 상태가 변경될 때 발생하며, 싱글 페이지 애플리케이션(SPA)에서 유용하게 활용됩니다.

## 문서화
### 목적
PopStateEvent는 사용자가 브라우저의 '뒤로' 또는 '앞으로' 버튼을 클릭할 때 발생합니다. 이 이벤트를 통해 개발자는 특정 상태와 관련된 작업을 수행할 수 있습니다.

### 사용법
PopStateEvent를 사용하려면 `window.onpopstate` 이벤트 리스너를 설정해야 합니다. 이 이벤트는 `popstate`라는 이름으로 발생하며, 상태 객체를 포함합니다.

#### 기본 문법
```javascript
window.onpopstate = function(event) {
    // 상태 변경 시 실행할 코드
    console.log(event.state);
};
```

### 세부 사항
- `event.state`: popstate 이벤트가 발생했을 때의 상태 객체를 참조합니다.
- `pushState()`와 `replaceState()`: 이 두 메서드를 사용해 히스토리의 상태를 조작할 수 있습니다. 이 메서드들을 호출하면 popstate 이벤트가 발생하지 않지만, 사용자가 뒤로 가기를 할 경우 popstate 이벤트가 발생합니다.

## 예제
### 기본 사용 예
```javascript
// 상태를 추가
history.pushState({ page: 1 }, "title 1", "?page=1");

// popstate 이벤트 리스너 설정
window.onpopstate = function(event) {
    if (event.state) {
        console.log("현재 페이지 상태:", event.state);
    } else {
        console.log("상태가 없습니다.");
    }
};

// 사용자가 뒤로 가기를 클릭할 때 popstate 이벤트가 발생합니다.
```

## 설명
### 일반적인 오류 및 주의사항
- **이벤트의 발생 조건**: popstate 이벤트는 `pushState()`나 `replaceState()` 호출 후에 발생하지 않습니다. 사용자가 실제로 히스토리 스택에서 이동해야 이벤트가 발생합니다.
- **상태 객체의 초기화**: 초기 상태를 설정하지 않으면 `event.state`가 `null`일 수 있습니다. 따라서 상태를 명시적으로 설정하는 것이 좋습니다.
- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 동작하지 않을 수 있으니 확인이 필요합니다.

## 한 줄 요약
PopStateEvent는 브라우저의 세션 기록에서 상태 변경 시 발생하는 이벤트로, 상태 관리에 필수적입니다.