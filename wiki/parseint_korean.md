<!--
Meta Description: # JavaScript의 parseInt: 문자열을 정수로 변환하기 ## 개요 `parseInt`는 JavaScript에서 문자열을 정수로 변환하는 함수로, 숫자 문자열을 정수로 처리할 때 유용하게 사용됩니다. 이 함수는 문자열의 가장 앞부분에서부터 숫자를 파싱하며, ...
Meta Keywords: parseint, console, log, 정수로, 문자열을
-->

# JavaScript의 parseInt: 문자열을 정수로 변환하기

## 개요
`parseInt`는 JavaScript에서 문자열을 정수로 변환하는 함수로, 숫자 문자열을 정수로 처리할 때 유용하게 사용됩니다. 이 함수는 문자열의 가장 앞부분에서부터 숫자를 파싱하며, 선택적으로 진수를 지정할 수 있습니다.

## 문서화
### 목적
`parseInt` 함수는 문자열을 정수로 변환하는 데 사용됩니다. 주로 사용자 입력을 처리하거나 문자열로 된 숫자를 계산할 때 사용됩니다.

### 사용법
```javascript
parseInt(string, radix);
```

- **string**: 변환할 문자열. 숫자 형태의 문자열이어야 하며, 그 앞에 공백이 올 수 있습니다.
- **radix**: (선택적) 진수(2~36)를 지정하는 정수. 지정하지 않으면 기본값은 10입니다.

### 세부사항
- `parseInt`는 문자열의 첫 번째 문자가 숫자가 아닐 경우 `NaN`을 반환합니다.
- 반환값은 정수이며, 소수점 이하 숫자는 무시됩니다.
- `radix`를 지정하지 않으면, 문자열이 '0x'로 시작하면 16진수로, '0'으로 시작하면 8진수로 인식할 수 있습니다. 나머지는 10진수로 처리됩니다.

## 예제
### 기본 사용 예제
```javascript
console.log(parseInt("123"));    // 123
console.log(parseInt("  456"));  // 456
console.log(parseInt("789abc"));  // 789
console.log(parseInt("abc789"));  // NaN
```

### 진수 지정 예제
```javascript
console.log(parseInt("11", 2));  // 3 (2진수)
console.log(parseInt("11", 8));  // 9 (8진수)
console.log(parseInt("11", 10)); // 11 (10진수)
console.log(parseInt("11", 16)); // 17 (16진수)
```

## 설명
`parseInt`를 사용할 때 주의해야 할 점은 입력 문자열이 숫자로 시작하지 않는 경우 `NaN`을 반환한다는 것입니다. 또한, `radix`를 지정하지 않으면, 문자열의 형식에 따라 해석이 달라질 수 있으므로, 항상 진수를 명시하는 것이 좋습니다. 마지막으로, 소수점 이하 숫자는 무시되므로, 정수로 변환하고자 할 경우 주의가 필요합니다.

## 한 줄 요약
`parseInt`는 문자열을 정수로 변환하는 JavaScript 함수로, 선택적으로 진수를 지정할 수 있습니다.