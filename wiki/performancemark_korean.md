<!--
Meta Description: # PerformanceMark: JavaScript 성능 측정의 최전선 ## 개요 `PerformanceMark`는 브라우저에서 성능 측정 및 분석을 위한 API의 일부로, 웹 애플리케이션의 특정 지점을 마크하여 성능 데이터를 수집하고 분석하는 데 도움을 줍니다. 이...
Meta Keywords: performance, performancemark, mark, 데이터를, 마크의
-->

# PerformanceMark: JavaScript 성능 측정의 최전선

## 개요
`PerformanceMark`는 브라우저에서 성능 측정 및 분석을 위한 API의 일부로, 웹 애플리케이션의 특정 지점을 마크하여 성능 데이터를 수집하고 분석하는 데 도움을 줍니다. 이는 개발자가 애플리케이션의 성능을 최적화하고 개선하는 데 필수적인 도구입니다.

## 문서화

### 목적
`PerformanceMark`는 웹 페이지의 특정 이벤트 또는 상태를 기록하여 성능 분석을 가능하게 합니다. 이 API는 성능 측정을 표준화된 방식으로 하여, 개발자가 성능 개선을 위해 필요한 데이터를 수집할 수 있도록 합니다.

### 사용법
`PerformanceMark`를 사용하려면 다음 단계를 따르세요:

1. **마크 생성**: `performance.mark()` 메서드를 사용하여 특정 지점을 마크합니다.
2. **마크 조회**: `performance.getEntriesByType('mark')` 메서드를 사용하여 생성한 마크의 목록을 가져옵니다.
3. **마크 삭제**: 필요 시 `performance.clearMarks()` 메서드를 통해 마크를 삭제할 수 있습니다.

### 세부 사항
- **마크의 이름**: 각 마크는 고유한 이름을 가져야 하며, 이는 문자열로 지정합니다.
- **타임스탬프**: 마크는 생성된 시점의 타임스탬프를 기록합니다.
- **브라우저 지원**: 대부분의 현대 웹 브라우저에서 지원되며, IE11을 제외한 여러 주요 브라우저에서 사용할 수 있습니다.

## 예제

### 기본 사용 예
```javascript
// 성능 마크 생성
performance.mark('startLoading');

// 페이지 로딩 시점
setTimeout(() => {
    // 성능 마크 생성
    performance.mark('endLoading');

    // 마크 목록 조회
    const marks = performance.getEntriesByType('mark');
    console.log(marks);
}, 2000);
```

### 마크 삭제 예
```javascript
// 특정 마크 삭제
performance.clearMarks('startLoading');
```

## 설명
- **일관된 명명 규칙**: 마크의 이름을 일관되게 유지하는 것이 중요합니다. 서로 다른 마크가 동일한 이름을 가질 경우, 데이터가 혼란스러울 수 있습니다.
- **성능 데이터 분석**: 마크를 사용하여 측정된 성능 데이터를 기반으로 분석을 수행할 수 있으며, 이를 통해 최적화 방향을 결정할 수 있습니다.
- **비동기 작업**: 비동기 작업의 성능을 측정할 때는 마크의 생성 시점에 유의해야 합니다.

## 한 줄 요약
`PerformanceMark`는 JavaScript에서 웹 애플리케이션의 성능 측정을 위한 강력한 도구로, 특정 이벤트를 마크하여 성능 데이터를 수집하고 분석하는 기능을 제공합니다.