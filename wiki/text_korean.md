<!--
Meta Description: # JavaScript의 텍스트 처리: 문자열과 관련된 기능 ## 개요 JavaScript에서 "텍스트"는 주로 문자열(String) 데이터 타입과 관련이 있습니다. 문자열은 문자들의 시퀀스로, 텍스트 데이터를 표현하고 조작하는 데 중요한 역할을 합니다. 이 문서에서는...
Meta Keywords: text, 있습니다, 문자열은, hello, console
-->

# JavaScript의 텍스트 처리: 문자열과 관련된 기능

## 개요
JavaScript에서 "텍스트"는 주로 문자열(String) 데이터 타입과 관련이 있습니다. 문자열은 문자들의 시퀀스로, 텍스트 데이터를 표현하고 조작하는 데 중요한 역할을 합니다. 이 문서에서는 JavaScript에서 문자열을 처리하는 다양한 방법과 기능을 설명합니다.

## 문서화

### 목적
JavaScript에서 문자열은 텍스트 데이터를 저장하고 조작하는 기본적인 방법입니다. 문자열은 다양한 메서드를 통해 생성, 수정, 검색 및 변환할 수 있습니다.

### 사용법
문자열은 큰따옴표(`"`), 작은따옴표(`'`), 또는 백틱(``` ` ```)을 사용하여 생성할 수 있습니다. 

```javascript
let str1 = "안녕하세요";
let str2 = 'JavaScript';
let str3 = `오늘은 ${str2}를 배우고 있습니다.`;
```

### 주요 메서드
- `length`: 문자열의 길이를 반환합니다.
- `charAt(index)`: 주어진 인덱스에 있는 문자를 반환합니다.
- `indexOf(searchValue)`: 특정 문자열이 처음 나타나는 인덱스를 반환합니다.
- `slice(start, end)`: 문자열의 특정 부분을 잘라냅니다.
- `toUpperCase()`: 문자열을 대문자로 변환합니다.
- `toLowerCase()`: 문자열을 소문자로 변환합니다.

## 예제

```javascript
let text = "Hello, World!";

// 문자열 길이
console.log(text.length); // 13

// 특정 문자 가져오기
console.log(text.charAt(0)); // H

// 특정 문자열의 인덱스 찾기
console.log(text.indexOf("World")); // 7

// 문자열 잘라내기
console.log(text.slice(0, 5)); // Hello

// 대문자 변환
console.log(text.toUpperCase()); // HELLO, WORLD!

// 소문자 변환
console.log(text.toLowerCase()); // hello, world!
```

## 설명
문자열을 다룰 때 주의해야 할 점은 문자열은 불변(immutable)하다는 것입니다. 즉, 문자열을 수정하면 새로운 문자열이 생성되고 기존 문자열은 변경되지 않습니다. 또한, 인덱스는 0부터 시작하며, 잘못된 인덱스를 사용할 경우 `undefined`가 반환될 수 있습니다. 

특정 메서드에서는 대소문자 구분이 있으므로, 문자열 검색 시 이러한 점을 고려해야 합니다. 예를 들어, `indexOf` 메서드는 대소문자를 구분하므로 "hello"와 "Hello"는 서로 다른 문자열로 취급됩니다.

## 한 줄 요약
JavaScript에서 텍스트(문자열)는 문자들의 시퀀스를 표현하며, 다양한 메서드를 통해 조작할 수 있습니다.