<!--
Meta Description: # JavaScript의 pageYOffset: 페이지 수직 스크롤 위치 가져오기 ## 개요 `pageYOffset`는 JavaScript에서 현재 문서의 수직 스크롤 위치를 가져오는 속성입니다. 스크롤 위치를 확인하는 데 유용하며, 사용자 인터페이스(UI) 또는 애니...
Meta Keywords: 스크롤, pageyoffset, window, 위치를, 있습니다
-->

# JavaScript의 pageYOffset: 페이지 수직 스크롤 위치 가져오기

## 개요
`pageYOffset`는 JavaScript에서 현재 문서의 수직 스크롤 위치를 가져오는 속성입니다. 스크롤 위치를 확인하는 데 유용하며, 사용자 인터페이스(UI) 또는 애니메이션과 같은 다양한 웹 애플리케이션에서 활용됩니다.

## 문서화
`pageYOffset`는 전역 객체인 `window`의 속성으로, 현재 문서에서 스크롤된 수직 거리(px)를 픽셀 단위로 반환합니다. 이 값은 문서의 상단에서 현재 스크롤 위치까지의 거리를 측정합니다.

### 목적
- 웹 페이지의 스크롤 위치를 알기 위해 사용됩니다.
- 스크롤 이벤트를 감지하여 동적인 효과를 구현할 수 있습니다.

### 사용법
`pageYOffset`는 다음과 같이 사용됩니다:

```javascript
let scrollPosition = window.pageYOffset;
```

이 코드는 현재 스크롤 위치를 `scrollPosition` 변수에 저장합니다. 값이 0일 경우, 페이지가 최상단에 위치하고 있음을 의미합니다.

### 세부정보
- `pageYOffset`는 읽기 전용 속성입니다.
- 모든 주요 브라우저에서 지원되며, Internet Explorer 11 및 그 이전 버전에서는 사용할 수 없습니다.
- `scrollY` 속성과 동일한 기능을 제공합니다. 

## 예제
여기 `pageYOffset`를 사용하는 몇 가지 기본 예제가 있습니다.

### 예제 1: 현재 스크롤 위치 출력
```javascript
window.addEventListener('scroll', function() {
    console.log('현재 스크롤 위치:', window.pageYOffset);
});
```

### 예제 2: 특정 위치에서 배경 색상 변경
```javascript
window.addEventListener('scroll', function() {
    if (window.pageYOffset > 200) {
        document.body.style.backgroundColor = 'lightblue';
    } else {
        document.body.style.backgroundColor = 'white';
    }
});
```

## 설명
`pageYOffset`를 사용할 때 주의할 점은 다음과 같습니다:

- **브라우저 호환성**: `pageYOffset`는 다수의 현대 브라우저에서 지원되지만, 구형 브라우저에서는 `document.documentElement.scrollTop`을 사용해야 할 수 있습니다.
  
- **성능 문제**: 스크롤 이벤트는 빈번하게 발생하므로, 성능을 고려하여 debounce 또는 throttle을 적용하는 것이 좋습니다.

- **CSS 스크롤 속성**: CSS의 `overflow` 속성이나 스크롤바의 존재 여부에 따라 스크롤 값이 달라질 수 있습니다.

## 한 줄 요약
`pageYOffset`는 현재 문서의 수직 스크롤 위치를 픽셀 단위로 반환하는 JavaScript 속성입니다.