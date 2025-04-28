<!--
Meta Description: # JavaScript의 "undefined": 정의 및 사용법 ## 개요 JavaScript에서 "undefined"는 변수나 객체의 속성이 정의되지 않았음을 나타내는 특별한 값입니다. "undefined"는 변수에 값이 할당되지 않았거나, 함수가 값을 반환하지 않을...
Meta Keywords: undefined, 함수가, console, log, javascript에서
-->

# JavaScript의 "undefined": 정의 및 사용법

## 개요
JavaScript에서 "undefined"는 변수나 객체의 속성이 정의되지 않았음을 나타내는 특별한 값입니다. "undefined"는 변수에 값이 할당되지 않았거나, 함수가 값을 반환하지 않을 때 기본적으로 자동으로 할당됩니다.

## 문서화
### 목적
"undefined"는 JavaScript에서 중요한 데이터 유형 중 하나로, 프로그램의 흐름과 변수의 상태를 이해하는 데 필수적입니다. 이 값은 주로 변수의 초기화 여부를 판단하거나, 함수가 반환하는 값의 존재 여부를 확인하는 데 사용됩니다.

### 사용법
- 변수 선언 후 값을 할당하지 않으면 기본적으로 "undefined" 값이 할당됩니다.
- 객체에서 존재하지 않는 속성에 접근할 경우 "undefined"가 반환됩니다.
- 함수가 아무런 값을 반환하지 않을 때, 호출 시 "undefined"가 반환됩니다.

### 세부 사항
"undefined"는 원시 데이터 타입 중 하나로, JavaScript의 모든 타입과 호환됩니다. "undefined"는 다음과 같은 경우에 발생할 수 있습니다:
- 변수 선언 후 초기화 하지 않은 경우
- 객체에서 정의되지 않은 속성에 접근한 경우
- 함수가 반환문 없이 종료된 경우

## 예제
```javascript
// 1. 변수 선언 후 초기화하지 않음
let a;
console.log(a); // 출력: undefined

// 2. 객체에서 정의되지 않은 속성 접근
let obj = { name: "John" };
console.log(obj.age); // 출력: undefined

// 3. 함수에서 반환값이 없음
function greet() {
    console.log("Hello!");
}
let result = greet(); // 출력: Hello!
console.log(result); // 출력: undefined
```

## 설명
"undefined"는 종종 혼란을 초래할 수 있습니다. 예를 들어, 변수가 "undefined"인지 실제로 값이 존재하는지를 구별하는 것이 중요합니다. "undefined"는 falsy 값으로, 조건문에서 false로 평가됩니다. 그러나 "null", "NaN", 빈 문자열("")과 같은 다른 falsy 값과 혼동되지 않도록 주의해야 합니다. 

일반적인 실수 중 하나는 변수를 초기화하지 않고 사용하여 "undefined" 값을 기대하는 것입니다. 이는 디버깅 시 혼란을 초래할 수 있으므로 항상 변수를 선언한 후 초기화하는 것이 좋습니다.

## 한 줄 요약
JavaScript에서 "undefined"는 변수가 값이 할당되지 않았거나 존재하지 않는 속성을 나타내는 특별한 값입니다.