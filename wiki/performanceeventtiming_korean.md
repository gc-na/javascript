<!--
Meta Description: # PerformanceEventTiming: 자바스크립트의 성능 측정 이벤트 ## 개요 `PerformanceEventTiming`은 웹 애플리케이션의 성능을 측정하기 위해 사용되는 JavaScript 인터페이스입니다. 이 인터페이스는 특정 이벤트의 시작 시간 및 지...
Meta Keywords: 이벤트, event, performanceeventtiming, performance, console
-->

# PerformanceEventTiming: 자바스크립트의 성능 측정 이벤트

## 개요
`PerformanceEventTiming`은 웹 애플리케이션의 성능을 측정하기 위해 사용되는 JavaScript 인터페이스입니다. 이 인터페이스는 특정 이벤트의 시작 시간 및 지속 시간을 기록하여 개발자가 애플리케이션의 성능을 분석하고 최적화하는 데 도움을 줍니다.

## 문서화
`PerformanceEventTiming`은 웹 성능 API의 일환으로, 사용자 상호작용 이벤트를 측정하는 데 사용됩니다. 이 객체는 이벤트가 발생한 시점을 기록하고, 이를 통해 성능 분석과 문제 해결을 용이하게 합니다.

### 목적
- 웹 애플리케이션의 성능 문제를 파악하기 위해 이벤트의 발생 시점과 소요 시간을 기록합니다.
- 개발자가 사용자 경험을 개선할 수 있는 인사이트를 제공합니다.

### 사용법
`PerformanceEventTiming` 객체는 자동으로 생성되며, `Performance` 인터페이스의 `getEntriesByType()` 메서드를 통해 접근할 수 있습니다. 이 메서드는 'event' 유형의 성능 엔트리를 반환합니다.

```javascript
const entries = performance.getEntriesByType("event");
entries.forEach(entry => {
    console.log(`이벤트: ${entry.name}`);
    console.log(`시작 시간: ${entry.startTime}`);
    console.log(`지속 시간: ${entry.duration}`);
});
```

### 상세 정보
- `PerformanceEventTiming` 객체는 다음과 같은 속성을 포함합니다:
  - `name`: 이벤트의 이름
  - `startTime`: 이벤트가 시작된 시점 (밀리초 단위)
  - `duration`: 이벤트가 발생하는 데 걸린 시간 (밀리초 단위)
  - `processingStart`: 이벤트 처리 시작 시간
  - `processingEnd`: 이벤트 처리 완료 시간

## 예제
```javascript
// 이벤트 리스너 등록
document.addEventListener('click', (event) => {
    // 이벤트 발생 시 성능 기록
    const mark = performance.mark('event-start');
    
    // 이벤트 처리 로직
    console.log('클릭 이벤트 발생!');

    const markEnd = performance.mark('event-end');
    performance.measure('click-event', 'event-start', 'event-end');
});

// 성능 측정 결과 출력
const measures = performance.getEntriesByType('measure');
measures.forEach(measure => {
    console.log(`측정: ${measure.name}, 시간: ${measure.duration}ms`);
});
```

## 설명
`PerformanceEventTiming`을 사용할 때 주의할 점은 다음과 같습니다:
- 이벤트가 발생하기 전에 성능 마크를 설정해야 합니다.
- 성능 측정은 비동기 작업에 영향을 받을 수 있으므로, 정확한 측정을 위해 이벤트 처리 로직을 최적화해야 합니다.
- 브라우저 호환성 문제가 있을 수 있으므로, 다양한 브라우저에서의 테스트가 필요합니다.

## 한 줄 요약
`PerformanceEventTiming`은 웹 애플리케이션의 이벤트 성능을 측정하여 개발자가 성능 최적화를 할 수 있도록 돕는 JavaScript 인터페이스입니다.