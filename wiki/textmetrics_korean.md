<!--
Meta Description: # JavaScript TextMetrics: 텍스트 측정의 이해와 활용 ## 개요 JavaScript의 TextMetrics는 텍스트의 크기와 관련된 다양한 정보를 제공하는 객체로, 주로 HTML5의 Canvas API와 함께 사용됩니다. 이를 통해 텍스트의 폭, 높...
Meta Keywords: 텍스트의, 텍스트, textmetrics, 정보를, canvas
-->

# JavaScript TextMetrics: 텍스트 측정의 이해와 활용

## 개요
JavaScript의 TextMetrics는 텍스트의 크기와 관련된 다양한 정보를 제공하는 객체로, 주로 HTML5의 Canvas API와 함께 사용됩니다. 이를 통해 텍스트의 폭, 높이 등 측정치를 얻을 수 있어 웹 애플리케이션에서 텍스트 레이아웃을 조정하는 데 유용합니다.

## 문서화

### 목적
TextMetrics는 특정 텍스트 문자열의 측정 정보를 제공하여, 개발자가 텍스트가 차지하는 공간을 정확히 계산할 수 있도록 돕습니다. 이는 특히 동적으로 텍스트를 렌더링하는 경우에 중요합니다.

### 사용법
TextMetrics 객체는 `CanvasRenderingContext2D.measureText()` 메서드를 통해 생성됩니다. 이 메서드는 주어진 문자열과 현재 설정된 글꼴에 대한 측정 정보를 반환합니다.

### 세부사항
- **속성**: TextMetrics 객체에는 다음과 같은 속성이 포함됩니다:
  - `width`: 텍스트가 차지하는 가로 길이.
  - `actualBoundingBoxAscent`: 텍스트의 실제 경계 상단 높이.
  - `actualBoundingBoxDescent`: 텍스트의 실제 경계 하단 깊이.
  - `emHeightAscent`: 글꼴의 em 박스 상단 높이.
  - `emHeightDescent`: 글꼴의 em 박스 하단 깊이.
  - `hangingBaseline`: 텍스트의 걸리는 기준선.
  - `alphabeticBaseline`: 알파벳 기준선.

## 예제

```javascript
// 캔버스 생성 및 컨텍스트 가져오기
const canvas = document.createElement('canvas');
const context = canvas.getContext('2d');

// 글꼴 설정
context.font = '16px Arial';

// 텍스트 측정
const text = 'Hello, World!';
const metrics = context.measureText(text);

// 측정 결과 출력
console.log(`Text width: ${metrics.width}px`);
console.log(`Actual Bounding Box Ascent: ${metrics.actualBoundingBoxAscent}px`);
console.log(`Actual Bounding Box Descent: ${metrics.actualBoundingBoxDescent}px`);
```

## 설명
TextMetrics 사용 시 주의해야 할 점은 다음과 같습니다:
- **글꼴 설정**: `measureText`를 호출하기 전에 반드시 글꼴을 설정해야 합니다. 글꼴이 설정되지 않으면 예상치 못한 결과가 나올 수 있습니다.
- **스타일 차이**: 다양한 글꼴이나 스타일(예: 볼드, 이탤릭) 간의 측정 결과는 다를 수 있으므로, 필요에 따라 스타일을 변경해야 합니다.
- **캔버스 크기**: 캔버스의 크기와 비율이 텍스트의 렌더링에 영향을 미칠 수 있습니다. 적절한 크기로 설정하는 것이 중요합니다.

## 한 줄 요약
JavaScript의 TextMetrics는 텍스트의 크기와 경계 정보를 제공하여, 동적인 텍스트 레이아웃 관리를 용이하게 합니다.