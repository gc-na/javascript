<!--
Meta Description: # PerformanceScriptTiming: 자바스크립트 성능 측정의 새로운 도구 ## 개요 `PerformanceScriptTiming`은 웹 애플리케이션의 스크립트 실행 성능을 분석하고 최적화하는 데 도움을 주는 JavaScript API입니다. 이를 통해 개발...
Meta Keywords: entry, performancescripttiming, duration, script, 스크립트
-->

# PerformanceScriptTiming: 자바스크립트 성능 측정의 새로운 도구

## 개요
`PerformanceScriptTiming`은 웹 애플리케이션의 스크립트 실행 성능을 분석하고 최적화하는 데 도움을 주는 JavaScript API입니다. 이를 통해 개발자는 스크립트 로딩 및 실행 시간에 대한 세부 정보를 수집하여 애플리케이션 성능을 향상시킬 수 있습니다.

## 문서
`PerformanceScriptTiming` 인터페이스는 웹 페이지에서 실행되는 JavaScript 스크립트의 성능을 측정하는 데 필요한 메트릭을 제공합니다. 이 API는 `PerformanceEntry` 인터페이스의 인스턴스를 통해 접근할 수 있으며, 다음과 같은 주요 요소를 포함합니다:

- **startTime**: 스크립트가 로드되기 시작한 시간입니다.
- **duration**: 스크립트 실행이 완료될 때까지 걸린 시간입니다.
- **scriptUrl**: 측정된 스크립트의 URL입니다.

이 정보를 통해 개발자는 스크립트 성능을 모니터링하고, 최적화를 위한 인사이트를 얻을 수 있습니다. 

### 사용법
`PerformanceScriptTiming`은 `performance.getEntriesByType("script")`를 사용하여 접근할 수 있습니다. 이 메서드는 현재 페이지에서 로드된 모든 스크립트의 성능 데이터를 포함하는 배열을 반환합니다.

```javascript
const scriptTimings = performance.getEntriesByType("script");
scriptTimings.forEach((entry) => {
    console.log(`Script URL: ${entry.scriptUrl}`);
    console.log(`Start Time: ${entry.startTime}`);
    console.log(`Duration: ${entry.duration}`);
});
```

## 예제
다음은 `PerformanceScriptTiming`을 사용하여 웹 페이지에서 스크립트의 성능을 측정하는 예제입니다.

### 기본 예제
```javascript
// 페이지 로드 후 스크립트 성능 측정
window.onload = () => {
    const scriptTimings = performance.getEntriesByType("script");
    scriptTimings.forEach((entry) => {
        console.log(`Script: ${entry.scriptUrl} | Duration: ${entry.duration}ms`);
    });
};
```

### 조건부 필터링 예제
```javascript
window.onload = () => {
    const scriptTimings = performance.getEntriesByType("script").filter(entry => entry.duration > 100);
    scriptTimings.forEach((entry) => {
        console.warn(`Long running script detected: ${entry.scriptUrl} | Duration: ${entry.duration}ms`);
    });
};
```

## 설명
`PerformanceScriptTiming`을 사용할 때 유의해야 할 몇 가지 사항이 있습니다:

- **브라우저 호환성**: 모든 브라우저가 `PerformanceScriptTiming`을 지원하는 것은 아닙니다. 최신 브라우저에서의 테스트가 필요합니다.
- **스크립트 로드 순서**: 스크립트가 비동기적으로 로드되는 경우, 로드 순서에 따라 성능 데이터가 달라질 수 있습니다.
- **도메인 제한**: 다른 도메인에서 로드된 스크립트는 CORS 정책에 따라 제한될 수 있습니다. 이 경우 성능 데이터에 접근할 수 없습니다.

## 요약
`PerformanceScriptTiming`은 자바스크립트 스크립트의 성능을 측정하고 최적화하는 강력한 도구로, 개발자가 웹 애플리케이션의 효율성을 높이는 데 필수적입니다.