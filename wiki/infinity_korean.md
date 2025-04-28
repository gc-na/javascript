<!--
Meta Description: # 자바스크립트의 Infinity: 무한대의 이해와 활용 ## 개요 자바스크립트에서 `Infinity`는 수학적 무한대를 나타내는 특수한 숫자 값으로, 수치 계산 및 비교에 유용하게 사용됩니다. 무한대를 이해하고 활용하는 것은 프로그래밍에서 매우 중요한 개념입니다. #...
Meta Keywords: infinity, console, log, let, 무한대
-->

# 자바스크립트의 Infinity: 무한대의 이해와 활용

## 개요
자바스크립트에서 `Infinity`는 수학적 무한대를 나타내는 특수한 숫자 값으로, 수치 계산 및 비교에 유용하게 사용됩니다. 무한대를 이해하고 활용하는 것은 프로그래밍에서 매우 중요한 개념입니다.

## 문서화
### 목적
`Infinity`는 자바스크립트에서 가장 큰 수를 의미하며, 양의 무한대로 표현됩니다. 이는 수학적 개념으로, 특정한 수치 연산의 결과가 무한대일 때 사용됩니다.

### 사용법
`Infinity`는 전역 객체의 속성으로 사용되며, 직접 생성할 수는 없습니다. 다음과 같은 경우에 주로 활용합니다:

1. 수치 연산 결과가 무한대일 때
2. 비교 연산에서 최대값을 설정할 때
3. 오류 처리 및 경계 조건을 확인할 때

```javascript
console.log(Infinity); // 무한대 출력
console.log(1 / 0);    // 무한대의 예: 1을 0으로 나누면 Infinity
console.log(-1 / 0);   // -Infinity: 음의 무한대
```

## 예제
### 기본 사용 예
```javascript
let positiveInfinity = Infinity; // 양의 무한대
let negativeInfinity = -Infinity; // 음의 무한대

console.log(positiveInfinity); // Infinity
console.log(negativeInfinity); // -Infinity

console.log(positiveInfinity > 1000); // true
console.log(negativeInfinity < -1000); // true

let result = 10 / 0; // 10을 0으로 나누면 Infinity
console.log(result); // Infinity
```

### 배열 및 Infinity
```javascript
let numbers = [1, 2, 3, Infinity, 5];
let max = Math.max(...numbers); // 배열에서 최대값 찾기
console.log(max); // Infinity
```

## 설명
- **공통적인 오류 및 주의사항**: `Infinity`와 관련된 수치 연산에서 유의해야 할 점은, `Infinity`와 어떤 수를 곱하거나 더하면 항상 `Infinity`가 된다는 것입니다. 예를 들어, `Infinity + 1000`의 결과는 여전히 `Infinity`입니다.
  
- **자료형**: `Infinity`는 숫자 타입의 값으로, 다른 숫자와의 비교에서 항상 가장 큰 값으로 취급됩니다.

- **NaN과의 구분**: `Infinity`는 'Not a Number'(`NaN`)와는 다른 개념입니다. `NaN`은 수치 연산이 유효하지 않을 때 발생하며, `Infinity`는 유효한 수치 연산의 결과입니다.

## 한 문장 요약
자바스크립트에서 `Infinity`는 수학적 무한대를 나타내며, 수치 연산 및 비교에서 유용하게 활용되는 특수 숫자 값입니다.