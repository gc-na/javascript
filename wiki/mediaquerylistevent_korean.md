<!--
Meta Description: # MediaQueryListEvent: 자바스크립트에서 미디어 쿼리 이벤트 다루기 ## 개요 `MediaQueryListEvent`는 자바스크립트에서 미디어 쿼리의 상태 변화에 대한 정보를 전달하는 이벤트 객체입니다. 이 객체는 브라우저의 뷰포트 크기나 방향에 따라 ...
Meta Keywords: 미디어, mediaquerylistevent, 이벤트, 쿼리의, mediaquerylist
-->

# MediaQueryListEvent: 자바스크립트에서 미디어 쿼리 이벤트 다루기

## 개요
`MediaQueryListEvent`는 자바스크립트에서 미디어 쿼리의 상태 변화에 대한 정보를 전달하는 이벤트 객체입니다. 이 객체는 브라우저의 뷰포트 크기나 방향에 따라 CSS 미디어 쿼리가 변할 때 발생합니다. 주로 반응형 웹 디자인에서 유용하게 사용됩니다.

## 문서화
`MediaQueryListEvent`는 `MediaQueryList` 객체의 이벤트로, 미디어 쿼리의 상태가 변경될 때 발생합니다. 이 이벤트는 주로 다음과 같은 상황에서 사용됩니다:

- CSS 미디어 쿼리의 조건이 충족되거나 충족되지 않을 때.
- 뷰포트의 크기나 방향이 변경될 때.

### 사용법
`MediaQueryListEvent`는 `addListener` 메서드와 `removeListener` 메서드를 통해 등록 및 해제할 수 있으며, `matches` 속성을 통해 현재 미디어 쿼리가 충족되는지를 확인할 수 있습니다.

```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');

function handleMediaChange(event) {
    if (event.matches) {
        console.log('뿌리기: 화면 너비가 600px 이하입니다.');
    } else {
        console.log('뿌리기: 화면 너비가 600px를 초과합니다.');
    }
}

// 리스너 등록
mediaQueryList.addEventListener('change', handleMediaChange);

// 초기 상태 확인
handleMediaChange(mediaQueryList);
```

## 예제
다음은 `MediaQueryListEvent`를 사용하는 기본적인 예제입니다.

```javascript
// 미디어 쿼리 설정
const mediaQuery = window.matchMedia('(orientation: landscape)');

// 이벤트 핸들러 정의
function orientationChangeHandler(event) {
    if (event.matches) {
        console.log('화면 방향: 가로');
    } else {
        console.log('화면 방향: 세로');
    }
}

// 이벤트 리스너 등록
mediaQuery.addEventListener('change', orientationChangeHandler);

// 초기 상태 확인
orientationChangeHandler(mediaQuery);
```

## 설명
`MediaQueryListEvent`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- 이벤트 리스너는 `addListener` 대신 `addEventListener`를 사용하는 것이 좋습니다. 후자가 더 최신의 표준이며, 이벤트 핸들러가 더 잘 관리됩니다.
- 브라우저 호환성에 유의해야 합니다. `addEventListener`는 최신 브라우저에서 지원되지만, 구형 브라우저에서는 `addListener`가 필요할 수 있습니다.
- 이벤트가 발생할 때마다 모든 조건을 다시 확인해야 할 수 있습니다. 성능을 고려하여 불필요한 계산을 피하도록 주의합니다.

## 한 줄 요약
`MediaQueryListEvent`는 자바스크립트에서 미디어 쿼리의 상태 변화를 감지하고 처리하는 데 사용되는 이벤트 객체입니다.