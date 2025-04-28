<!--
Meta Description: # JavaScript의 문자열(String) 사용법과 특징 ## 개요 JavaScript에서 문자열(String)은 문자들의 집합으로, 텍스트를 다루는 데 사용되는 기본 데이터 타입입니다. 문자열은 다양한 메서드와 속성을 제공하여 텍스트 조작, 검색 및 변환을 용이하...
Meta Keywords: let, 문자열을, 문자열, 문자열은, 안녕하세요
-->

# JavaScript의 문자열(String) 사용법과 특징

## 개요
JavaScript에서 문자열(String)은 문자들의 집합으로, 텍스트를 다루는 데 사용되는 기본 데이터 타입입니다. 문자열은 다양한 메서드와 속성을 제공하여 텍스트 조작, 검색 및 변환을 용이하게 합니다.

## 문서화

### 목적
문자열은 웹 개발에서 사용자 입력, 데이터 출력, 텍스트 처리 등 다양한 용도로 사용됩니다. JavaScript의 문자열은 불변(immutable)이며, 즉 한 번 생성된 문자열은 변경할 수 없습니다.

### 사용법
문자열은 작은따옴표(`'`), 큰따옴표(`"`), 또는 백틱(``` ` ```)으로 정의할 수 있습니다. 각 기호는 약간의 차이가 있으며, 특히 백틱은 템플릿 리터럴을 사용하여 다중 행 문자열 및 문자열 보간을 지원합니다.

#### 문자열 생성 예:
```javascript
let singleQuoteString = '안녕하세요';
let doubleQuoteString = "안녕하세요";
let templateLiteralString = `안녕하세요`;
```

### 문자열 메서드
JavaScript의 문자열 객체는 여러 유용한 메서드를 제공합니다. 주요 메서드에는 다음이 포함됩니다:

- `length`: 문자열의 길이를 반환합니다.
- `charAt(index)`: 주어진 인덱스의 문자를 반환합니다.
- `substring(start, end)`: 주어진 인덱스 범위의 문자열을 반환합니다.
- `toUpperCase()`: 문자열을 대문자로 변환합니다.
- `toLowerCase()`: 문자열을 소문자로 변환합니다.
- `includes(searchString)`: 문자열이 지정한 값을 포함하는지 여부를 반환합니다.

## 예제
```javascript
let greeting = "안녕하세요";
console.log(greeting.length); // 6
console.log(greeting.charAt(0)); // '안'
console.log(greeting.toUpperCase()); // '안녕하세요'
console.log(greeting.includes("녕")); // true
```

## 설명
문자열을 다룰 때 주의해야 할 몇 가지 점이 있습니다:

1. **불변성**: 문자열은 불변이므로, 문자열을 수정하는 메서드는 원래 문자열을 변경하지 않고 새로운 문자열을 반환합니다.
   
   예:
   ```javascript
   let original = "Hello";
   let modified = original.toUpperCase();
   console.log(original); // "Hello"
   console.log(modified); // "HELLO"
   ```

2. **인덱스**: 문자열의 인덱스는 0부터 시작합니다. 따라서 `charAt(0)`은 첫 번째 문자를 반환합니다.

3. **템플릿 리터럴**: 백틱(``` ` ```)을 사용하여 문자열을 정의하면, 변수와 표현식을 포함할 수 있습니다.
   ```javascript
   let name = "홍길동";
   let welcomeMessage = `안녕하세요, ${name}!`;
   console.log(welcomeMessage); // "안녕하세요, 홍길동!"
   ```

## 한 줄 요약
JavaScript의 문자열은 문자들의 집합으로, 다양한 메서드를 통해 텍스트를 쉽게 다룰 수 있는 데이터 타입입니다.