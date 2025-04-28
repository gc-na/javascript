<!--
Meta Description: # PerformanceNavigationTiming: JavaScript 성능 측정의 기초 ## 개요 `PerformanceNavigationTiming`은 웹 페이지의 로드 성능을 측정하고 분석하는 데 사용되는 JavaScript 인터페이스입니다. 이 API는 페이...
Meta Keywords: performancenavigationtiming, 페이지, timing, javascript, 페이지의
-->

# PerformanceNavigationTiming: JavaScript 성능 측정의 기초

## 개요
`PerformanceNavigationTiming`은 웹 페이지의 로드 성능을 측정하고 분석하는 데 사용되는 JavaScript 인터페이스입니다. 이 API는 페이지 로드 이벤트에 대한 세부 정보를 제공하여 개발자가 웹 애플리케이션의 성능을 최적화하는 데 도움을 줍니다.

## 문서화
### 목적
`PerformanceNavigationTiming`은 브라우저가 웹 페이지를 로드하는 과정에서 발생하는 여러 이벤트와 시간 정보를 수집합니다. 이를 통해 개발자는 페이지 로드 시간, 리디렉션 시간, 그리고 기타 성능 관련 지표를 확인할 수 있습니다.

### 사용 방법
`PerformanceNavigationTiming` 객체는 `performance.getEntriesByType("navigation")` 메서드를 통해 접근할 수 있습니다. 이 객체는 다음과 같은 주요 속성을 포함합니다:

- `startTime`: 페이지 로드 요청이 시작된 시간 (밀리초)
- `redirectCount`: 페이지가 로드되기까지의 리디렉션 횟수
- `responseEnd`: 서버 응답이 끝난 시간
- `domComplete`: DOM이 완전히 로드된 시간
- `loadEventEnd`: 페이지의 load 이벤트가 끝난 시간

#### 코드 예시
```javascript
window.addEventListener('load', () => {
    const navigationEntries = performance.getEntriesByType("navigation");
    if (navigationEntries.length > 0) {
        const timing = navigationEntries[0];
        console.log("페이지 로드 시간:", timing.loadEventEnd - timing.startTime);
        console.log("리디렉션 횟수:", timing.redirectCount);
        console.log("DOM 완전 로드 시간:", timing.domComplete);
    }
});
```

## 설명
`PerformanceNavigationTiming`을 사용할 때 유의해야 할 점은 다음과 같습니다:

1. **브라우저 호환성**: 모든 브라우저가 `PerformanceNavigationTiming`을 지원하는 것은 아닙니다. 최신 브라우저에서의 지원 여부를 확인해야 합니다.
2. **비동기 로딩**: AJAX 요청이나 비동기 스크립트 로딩이 포함된 페이지의 경우, 로드 시간 측정이 다를 수 있습니다.
3. **멀티페이지 애플리케이션**: SPA(Single Page Application)의 경우, 페이지 전환에 따른 성능 측정이 복잡할 수 있습니다.

## 한 줄 요약
`PerformanceNavigationTiming`은 웹 페이지의 로드 성능을 정밀하게 측정하고 분석하는 JavaScript API입니다.