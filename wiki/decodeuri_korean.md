<!--
Meta Description: # JavaScript decodeURI 함수: URL 디코딩의 기본 ## 개요 `decodeURI` 함수는 JavaScript에서 URL을 디코딩하는 데 사용되는 내장 함수입니다. URL 인코딩된 문자열을 원래의 형태로 변환하여, 웹 애플리케이션에서 URL을 쉽게 다...
Meta Keywords: decodeuri, 인코딩된, 함수는, uri, encodeduri
-->

# JavaScript decodeURI 함수: URL 디코딩의 기본

## 개요
`decodeURI` 함수는 JavaScript에서 URL을 디코딩하는 데 사용되는 내장 함수입니다. URL 인코딩된 문자열을 원래의 형태로 변환하여, 웹 애플리케이션에서 URL을 쉽게 다룰 수 있게 해줍니다.

## 문서화

### 목적
`decodeURI` 함수는 인코딩된 URI(Uniform Resource Identifier) 구성 요소를 디코딩하여 다시 읽을 수 있는 형태로 변환하는 데 사용됩니다. 이 함수는 주로 쿼리 문자열이나 경로에서 전달된 데이터를 처리할 때 유용합니다.

### 사용법
```javascript
decodeURI(encodedURI);
```

- **매개변수**: 
  - `encodedURI` (문자열) - 인코딩된 URI 문자열.
  
- **반환 값**: 
  - 디코딩된 URI 문자열.

### 세부사항
- `decodeURI`는 특정 문자(예: 공백, #, &, = 등)는 변환하지 않으며, 그 외의 모든 인코딩된 문자를 디코딩합니다.
- 이 함수는 URI의 구조를 변경하지 않고, 인코딩된 데이터를 안전하게 복원합니다.

## 예제

```javascript
// 예제 1: 기본 사용법
const encodedURI = "https%3A%2F%2Fexample.com%2Fpage%3Fquery%3Dtest%20value";
const decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // 출력: https://example.com/page?query=test value

// 예제 2: 공백이 포함된 URL
const encodedURIWithSpace = "Hello%20World%21";
const decodedURIWithSpace = decodeURI(encodedURIWithSpace);
console.log(decodedURIWithSpace); // 출력: Hello World!
```

## 설명
- **일반적인 오류**: `decodeURI`를 사용할 때, 인코딩되지 않은 문자열에 사용하면 오류가 발생할 수 있습니다. 잘못된 형식의 문자열을 디코딩하려고 하면 `URIError`가 발생합니다.
- **주의 사항**: URL의 특정 부분(예: 쿼리 매개변수)에는 `encodeURIComponent` 함수를 사용하여 인코딩하는 것이 권장됩니다. 이는 더 안전하게 특정 문자(예: &, =, 등)를 처리할 수 있습니다.

## 한 줄 요약
`decodeURI`는 인코딩된 URI 문자열을 원래의 형태로 디코딩하는 JavaScript의 내장 함수입니다.