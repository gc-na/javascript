<!--
Meta Description: # JavaScript의 불리언(Boolean): 기본 개념과 활용 방법 ## 개요 JavaScript에서 불리언(Boolean)은 참(true) 또는 거짓(false)의 두 가지 값을 가질 수 있는 데이터 타입입니다. 프로그래밍에서 조건문, 반복문 등에서 중요한 역할...
Meta Keywords: 불리언, true, false, 있습니다, console
-->

# JavaScript의 불리언(Boolean): 기본 개념과 활용 방법

## 개요
JavaScript에서 불리언(Boolean)은 참(true) 또는 거짓(false)의 두 가지 값을 가질 수 있는 데이터 타입입니다. 프로그래밍에서 조건문, 반복문 등에서 중요한 역할을 하며, 프로그램의 흐름을 제어하는 데 필수적입니다.

## 문서화

### 목적
불리언 데이터 타입은 조건을 평가하고 논리적 결정을 내리는 데 사용되며, 이를 통해 다양한 제어 구조를 구현할 수 있습니다.

### 사용법
JavaScript에서 불리언 값은 다음과 같이 생성할 수 있습니다:
- 직접 지정: `true` 또는 `false`를 사용하여 불리언 값을 직접 지정할 수 있습니다.
- 비교 연산자: `==`, `===`, `!=`, `!==`, `<`, `>`, `<=`, `>=` 등을 사용하여 두 값을 비교하고 불리언 결과를 반환받을 수 있습니다.
- 논리 연산자: `&&`(AND), `||`(OR), `!`(NOT)을 사용하여 복합적인 조건을 평가할 수 있습니다.

### 세부 사항
불리언 타입은 JavaScript의 기본 데이터 타입 중 하나로, 다른 데이터 타입인 숫자(Number), 문자열(String), 객체(Object)와 함께 사용됩니다. 불리언 값은 제어 구조(예: `if`, `while`, `for`)에서 조건을 평가하는 데 사용되며, 이로 인해 프로그램의 흐름을 결정짓는 중요한 역할을 합니다.

## 예시

### 기본 사용 예제
```javascript
let isActive = true;
let isCompleted = false;

// 조건문에서의 사용
if (isActive) {
    console.log("활성 상태입니다.");
} else {
    console.log("비활성 상태입니다.");
}

// 비교 연산자 사용 예
let number = 10;
console.log(number > 5); // true
console.log(number < 5); // false
```

### 논리 연산자 사용 예
```javascript
let isLoggedIn = true;
let isAdmin = false;

if (isLoggedIn && isAdmin) {
    console.log("관리자 권한이 있는 사용자입니다.");
} else {
    console.log("관리자 권한이 없습니다.");
}
```

## 설명
불리언을 사용할 때 주의해야 할 점은, JavaScript에서 불리언 값으로 평가되는 "truthy"와 "falsy" 값이 있다는 것입니다. 예를 들어, `0`, `""`(빈 문자열), `null`, `undefined`, `NaN`은 모두 falsy로 평가되며, 그 외의 값들은 truthy로 평가됩니다. 이러한 특성을 이해하지 못하면 조건문에서 예상치 못한 결과를 초래할 수 있습니다.

## 한 줄 요약
JavaScript에서 불리언은 참(true) 또는 거짓(false) 값을 가지며, 조건 평가 및 프로그램 흐름 제어에 필수적인 데이터 타입입니다.