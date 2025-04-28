<!--
Meta Description: # JavaScript의 escape 함수: 문자열 인코딩을 위한 필수 도구 ## 개요 JavaScript에서 `escape` 함수는 문자열 내의 특수 문자를 인코딩하여 URI(Uniform Resource Identifier)에서 안전하게 사용할 수 있도록 변환하는 ...
Meta Keywords: escape, 함수는, 문자를, 문자열, 안전하게
-->

# JavaScript의 escape 함수: 문자열 인코딩을 위한 필수 도구

## 개요
JavaScript에서 `escape` 함수는 문자열 내의 특수 문자를 인코딩하여 URI(Uniform Resource Identifier)에서 안전하게 사용할 수 있도록 변환하는 데 사용됩니다. 이 함수는 주로 URL이나 쿼리 문자열을 처리할 때 유용합니다.

## 문서화
### 목적
`escape` 함수는 주어진 문자열 내의 ASCII 문자를 제외한 모든 문자를 유니코드 형식으로 인코딩합니다. 이는 URL에 포함될 수 없는 문자를 안전하게 변환하여 웹에서 데이터를 전송할 수 있도록 돕습니다.

### 사용법
```javascript
escape(string);
```
- **매개변수**: 
  - `string` (필수): 인코딩할 문자열입니다.
  
- **반환값**: 
  - 입력된 문자열의 인코딩된 형태를 반환합니다.

### 세부사항
- `escape` 함수는 모든 비-ASCII 문자를 `%`와 그에 이어지는 2자리 16진수로 변환합니다.
- 이 함수는 더 이상 사용되지 않는 것으로 권장되며, 대신 `encodeURIComponent`나 `encodeURI` 사용이 권장됩니다.
- `escape`는 알파벳, 숫자, 일부 특수 문자(!, *, ', (, ), ~)를 제외한 문자에 대해 인코딩을 수행합니다.

## 예제
### 기본 사용 예
```javascript
let originalString = "Hello World!";
let escapedString = escape(originalString);
console.log(escapedString); // "Hello%20World%21"
```

### 비-ASCII 문자 예
```javascript
let nonASCIIStr = "안녕하세요";
let escapedNonASCIIStr = escape(nonASCIIStr);
console.log(escapedNonASCIIStr); // "%C0%B0%CD%C1%BF%F2%BF%F2"
```

## 설명
- `escape` 함수는 특정 문자열을 안전하게 인코딩하는 데 유용하지만, 사용할 때 주의해야 합니다. 이 함수는 모든 비-ASCII 문자를 처리하므로, 일반적인 URL 인코딩을 위한 기능을 수행하지만, 최신 JavaScript에서는 `encodeURIComponent`와 `encodeURI`를 사용하는 것이 더 바람직합니다.
- 또한, `escape` 함수는 더 이상 표준에 포함되지 않으며, 브라우저의 지원이 다를 수 있습니다. 이러한 이유로, 이 함수를 사용할 때는 호환성 문제를 고려해야 합니다.

## 한 문장 요약
JavaScript의 `escape` 함수는 문자열 내 특수 문자를 안전하게 인코딩하는 데 사용되지만, 최신 개발에서는 `encodeURIComponent`와 `encodeURI`를 사용하는 것이 권장됩니다.