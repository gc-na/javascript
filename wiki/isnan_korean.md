<!--
Meta Description: # JavaScript의 isNaN 함수: 사용법 및 예제 ## 개요 `isNaN`은 JavaScript에서 값이 NaN(Not-a-Number)인지 여부를 확인하는 함수입니다. 이 함수는 주어진 값이 숫자가 아닌 경우 true를 반환하며, 숫자인 경우 false를 반...
Meta Keywords: isnan, 함수는, console, log, 숫자로
-->

# JavaScript의 isNaN 함수: 사용법 및 예제

## 개요
`isNaN`은 JavaScript에서 값이 NaN(Not-a-Number)인지 여부를 확인하는 함수입니다. 이 함수는 주어진 값이 숫자가 아닌 경우 true를 반환하며, 숫자인 경우 false를 반환합니다. `isNaN`은 데이터 유효성 검증 및 오류 처리를 위한 필수 도구입니다.

## 문서화
### 목적
`isNaN` 함수는 주어진 인자가 숫자인지 아닌지를 판별하는 데 사용됩니다. 이 함수는 특히 사용자 입력값이 숫자로 변환 가능한지 확인할 때 유용합니다.

### 사용법
`isNaN` 함수는 다음과 같이 사용됩니다:

```javascript
isNaN(value);
```

- **value**: 확인할 값입니다. 이 값은 숫자, 문자열, 객체 등 다양한 데이터 타입이 될 수 있습니다.

### 세부 정보
- `isNaN`은 내부적으로 `Number` 함수와 함께 사용되어, 주어진 값이 NaN으로 평가되는지를 확인합니다.
- NaN은 JavaScript에서 "정의되지 않은 수치"를 나타내며, 어떤 수학적 연산에서 발생할 수 있습니다.
- `isNaN` 함수는 다음과 같은 방식으로 동작합니다:
  - 문자열, 객체 등을 숫자로 변환하려고 시도합니다.
  - 변환 결과가 NaN이면 true를 반환합니다.
  - 그렇지 않으면 false를 반환합니다.

## 예제
### 기본 사용법

```javascript
console.log(isNaN(NaN)); // true
console.log(isNaN(123)); // false
console.log(isNaN('123')); // false (문자열은 숫자로 변환됨)
console.log(isNaN('abc')); // true (숫자로 변환할 수 없음)
console.log(isNaN(undefined)); // true (undefined는 NaN으로 변환됨)
console.log(isNaN(null)); // false (null은 0으로 변환됨)
```

## 설명
`isNaN` 함수는 매우 유용하지만, 몇 가지 주의할 점이 있습니다:
- `isNaN`은 입력값을 숫자로 변환하려고 시도하므로, 숫자를 포함하는 문자열이 true로 평가되는 경우가 있습니다. 예를 들어, `isNaN('123')`는 false를 반환합니다.
- `isNaN`은 모든 객체와 배열을 검사할 때도 타입 변환을 시도하므로 예상치 못한 결과를 초래할 수 있습니다. 배열은 첫 번째 요소를 기준으로 변환되며, 비어 있는 배열은 0으로 변환됩니다.
- JavaScript에서는 `Number.isNaN` 메서드도 제공하며, 이는 값이 NaN인지 여부를 판별하면서 타입 변환을 수행하지 않기 때문에 더 엄격한 검사가 가능합니다.

## 한 줄 요약
`isNaN` 함수는 주어진 값이 NaN인지 여부를 확인하는 JavaScript의 유용한 도구입니다.