<!--
Meta Description: # JavaScript scrollY: 스크롤 위치를 확인하는 방법 ## 개요 `scrollY`는 JavaScript에서 현재 문서의 수직 스크롤 위치를 픽셀 단위로 반환하는 속성입니다. 이를 통해 사용자는 페이지 내에서 스크롤이 얼마나 이동했는지를 쉽게 확인할 수 있...
Meta Keywords: 스크롤, scrolly, 위치를, window, javascript
-->

# JavaScript scrollY: 스크롤 위치를 확인하는 방법

## 개요
`scrollY`는 JavaScript에서 현재 문서의 수직 스크롤 위치를 픽셀 단위로 반환하는 속성입니다. 이를 통해 사용자는 페이지 내에서 스크롤이 얼마나 이동했는지를 쉽게 확인할 수 있습니다.

## 문서화
### 목적
`scrollY`는 전역 `window` 객체의 속성으로, 사용자가 웹 페이지를 수직으로 스크롤한 거리(위치)를 나타냅니다. 이 속성은 페이지의 현재 스크롤 위치를 확인하고, 스크롤 이벤트에 따라 동작을 조절하는 데 유용합니다.

### 사용법
```javascript
let scrollPosition = window.scrollY;
```
- **반환값**: 현재 수직 스크롤 위치를 픽셀 단위로 반환합니다. 예를 들어, 페이지의 가장 위쪽에 있을 경우 `scrollY` 값은 `0`입니다.

### 세부 사항
- `scrollY`는 읽기 전용 속성입니다.
- `document.documentElement.scrollTop`과 같은 다른 속성과 유사하지만, `scrollY`는 항상 현재 스크롤 위치를 정확하게 반환합니다.
- 이 속성은 모든 주요 브라우저에서 지원됩니다.

## 예제
### 기본 사용 예제
```javascript
// 현재 스크롤 위치를 콘솔에 출력
window.addEventListener('scroll', function() {
    console.log('현재 스크롤 Y 위치: ', window.scrollY);
});
```

### 스크롤 위치에 따른 조건부 동작
```javascript
window.addEventListener('scroll', function() {
    if (window.scrollY > 100) {
        console.log('스크롤이 100픽셀을 초과했습니다.');
    } else {
        console.log('스크롤이 100픽셀 이하입니다.');
    }
});
```

## 설명
`scrollY`를 사용할 때 주의해야 할 점은 다음과 같습니다:
- **성능 이슈**: 스크롤 이벤트는 매우 빈번하게 발생하므로, 스크롤 위치를 확인하는 코드가 비효율적일 경우 성능 저하를 유발할 수 있습니다. 이럴 경우, `throttle` 또는 `debounce` 기법을 사용하는 것이 좋습니다.
- **CSS 스타일**: 스크롤이 발생하는 요소(예: `overflow: auto`가 설정된 div)와 `window` 객체의 스크롤을 혼동하지 않도록 주의해야 합니다. 이 경우 `scrollTop`을 사용해야 할 수 있습니다.

## 한 줄 요약
`scrollY`는 현재 문서의 수직 스크롤 위치를 픽셀 단위로 반환하는 JavaScript 속성입니다.