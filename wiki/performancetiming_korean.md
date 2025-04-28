<!--
Meta Description: # PerformanceTiming: JavaScript의 성능 측정 API ## 개요 PerformanceTiming은 웹 페이지의 로드 시간 및 성능 관련 메트릭을 수집하는 데 사용되는 JavaScript API입니다. 이 API는 웹 애플리케이션의 성능을 모니터링...
Meta Keywords: timing, 페이지, 이벤트, 페이지의, performancetiming은
-->

# PerformanceTiming: JavaScript의 성능 측정 API

## 개요
PerformanceTiming은 웹 페이지의 로드 시간 및 성능 관련 메트릭을 수집하는 데 사용되는 JavaScript API입니다. 이 API는 웹 애플리케이션의 성능을 모니터링하고 최적화하는 데 유용합니다.

## 문서화
PerformanceTiming은 `window.performance.timing` 객체를 통해 접근할 수 있으며, 이 객체는 여러 시간 관련 속성을 제공합니다. 이러한 속성들은 페이지가 로드되는 동안의 다양한 타이밍 정보를 포함하고 있습니다. 주요 속성으로는 다음과 같습니다:

- `navigationStart`: 페이지 탐색 시작 시간.
- `unloadEventStart`: 이전 페이지의 unload 이벤트 시작 시간.
- `unloadEventEnd`: 이전 페이지의 unload 이벤트 종료 시간.
- `redirectStart`: 리디렉션 시작 시간.
- `redirectEnd`: 리디렉션 종료 시간.
- `fetchStart`: 리소스 요청 시작 시간.
- `domainLookupStart`: DNS 조회 시작 시간.
- `domainLookupEnd`: DNS 조회 종료 시간.
- `connectStart`: TCP 연결 시작 시간.
- `connectEnd`: TCP 연결 종료 시간.
- `requestStart`: HTTP 요청 시작 시간.
- `responseEnd`: HTTP 응답 종료 시간.
- `domLoading`: DOM 로딩 시작 시간.
- `domInteractive`: DOM 상호작용 가능 상태 도달 시간.
- `domContentLoadedEventStart`: DOMContentLoaded 이벤트 시작 시간.
- `domContentLoadedEventEnd`: DOMContentLoaded 이벤트 종료 시간.
- `loadEventStart`: 페이지 로드 이벤트 시작 시간.
- `loadEventEnd`: 페이지 로드 이벤트 종료 시간.

이 속성들은 웹 페이지의 성능을 분석하고 문제를 해결하는 데 필수적인 정보를 제공합니다.

## 예제
다음은 PerformanceTiming API를 사용하는 기본적인 예제입니다:

```javascript
window.addEventListener('load', function() {
    const timing = window.performance.timing;

    const pageLoadTime = timing.loadEventEnd - timing.navigationStart;
    console.log('페이지 로드 시간: ' + pageLoadTime + 'ms');

    const dnsLookupTime = timing.domainLookupEnd - timing.domainLookupStart;
    console.log('DNS 조회 시간: ' + dnsLookupTime + 'ms');
});
```

이 예제는 페이지가 로드된 후 전체 페이지 로드 시간과 DNS 조회 시간을 콘솔에 출력합니다.

## 설명
PerformanceTiming API를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **API 지원**: PerformanceTiming은 대부분의 최신 브라우저에서 지원되지만, 일부 구형 브라우저에서는 지원하지 않을 수 있습니다. 따라서 이를 사용할 때는 항상 브라우저 호환성을 확인해야 합니다.
- **타이밍 정확도**: 타이밍 정보는 브라우저와 네트워크 환경에 따라 달라질 수 있습니다. 따라서 결과를 해석할 때 이러한 변수를 고려해야 합니다.
- **복잡한 페이지**: 동적 콘텐츠 로딩이나 여러 리디렉션이 있는 페이지에서는 타이밍 정보가 복잡해질 수 있습니다. 적절한 분석을 위해 여러 속성을 함께 고려해야 합니다.

## 한 줄 요약
PerformanceTiming은 웹 페이지의 로드 시간 및 성능 메트릭을 측정하여 성능 최적화에 도움을 주는 JavaScript API입니다.