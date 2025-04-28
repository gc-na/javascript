<!--
Meta Description: # PerformanceMeasure: 자바스크립트 성능 측정 기법 ## 개요 PerformanceMeasure는 웹 애플리케이션의 성능을 측정하고 분석하기 위한 API로, 특정 코드 블록이 실행되는 시간을 측정하여 성능 최적화에 도움을 줍니다. ## 문서 ### 목적...
Meta Keywords: performance, mark, 성능을, 시간을, 있습니다
-->

# PerformanceMeasure: 자바스크립트 성능 측정 기법

## 개요
PerformanceMeasure는 웹 애플리케이션의 성능을 측정하고 분석하기 위한 API로, 특정 코드 블록이 실행되는 시간을 측정하여 성능 최적화에 도움을 줍니다.

## 문서
### 목적
PerformanceMeasure API는 웹 페이지의 성능을 세밀하게 분석할 수 있도록 특정 코드 블록의 실행 시간을 측정하는 기능을 제공합니다. 이를 통해 개발자들은 성능 병목 지점을 식별하고 개선할 수 있습니다.

### 사용법
PerformanceMeasure를 사용하기 위해서는 Performance API의 일부로 `performance.mark()`와 `performance.measure()` 메소드를 함께 활용해야 합니다. 다음은 기본적인 사용 흐름입니다:

1. **성능 마크 설정**: `performance.mark('start')`로 시작 마크를 설정합니다.
2. **코드 실행**: 성능을 측정할 코드 블록을 실행합니다.
3. **성능 마크 종료**: `performance.mark('end')`로 종료 마크를 설정합니다.
4. **성능 측정**: `performance.measure('measureName', 'start', 'end')`를 호출하여 두 마크 사이의 시간을 측정합니다.

### 예제
```javascript
// 1. 시작 마크 설정
performance.mark('start');

// 2. 성능을 측정할 코드 블록
for (let i = 0; i < 1000000; i++) {
    // 코드 실행
}

// 3. 종료 마크 설정
performance.mark('end');

// 4. 성능 측정
performance.measure('MyMeasure', 'start', 'end');

// 5. 측정 결과 확인
const measures = performance.getEntriesByName('MyMeasure');
console.log(measures[0].duration); // 측정된 시간 출력
```

## 설명
- **공통적인 실수**: 마크를 설정하기 전에 코드 블록을 실행하거나 마크를 잘못 설정하는 경우가 많습니다. 반드시 마크 순서가 올바른지 확인해야 합니다.
- **측정 결과의 수명**: 측정 결과는 성능 엔트리로 저장되며, `performance.clearMeasures()`를 통해 삭제할 수 있습니다.
- **브라우저 지원**: 대부분의 현대 브라우저에서 지원되지만, 특정 구형 브라우저에서는 지원되지 않을 수 있습니다.
- **성능 분석 도구**: 측정된 성능 데이터는 Chrome DevTools와 같은 도구를 사용하여 시각화하고 분석할 수 있습니다.

## 한줄 요약
PerformanceMeasure는 자바스크립트 코드의 실행 시간을 측정하여 성능 최적화를 지원하는 API입니다.