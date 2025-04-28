<!--
Meta Description: # JavaScript의 NaN: 정의 및 사용법 ## 개요 JavaScript에서 `NaN`(Not-a-Number)은 숫자가 아닌 값을 나타내는 특별한 값입니다. 주로 수학적 연산의 결과가 숫자가 아닐 때 사용되며, JavaScript의 타입 시스템에서 중요한 역할...
Meta Keywords: nan, number, 숫자가, 반환합니다, console
-->

# JavaScript의 NaN: 정의 및 사용법

## 개요
JavaScript에서 `NaN`(Not-a-Number)은 숫자가 아닌 값을 나타내는 특별한 값입니다. 주로 수학적 연산의 결과가 숫자가 아닐 때 사용되며, JavaScript의 타입 시스템에서 중요한 역할을 합니다.

## 문서화
### 목적
`NaN`은 수치 연산에서 오류가 발생했음을 나타내는 데 사용되며, 주로 다음과 같은 상황에서 발생합니다:
- 숫자가 아닌 값을 숫자로 변환할 때
- 수학적 연산이 정의되지 않을 때

### 사용법
`NaN`은 전역 객체인 `Number`의 속성으로 정의됩니다. `NaN`은 다음과 같은 경우에 발생할 수 있습니다:
- 0을 0으로 나누기: `0 / 0`은 `NaN`을 반환합니다.
- 문자를 숫자로 변환할 때: `Number("string")`은 `NaN`을 반환합니다.

#### 예시 코드
```javascript
console.log(0 / 0);         // NaN
console.log(Number("abc")); // NaN
console.log(Math.sqrt(-1)); // NaN
console.log(NaN === NaN);   // false
```

## 설명
### 일반적인 함정
- **NaN의 특성**: `NaN`은 자기 자신과 동등하지 않습니다. 즉, `NaN === NaN`은 `false`를 반환합니다. `NaN`을 판별하려면 `Number.isNaN()` 또는 `isNaN()` 함수를 사용해야 합니다.
- **전역적인 NaN**: `NaN`은 전역적으로 사용 가능하지만, `isNaN()` 함수는 입력값이 숫자형인지 확인 후, 숫자가 아닌 경우 `true`를 반환합니다. 이는 `null` 또는 `undefined`와 같은 값도 포함됩니다.

### 추가 사항
- `NaN`은 `typeof` 연산자를 사용하여 `number`로 식별됩니다. 이 점은 `NaN`이 숫자 타입임을 명확히 합니다.
- `NaN`은 프로그래밍에서 비교적 자주 발생하므로, 이를 예방하는 방법을 알고 있는 것이 중요합니다.

## 한 줄 요약
JavaScript에서 `NaN`은 수치 연산의 결과가 숫자가 아님을 나타내는 특별한 값으로, 오류 상황을 식별하는 데 유용합니다.