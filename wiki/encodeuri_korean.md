<!--
Meta Description: # JavaScript의 encodeURI 함수: URL 인코딩의 필수 요소 ## 개요 `encodeURI`는 JavaScript에서 URL을 안전하게 인코딩하는 데 사용되는 함수입니다. 이 함수는 URL 내에서 특별한 의미를 가지는 문자를 인코딩하여 URI를 유효하게...
Meta Keywords: encodeuri, url, const, 함수는, javascript
-->

# JavaScript의 encodeURI 함수: URL 인코딩의 필수 요소

## 개요
`encodeURI`는 JavaScript에서 URL을 안전하게 인코딩하는 데 사용되는 함수입니다. 이 함수는 URL 내에서 특별한 의미를 가지는 문자를 인코딩하여 URI를 유효하게 만듭니다.

## 문서화
### 목적
`encodeURI` 함수는 URL의 특정 부분에 포함될 수 있는 특수 문자(예: 공백, 슬래시, 물음표 등)를 인코딩하여 웹 브라우저가 올바르게 해석할 수 있도록 합니다. 이로 인해 웹 애플리케이션에서의 데이터 전송이 원활해집니다.

### 사용법
`encodeURI` 함수는 다음과 같은 형식으로 사용됩니다:

```javascript
encodeURI(uri);
```

여기서 `uri`는 인코딩할 URL 문자열입니다. 반환값은 인코딩된 URL 문자열입니다.

### 세부사항
- 이 함수는 전체 URI를 인코딩하며, URI의 구성 요소를 개별적으로 인코딩하지 않습니다.
- `encodeURI`는 다음과 같은 문자를 인코딩하지 않습니다: `:`, `/`, `?`, `#`, `&`, `=`, `+`.
- 인코딩된 결과는 `%` 기호와 16진수로 표현된 문자 코드로 구성됩니다.

## 예제
### 기본 사용 예제

```javascript
const url = "https://example.com/search?query=java script";
const encodedUrl = encodeURI(url);
console.log(encodedUrl); // "https://example.com/search?query=java%20script"
```

### 다중 쿼리 파라미터 처리

```javascript
const baseUrl = "https://example.com/search?";
const params = "query=java script&sort=asc";
const fullUrl = baseUrl + params;
const encodedFullUrl = encodeURI(fullUrl);
console.log(encodedFullUrl); // "https://example.com/search?query=java%20script&sort=asc"
```

## 설명
`encodeURI` 사용 시 주의해야 할 점은 인코딩되지 않는 특정 문자들입니다. 예를 들어, 쿼리 문자열이나 경로 세그먼트에 포함된 `/`와 같은 문자는 인코딩되지 않기 때문에, 이를 사용자가 직접 처리해야 할 수 있습니다. 또한, `encodeURIComponent`와의 차이점을 이해하는 것이 중요합니다. `encodeURIComponent`는 모든 특수 문자를 인코딩하므로, 필요한 경우 더욱 세밀한 인코딩이 가능합니다.

## 한 줄 요약
`encodeURI`는 URL을 안전하게 인코딩하여 웹 브라우저에서 올바르게 해석되도록 돕는 JavaScript 함수입니다.