<!--
Meta Description: # JavaScript에서 URL 다루기: URL 객체와 메서드 ## 개요 JavaScript에서 URL은 웹 페이지의 주소를 나타내며, URL 객체를 통해 URL을 생성, 수정 및 분석할 수 있습니다. 이 문서에서는 JavaScript의 URL 객체와 그 사용법에 대...
Meta Keywords: url, console, log, url을, https
-->

# JavaScript에서 URL 다루기: URL 객체와 메서드

## 개요
JavaScript에서 URL은 웹 페이지의 주소를 나타내며, URL 객체를 통해 URL을 생성, 수정 및 분석할 수 있습니다. 이 문서에서는 JavaScript의 URL 객체와 그 사용법에 대해 설명합니다.

## 문서
### 목적
JavaScript의 URL 객체는 웹 애플리케이션에서 URL을 다루기 위한 강력한 도구입니다. 이 객체를 사용하면 URL의 구성 요소를 쉽게 분리하고 수정할 수 있습니다. 또한, URL에 대한 다양한 메서드를 제공하여 URL을 보다 효율적으로 관리할 수 있습니다.

### 사용법
URL 객체는 `URL` 생성자를 사용하여 생성합니다. 기본 문법은 다음과 같습니다:

```javascript
const myURL = new URL(urlString[, base]);
```

- `urlString`: URL로 변환할 문자열입니다.
- `base` (선택적): URL이 상대 경로인 경우 해당 URL의 기준이 되는 기본 URL입니다.

### 세부 사항
- URL 객체의 주요 속성:
  - `href`: 전체 URL 문자열
  - `protocol`: URL의 프로토콜 (예: `http:`, `https:`)
  - `host`: 호스트 이름과 포트 번호
  - `hostname`: 호스트 이름
  - `port`: 포트 번호
  - `pathname`: 경로
  - `search`: 쿼리 문자열
  - `hash`: 해시 문자열

- URL 객체는 다음과 같은 메서드를 제공합니다:
  - `toString()`: URL을 문자열로 변환
  - `searchParams`: URL의 검색 매개변수를 쉽게 관리할 수 있는 객체를 반환

## 예시
### 기본 사용 예
```javascript
const url = new URL('https://example.com:8080/path?query=string#hash');

console.log(url.href);       // "https://example.com:8080/path?query=string#hash"
console.log(url.protocol);   // "https:"
console.log(url.hostname);    // "example.com"
console.log(url.port);        // "8080"
console.log(url.pathname);    // "/path"
console.log(url.search);      // "?query=string"
console.log(url.hash);        // "#hash"
```

### 검색 매개변수 예
```javascript
const url = new URL('https://example.com?name=John&age=30');

// 검색 매개변수에 접근
console.log(url.searchParams.get('name')); // "John"

// 검색 매개변수 추가
url.searchParams.append('country', 'Korea');
console.log(url.href); // "https://example.com?name=John&age=30&country=Korea"
```

## 설명
JavaScript의 URL 객체를 사용할 때 주의할 점:
- 상대 경로를 사용할 경우 `base` URL을 정확히 지정해야 합니다. 그렇지 않으면 의도하지 않은 결과를 초래할 수 있습니다.
- URL 구조에 대한 이해가 부족하면 매개변수 접근이나 수정 시 어려움을 겪을 수 있습니다.
- URL의 일부 속성은 읽기 전용이며 직접 수정할 수 없습니다 (예: `href` 속성은 URL 객체에 의해 자동으로 관리됩니다).

## 한 줄 요약
JavaScript의 URL 객체는 URL을 생성, 수정 및 분석하는 데 필요한 유용한 기능을 제공합니다.