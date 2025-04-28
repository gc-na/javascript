<!--
Meta Description: # decodeURIComponent: JavaScript에서 URL 인코딩된 문자열을 디코딩하는 방법 ## 개요 `decodeURIComponent`는 JavaScript에서 URL 인코딩된 문자열을 디코딩하는 데 사용되는 내장 함수입니다. 이 함수는 특수 문자와 공...
Meta Keywords: decodeuricomponent, 인코딩된, javascript, 문자열을, const
-->

# decodeURIComponent: JavaScript에서 URL 인코딩된 문자열을 디코딩하는 방법

## 개요
`decodeURIComponent`는 JavaScript에서 URL 인코딩된 문자열을 디코딩하는 데 사용되는 내장 함수입니다. 이 함수는 특수 문자와 공백을 포함한 URI 구성 요소의 값을 복원하는 데 매우 유용합니다.

## 문서화
### 목적
`decodeURIComponent` 함수는 URI 구성 요소에서 인코딩된 문자열을 원래의 형태로 변환합니다. 예를 들어, 공백은 `%20`으로 인코딩되고, 특수 문자는 다른 코드로 인코딩됩니다. 이 함수를 사용하면 이러한 인코딩을 쉽게 복원할 수 있습니다.

### 사용법
`decodeURIComponent` 함수의 기본 사용법은 다음과 같습니다:

```javascript
decodeURIComponent(encodedURI)
```

- `encodedURI`: 디코딩할 URL 인코딩된 문자열입니다. 이 문자열은 반드시 올바른 URI 인코딩을 따라야 합니다.

### 세부사항
- `decodeURIComponent`는 인코딩된 문자열을 해석하여, 원래 문자로 변환합니다.
- 인코딩된 문자열에 잘못된 형식이 포함되어 있으면 `URIError`가 발생합니다.
- 이 함수는 URI에서 사용할 수 있는 모든 문자에 대해 작동하며, 공백, 특수 문자 및 비 ASCII 문자를 포함합니다.

## 예제
다음은 `decodeURIComponent`의 기본적인 사용 예입니다.

### 예제 1: 간단한 디코딩
```javascript
const encodedStr = "Hello%20World%21";
const decodedStr = decodeURIComponent(encodedStr);
console.log(decodedStr); // 출력: Hello World!
```

### 예제 2: 복잡한 문자열 디코딩
```javascript
const encodedStr = "JavaScript%20%26%20Web%20Development";
const decodedStr = decodeURIComponent(encodedStr);
console.log(decodedStr); // 출력: JavaScript & Web Development
```

### 예제 3: 비 ASCII 문자 디코딩
```javascript
const encodedStr = "%E2%9C%94";
const decodedStr = decodeURIComponent(encodedStr);
console.log(decodedStr); // 출력: ✔
```

## 설명
- **일반적인 문제점**: 인코딩된 문자열에 잘못된 형식이 포함되어 있을 경우 `URIError`가 발생할 수 있습니다. 예를 들어, `%` 뒤에 두 자리의 16진수 숫자가 없으면 오류가 발생합니다.
  
  ```javascript
  try {
      decodeURIComponent("Hello%20World%2");
  } catch (e) {
      console.error(e); // URIError: URI malformed
  }
  ```

- **인코딩된 문자열의 올바른 형식**: `decodeURIComponent`를 사용하기 전에 문자열이 올바르게 인코딩되었는지 확인하는 것이 중요합니다. 일반적으로 `encodeURIComponent`로 인코딩된 문자열을 디코딩하는 데 사용됩니다.

## 한 줄 요약
`decodeURIComponent`는 JavaScript에서 URL 인코딩된 문자열을 원래의 문자로 변환하는 함수입니다.