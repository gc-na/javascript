<!--
Meta Description: # PerformanceObserverEntryList: 자바스크립트 성능 관찰을 위한 리스트 ## 개요 `PerformanceObserverEntryList`는 웹 애플리케이션의 성능 데이터를 수집하고 분석하기 위해 사용되는 객체입니다. 이 객체는 `Performan...
Meta Keywords: performanceobserverentrylist, performanceobserver, observer, 있습니다, 반환합니다
-->

# PerformanceObserverEntryList: 자바스크립트 성능 관찰을 위한 리스트

## 개요
`PerformanceObserverEntryList`는 웹 애플리케이션의 성능 데이터를 수집하고 분석하기 위해 사용되는 객체입니다. 이 객체는 `PerformanceObserver` API와 함께 사용되며, 성능 이벤트의 목록을 제공하여 개발자가 애플리케이션의 성능을 모니터링하고 최적화하는 데 도움을 줍니다.

## 문서화

### 목적
`PerformanceObserverEntryList` 객체는 특정 성능 관찰자(Performance Observer)가 수집한 성능 관련 정보를 담고 있습니다. 이 객체를 통해 다양한 성능 이벤트에 대한 세부 사항에 접근할 수 있습니다.

### 사용법
`PerformanceObserverEntryList`는 `PerformanceObserver`에서 수집된 엔트리들을 배열처럼 다룰 수 있도록 해줍니다. 배열 메서드와 유사한 방법으로 엔트리에 접근하고, 필터링할 수 있습니다.

**생성 방법:**
`PerformanceObserver`를 사용하여 성능 데이터를 수집하고, `getEntries()` 메서드를 호출하여 `PerformanceObserverEntryList`를 얻습니다.

### 세부사항
- **속성**:
  - `length`: 리스트 내의 항목 수를 반환합니다.
  
- **메서드**:
  - `getEntries()`: 모든 성능 항목을 반환합니다.
  - `getEntriesByName(name)`: 특정 이름을 가진 성능 항목만 반환합니다.
  - `getEntriesByType(type)`: 특정 타입의 성능 항목만 반환합니다.

## 예제

### 기본 사용법
```javascript
const observer = new PerformanceObserver((list) => {
    const entries = list.getEntries();
    entries.forEach(entry => {
        console.log(`${entry.name}: ${entry.startTime} - ${entry.duration}`);
    });
});

// 성능 이벤트 관찰 시작
observer.observe({ entryTypes: ['mark', 'measure'] });

// 마크와 측정을 기록
performance.mark('start');
// ... 코드 실행 ...
performance.measure('myMeasure', 'start');
```

### 특정 엔트리 가져오기
```javascript
const observer = new PerformanceObserver((list) => {
    const entries = list.getEntriesByType('measure');
    console.log(entries);
});

observer.observe({ entryTypes: ['measure'] });
```

## 설명
`PerformanceObserverEntryList`를 사용할 때 주의해야 할 점은 성능 이벤트가 발생하기 전에 관찰자를 등록해야 한다는 것입니다. 그렇지 않으면 해당 이벤트를 놓칠 수 있습니다. 또한, 성능 데이터는 비동기적으로 수집되므로, 데이터가 수집되기 전에 접근할 경우 빈 리스트가 반환될 수 있습니다.

## 한 줄 요약
`PerformanceObserverEntryList`는 웹 성능 이벤트를 수집하여 분석하는 데 사용되는 객체로, 성능 최적화를 위한 중요한 도구입니다.