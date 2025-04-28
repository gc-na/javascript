<!--
Meta Description: # JavaScript의 isFinite 함수: 유한성 확인하기 ## 개요 `isFinite` 함수는 주어진 값이 유한한 숫자인지를 판별하는 데 사용됩니다. 이 함수는 숫자 이외의 값을 포함하여 다양한 데이터 타입에 대해 작동하며, 유한한 숫자(true)와 무한대 또는...
Meta Keywords: isfinite, false, true, console, log
-->

# JavaScript의 isFinite 함수: 유한성 확인하기

## 개요
`isFinite` 함수는 주어진 값이 유한한 숫자인지를 판별하는 데 사용됩니다. 이 함수는 숫자 이외의 값을 포함하여 다양한 데이터 타입에 대해 작동하며, 유한한 숫자(true)와 무한대 또는 NaN(false)를 구분합니다.

## 문서화
`isFinite`는 전역 함수로, JavaScript에서 다음과 같은 목적과 용도로 사용됩니다:

- **목적**: 주어진 값이 유한한 숫자인지 확인.
- **사용법**: `isFinite(value)`
  - `value`: 확인할 값. 숫자, 문자열, 불리언 등 다양한 타입을 입력받을 수 있습니다.
- **반환값**: 
  - 유한한 숫자일 경우 `true`를 반환합니다.
  - 무한대(`Infinity` 또는 `-Infinity`) 또는 `NaN`일 경우 `false`를 반환합니다.

## 예제
```javascript
console.log(isFinite(123));          // true
console.log(isFinite(-123));         // true
console.log(isFinite(0));            // true
console.log(isFinite(Infinity));     // false
console.log(isFinite(-Infinity));    // false
console.log(isFinite(NaN));          // false
console.log(isFinite("123"));        // true (문자열이 숫자로 변환됨)
console.log(isFinite("Hello"));      // false (문자열이 숫자로 변환될 수 없음)
```

## 설명
`isFinite` 함수는 특정 값이 유한한 숫자인지를 판단하는 데 유용하지만 몇 가지 주의해야 할 점이 있습니다:

1. **타입 변환**: `isFinite`는 입력값이 숫자가 아닐 경우, 암묵적으로 숫자 타입으로 변환합니다. 예를 들어, 문자열 "123"은 숫자 123으로 변환되어 `true`를 반환합니다. 그러나 "Hello"와 같이 숫자로 변환할 수 없는 문자열은 `false`를 반환합니다.

2. **NaN과 무한대**: `isFinite`는 NaN과 무한대에 대해서는 `false`를 반환합니다. 이러한 값들은 수학적으로 유한하지 않기 때문에 유의해야 합니다.

3. **전역 함수**: `isFinite`는 전역으로 제공되므로, 별도의 객체나 모듈을 통해 접근할 필요가 없습니다.

## 한 줄 요약
`isFinite` 함수는 주어진 값이 유한한 숫자인지를 확인하여, 유한한 경우 `true`, 그렇지 않은 경우 `false`를 반환하는 전역 함수입니다.