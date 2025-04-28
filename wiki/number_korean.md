<!--
Meta Description: # JavaScript에서의 Number: 숫자 데이터 타입에 대한 완벽 가이드 ## 개요 JavaScript의 `Number`는 숫자 데이터를 저장하고 조작하는 데 사용되는 기본 데이터 타입으로, 정수와 실수를 모두 포함합니다. `Number`는 다양한 수학적 연산을...
Meta Keywords: number, let, javascript, 있습니다, 숫자를
-->

# JavaScript에서의 Number: 숫자 데이터 타입에 대한 완벽 가이드

## 개요
JavaScript의 `Number`는 숫자 데이터를 저장하고 조작하는 데 사용되는 기본 데이터 타입으로, 정수와 실수를 모두 포함합니다. `Number`는 다양한 수학적 연산을 수행할 수 있는 메서드를 제공합니다.

## 문서화

### 목적
JavaScript의 `Number`는 수치 연산을 수행하기 위한 기본 단위로, 프로그래밍에서 수치를 다룰 때 필수적으로 사용됩니다. `Number`는 IEEE 754 표준을 따르는 64비트 부동 소수점 형식으로 구현됩니다.

### 사용법
JavaScript에서 `Number`는 내장된 생성자 함수로 사용되며, 다음과 같은 방법으로 숫자를 정의할 수 있습니다:

1. **리터럴 사용**: 직접 숫자를 코딩
   ```javascript
   let num1 = 42; // 정수
   let num2 = 3.14; // 실수
   ```

2. **Number() 생성자 사용**: 문자열을 숫자로 변환
   ```javascript
   let num3 = Number("123"); // 123
   let num4 = Number("123.45"); // 123.45
   ```

### 세부사항
- **특수 값**: `Number`는 `Infinity`, `-Infinity`, `NaN`(Not a Number)와 같은 특수 값을 포함합니다.
- **정수 및 실수**: JavaScript는 모든 숫자를 `Number` 타입으로 저장하므로 정수와 실수의 구분이 없습니다.
- **정밀도**: `Number`는 15-17자리의 십진수 정밀도를 가집니다. 그 이상의 숫자는 근사값으로 저장될 수 있습니다.

## 예제
### 기본 사용 예
```javascript
// 숫자 리터럴
let a = 10;
let b = 20;

// 덧셈
let sum = a + b; // 30

// 실수
let c = 5.5;
let d = 2.2;

// 곱셈
let product = c * d; // 12.1
```

### 문자열을 숫자로 변환하기
```javascript
let strNumber = "100";
let numFromString = Number(strNumber); // 100
```

## 설명
`Number` 타입을 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **정밀도 손실**: 큰 숫자 또는 소수점이 많은 숫자를 사용할 때 정밀도 손실이 발생할 수 있습니다.
   ```javascript
   console.log(0.1 + 0.2); // 0.30000000000000004
   ```

2. **NaN 처리**: `NaN`은 숫자가 아닌 값을 나타내며, 이를 처리할 때는 `isNaN()` 함수를 사용할 수 있습니다.
   ```javascript
   console.log(isNaN(NaN)); // true
   ```

3. **연산자 오버로드**: `Number`는 `+` 연산자가 문자열과 결합될 때 문자열 연결로 작동할 수 있으므로 주의가 필요합니다.
   ```javascript
   let result = 5 + "5"; // "55"
   ```

## 한 줄 요약
JavaScript의 `Number`는 정수와 실수를 포함하며 수치 연산을 수행하는 데 사용되는 기본 데이터 타입입니다.