<!--
Meta Description: # JavaScript의 length: 배열 및 문자열의 길이 확인하기 ## 개요 JavaScript에서 `length`는 배열이나 문자열의 요소 수 또는 문자 수를 반환하는 속성입니다. 이 속성은 데이터 구조의 크기를 확인하는 데 유용하며, 반복문이나 조건문 등 다양...
Meta Keywords: length, 문자열의, 배열의, let, console
-->

# JavaScript의 length: 배열 및 문자열의 길이 확인하기

## 개요
JavaScript에서 `length`는 배열이나 문자열의 요소 수 또는 문자 수를 반환하는 속성입니다. 이 속성은 데이터 구조의 크기를 확인하는 데 유용하며, 반복문이나 조건문 등 다양한 상황에서 활용될 수 있습니다.

## 문서화

### 목적
`length` 속성은 배열이나 문자열의 길이를 쉽게 확인할 수 있게 해주며, 특히 데이터 조작이나 검증에 필수적인 요소입니다.

### 사용법
- **문자열**: 문자열의 길이를 반환합니다.
- **배열**: 배열의 요소 개수를 반환합니다.

```javascript
// 문자열 예제
let str = "안녕하세요";
console.log(str.length); // 5

// 배열 예제
let arr = [1, 2, 3, 4, 5];
console.log(arr.length); // 5
```

### 세부사항
- `length`는 0부터 시작하는 인덱스와는 달리, 데이터 구조의 총 요소 수를 반환합니다.
- 문자열의 경우, 공백도 문자로 간주되어 길이에 포함됩니다.
- 배열의 경우, 정의된 요소 수만 반영되며, 빈 요소는 카운트되지 않습니다.

## 예제

```javascript
// 문자열 길이 확인
let greeting = "안녕하세요!";
console.log(greeting.length); // 6

// 배열 길이 확인
let fruits = ["사과", "바나나", "체리"];
console.log(fruits.length); // 3

// 빈 문자열과 배열
let emptyString = "";
let emptyArray = [];
console.log(emptyString.length); // 0
console.log(emptyArray.length); // 0
```

## 설명
`length` 속성을 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **문자열과 배열의 차이**: 문자열의 경우, `length`는 문자의 개수를 반환하며, 배열은 요소의 개수를 반환합니다. 이 두 가지는 동일한 속성이지만, 반환 값이 다를 수 있습니다.
   
2. **변경 가능성**: 배열의 경우, 요소가 추가되거나 삭제되면 `length` 값이 자동으로 업데이트되지만, 문자열은 immutable(불변)하여 수정할 수 없습니다.

3. **비어 있는 경우**: 빈 문자열이나 빈 배열의 경우 `length`는 항상 0입니다.

## 한 줄 요약
JavaScript의 `length` 속성은 문자열과 배열의 요소 수를 확인하는 데 사용됩니다.