<!--
Meta Description: # PerformanceResourceTiming: JavaScript의 성능 측정 API ## 개요 `PerformanceResourceTiming`은 웹 애플리케이션의 리소스 로딩 성능을 측정하기 위한 API입니다. 이 인터페이스는 리소스의 로딩 시간을 정량화하여 ...
Meta Keywords: performanceresourcetiming, 리소스, 있습니다, resource, 리소스의
-->

# PerformanceResourceTiming: JavaScript의 성능 측정 API

## 개요
`PerformanceResourceTiming`은 웹 애플리케이션의 리소스 로딩 성능을 측정하기 위한 API입니다. 이 인터페이스는 리소스의 로딩 시간을 정량화하여 웹 개발자가 최적화를 할 수 있도록 돕습니다.

## 문서
### 목적
`PerformanceResourceTiming`은 웹 페이지에서 로드된 리소스(예: 이미지, 스크립트, 스타일시트 등)의 성능 데이터를 수집하고 분석하는 데 사용됩니다. 이를 통해 개발자는 각 리소스의 로딩 시간, DNS 조회 시간, 연결 시간 등을 파악할 수 있습니다.

### 사용법
`PerformanceResourceTiming` 객체는 `performance.getEntriesByType("resource")` 메서드를 사용하여 접근할 수 있습니다. 이 메서드는 로드된 리소스에 대한 정보를 포함하는 배열을 반환합니다.

### 세부사항
- **속성**: `PerformanceResourceTiming` 객체는 다음과 같은 주요 속성을 포함합니다:
  - `name`: 리소스의 URL.
  - `startTime`: 리소스 요청이 시작된 시점.
  - `responseEnd`: 서버의 응답이 완료된 시점.
  - `duration`: 전체 요청 및 응답에 소요된 시간.
  - `transferSize`: 전송된 데이터의 크기.
  
- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원되며, IE에서는 제한적 지원을 합니다.

## 예제
```javascript
// 리소스 타이밍 데이터 수집
const resources = performance.getEntriesByType("resource");

resources.forEach((resource) => {
    console.log(`리소스: ${resource.name}`);
    console.log(`로딩 시간: ${resource.duration} ms`);
});
```

## 설명
- **공통적인 함정**: `PerformanceResourceTiming` 객체는 모든 리소스 요청을 포함하지 않을 수 있습니다. 예를 들어, `Same-Origin Policy`에 의해 다른 도메인에서 로드된 리소스는 제한될 수 있습니다.
- **추가 노트**: 성능 데이터는 페이지가 완전히 로드된 후에 수집해야 하며, 그렇지 않으면 일부 데이터가 누락될 수 있습니다.

## 한 줄 요약
`PerformanceResourceTiming`은 웹 리소스의 로딩 성능을 측정하고 분석하는 데 유용한 API입니다.