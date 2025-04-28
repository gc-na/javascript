<!--
Meta Description: # visualViewport: JavaScript의 시각적 뷰포트 API ## 개요 `visualViewport`는 웹 페이지의 뷰포트(화면에서 보여지는 영역)의 크기 및 위치에 대한 정보를 제공하는 JavaScript API입니다. 이 API는 특히 모바일 디바이스...
Meta Keywords: visualviewport, 뷰포트의, 반환합니다, 뷰포트, javascript
-->

# visualViewport: JavaScript의 시각적 뷰포트 API

## 개요
`visualViewport`는 웹 페이지의 뷰포트(화면에서 보여지는 영역)의 크기 및 위치에 대한 정보를 제공하는 JavaScript API입니다. 이 API는 특히 모바일 디바이스에서의 사용자 경험을 개선하는 데 유용합니다.

## 문서화
### 목적
`visualViewport` API는 사용자가 화면을 확대하거나 스크롤할 때 뷰포트의 크기와 위치를 동적으로 추적할 수 있도록 해줍니다. 이를 통해 개발자는 사용자 인터페이스(UI)를 보다 매끄럽게 조정할 수 있습니다.

### 사용법
`visualViewport`를 사용하려면 다음과 같은 방법으로 접근할 수 있습니다:

```javascript
const viewport = visualViewport;
```

### 주요 속성
- **width**: 뷰포트의 현재 너비를 픽셀 단위로 반환합니다.
- **height**: 뷰포트의 현재 높이를 픽셀 단위로 반환합니다.
- **offsetLeft**: 뷰포트의 왼쪽 경계와 스크린의 왼쪽 경계 사이의 거리(픽셀)를 반환합니다.
- **offsetTop**: 뷰포트의 위쪽 경계와 스크린의 위쪽 경계 사이의 거리(픽셀)를 반환합니다.
- **scale**: 뷰포트의 확대/축소 비율을 반환합니다.

### 이벤트
`visualViewport`는 다음과 같은 이벤트를 지원합니다:
- **resize**: 뷰포트의 크기가 변경될 때 발생합니다.
- **scroll**: 뷰포트의 스크롤 위치가 변경될 때 발생합니다.

## 예제
### 기본 사용 예제
```javascript
window.visualViewport.addEventListener('resize', () => {
    console.log(`Viewport width: ${visualViewport.width}, height: ${visualViewport.height}`);
});

window.visualViewport.addEventListener('scroll', () => {
    console.log(`Viewport offset: (${visualViewport.offsetLeft}, ${visualViewport.offsetTop})`);
});
```

## 설명
### 일반적인 함정 및 주의사항
- **브라우저 지원**: 모든 브라우저에서 `visualViewport` API를 지원하지 않습니다. 최신 브라우저에서 사용해야 하며, 구형 브라우저에서는 대체 방법을 고려해야 합니다.
- **이벤트 중복 처리**: 이벤트 리스너를 추가할 때 중복 등록을 피하기 위해 주의해야 합니다. 필요 시 이벤트 리스너를 제거하는 것도 고려해야 합니다.
- **비동기 처리**: 뷰포트 크기나 위치를 계산할 때 비동기 작업의 영향을 받을 수 있으므로, 필요 시 적절한 디바운싱(debouncing) 기법을 적용해야 합니다.

## 한 줄 요약
`visualViewport` API는 웹 페이지의 뷰포트 크기와 위치를 동적으로 추적하여 사용자 경험을 향상시키는 JavaScript 기능입니다.