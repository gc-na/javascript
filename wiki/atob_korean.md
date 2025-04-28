<!--
Meta Description: # JavaScript atob() 함수: Base64 디코딩의 모든 것 ## 개요 `atob()` 함수는 Base64로 인코딩된 문자열을 디코딩하는 JavaScript 내장 함수입니다. 이 함수는 웹 애플리케이션에서 데이터를 안전하게 전송하고 저장하기 위해 자주 사용...
Meta Keywords: atob, 함수는, base64, 인코딩된, 문자열을
-->

# JavaScript atob() 함수: Base64 디코딩의 모든 것

## 개요
`atob()` 함수는 Base64로 인코딩된 문자열을 디코딩하는 JavaScript 내장 함수입니다. 이 함수는 웹 애플리케이션에서 데이터를 안전하게 전송하고 저장하기 위해 자주 사용됩니다.

## 문서화

### 목적
`atob()` 함수는 Base64 인코딩된 데이터를 디코딩하여 원래의 문자열로 변환하는 데 사용됩니다. 이 함수는 주로 웹 브라우저 환경에서 사용되며, Base64 인코딩된 이미지나 파일을 처리할 때 유용합니다.

### 사용법
```javascript
let decodedString = atob(encodedString);
```

- `encodedString`: Base64로 인코딩된 문자열. 이 문자열은 ASCII 문자만 포함해야 합니다.
- `decodedString`: 디코딩된 원래 문자열.

### 세부사항
- `atob()` 함수는 Base64로 인코딩된 데이터만 디코딩할 수 있습니다. 만약 입력 문자열이 Base64 형식이 아니라면 `DOMException`이 발생합니다.
- 이 함수는 UTF-16 문자열을 처리하지 못하므로, UTF-8 문자열을 디코딩하려면 추가적인 변환 과정이 필요합니다.

## 예제

### 기본 사용 예제
```javascript
let encoded = "SGVsbG8gV29ybGQh"; // "Hello World!"의 Base64 인코딩
let decoded = atob(encoded);
console.log(decoded); // "Hello World!"
```

### UTF-8 문자열 디코딩 예제
```javascript
function decodeUTF8(encoded) {
    return decodeURIComponent(escape(atob(encoded)));
}

let encodedUTF8 = "5Lit5Zu96YeM5LiK"; // "안녕하세요"의 Base64 인코딩
let decodedUTF8 = decodeUTF8(encodedUTF8);
console.log(decodedUTF8); // "안녕하세요"
```

## 설명
- `atob()` 함수는 인코딩된 문자열이 올바른 Base64 형식이 아닐 경우 `DOMException`을 발생시킵니다. 따라서, 입력값의 유효성을 검증하는 것이 중요합니다.
- 이 함수는 ASCII 문자 집합에만 작동하므로, UTF-8 문자열을 다룰 경우 `decodeURIComponent` 및 `escape`를 사용하여 추가적인 처리가 필요합니다.
- 최신 브라우저에서는 `atob()`와 함께 `btoa()` 함수도 제공되며, 이는 문자열을 Base64로 인코딩하는 데 사용됩니다.

## 한 줄 요약
`atob()` 함수는 Base64로 인코딩된 문자열을 원래의 문자열로 디코딩하는 JavaScript의 내장 함수입니다.