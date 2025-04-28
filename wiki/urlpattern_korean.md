<!--
Meta Description: # URLPattern: JavaScript에서 URL 패턴 매칭의 이해 ## 개요 `URLPattern`은 JavaScript에서 URL을 비교하고, 패턴을 정의하여 URL을 쉽게 매칭할 수 있도록 도와주는 API입니다. 이 기능은 웹 애플리케이션에서 라우팅 및 UR...
Meta Keywords: url, urlpattern, const, url을, pattern
-->

# URLPattern: JavaScript에서 URL 패턴 매칭의 이해

## 개요
`URLPattern`은 JavaScript에서 URL을 비교하고, 패턴을 정의하여 URL을 쉽게 매칭할 수 있도록 도와주는 API입니다. 이 기능은 웹 애플리케이션에서 라우팅 및 URL 처리 작업을 간소화합니다.

## 문서
`URLPattern`은 주로 웹 개발에서 URL을 쉽게 분석하고 매칭하기 위해 사용됩니다. 이 API는 복잡한 URL 문자열의 처리와 특정 패턴에 맞는 URL을 찾는 데 유용합니다.

### 목적
`URLPattern`의 주요 목적은 URL을 패턴에 따라 비교하고, URL에서 특정 구성 요소를 추출하는 것입니다. 이를 통해 개발자는 RESTful API 라우팅 및 클라이언트 측 내비게이션을 관리할 수 있습니다.

### 사용법
`URLPattern` 객체는 URL 패턴을 정의하고, 이를 사용하여 URL을 검사하는 데 사용됩니다. 객체를 생성할 때는 패턴 문자열과 선택적으로 옵션을 추가할 수 있습니다.

```javascript
const pattern = new URLPattern({ 
    pathname: '/users/:id' 
});
```

### 세부 사항
- **생성자**: `new URLPattern(pattern, baseUrl)`
  - `pattern`: URL 패턴을 정의하는 문자열. 경로 매개변수(`:param`)와 쿼리 매개변수를 포함할 수 있습니다.
  - `baseUrl` (선택 사항): 패턴의 기준이 되는 기본 URL.
  
- **메서드**:
  - `test(url)`: 주어진 URL이 패턴에 맞는지 확인합니다.
  - `exec(url)`: 주어진 URL이 패턴에 맞는 경우, 매칭된 결과를 반환합니다.

## 예제
### 기본 사용법
```javascript
const pattern = new URLPattern({ pathname: '/products/:id' });
const url = 'https://example.com/products/123';

// 패턴 테스트
console.log(pattern.test(url)); // true

// 패턴 실행
const match = pattern.exec(url);
console.log(match.pathname.groups.id); // 123
```

### 쿼리 매개변수 사용
```javascript
const patternWithQuery = new URLPattern({ 
    pathname: '/search', 
    search: '?query=:searchTerm' 
});
const searchUrl = 'https://example.com/search?query=javascript';

// 패턴 테스트
console.log(patternWithQuery.test(searchUrl)); // true

// 패턴 실행
const searchMatch = patternWithQuery.exec(searchUrl);
console.log(searchMatch.search.groups.searchTerm); // javascript
```

## 설명
`URLPattern`을 사용할 때 주의할 점은 URL이 패턴과 정확히 일치해야 한다는 것입니다. 매개변수가 없는 URL이나 추가적인 경로가 있을 경우, `test` 메서드는 `false`를 반환합니다. 또한, `exec` 메서드는 매칭된 그룹을 반환하지만, 매칭되지 않을 경우 `null`을 반환하므로 이를 처리해야 합니다.

## 한 줄 요약
`URLPattern`은 JavaScript에서 URL 패턴을 정의하고 매칭하는 데 유용한 API로, 웹 애플리케이션의 라우팅을 간소화합니다.