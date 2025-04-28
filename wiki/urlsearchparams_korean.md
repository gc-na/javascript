<!--
Meta Description: # URLSearchParams: 자바스크립트에서 URL 쿼리 문자열 처리하기 ## 개요 `URLSearchParams`는 JavaScript에서 URL 쿼리 문자열을 쉽게 처리하고 조작할 수 있도록 도와주는 인터페이스입니다. 이 객체를 사용하면 URL의 쿼리 파라미터...
Meta Keywords: urlsearchparams, name, params, url, 문자열을
-->

# URLSearchParams: 자바스크립트에서 URL 쿼리 문자열 처리하기

## 개요
`URLSearchParams`는 JavaScript에서 URL 쿼리 문자열을 쉽게 처리하고 조작할 수 있도록 도와주는 인터페이스입니다. 이 객체를 사용하면 URL의 쿼리 파라미터를 추가, 수정, 삭제 및 조회할 수 있습니다.

## 문서화

### 목적
`URLSearchParams`는 URL의 쿼리 문자열을 다루기 위한 API로, 복잡한 문자열 조작을 간소화하여 개발자가 더 쉽게 URL을 관리할 수 있도록 합니다.

### 사용법
`URLSearchParams`는 URL의 쿼리 문자열을 파싱하여 쉽게 사용할 수 있는 형태로 변환합니다. 다음과 같은 방법으로 생성할 수 있습니다:

```javascript
const params = new URLSearchParams('key1=value1&key2=value2');
```

### 주요 메서드
- `append(name, value)`: 새로운 쿼리 파라미터를 추가합니다.
- `delete(name)`: 특정 쿼리 파라미터를 삭제합니다.
- `get(name)`: 특정 파라미터의 값을 반환합니다.
- `has(name)`: 특정 파라미터가 존재하는지 확인합니다.
- `set(name, value)`: 특정 파라미터의 값을 설정합니다.
- `toString()`: 쿼리 문자열을 문자열 형태로 반환합니다.

## 예제

### 기본 사용 예
```javascript
const params = new URLSearchParams('name=John&age=30');

// 파라미터 추가
params.append('city', 'Seoul');

// 파라미터 조회
console.log(params.get('name')); // "John"

// 파라미터 수정
params.set('age', '31');
console.log(params.toString()); // "name=John&age=31&city=Seoul"

// 파라미터 삭제
params.delete('city');
console.log(params.toString()); // "name=John&age=31"
```

## 설명
`URLSearchParams`는 URL 쿼리 문자열을 다루는 데 유용하지만, 몇 가지 주의할 점이 있습니다:

1. **인코딩**: URL 쿼리 문자열은 항상 URL 인코딩을 고려해야 합니다. `URLSearchParams`는 자동으로 이를 처리하지만, 특정 문자가 인코딩되지 않으면 예상치 못한 결과가 발생할 수 있습니다.
2. **중복 키**: 동일한 키를 가진 여러 값을 사용할 수 있으며, `get()` 메서드는 첫 번째 값을 반환합니다. 모든 값을 가져오려면 `getAll()` 메서드를 사용해야 합니다.
3. **IE 호환성**: `URLSearchParams`는 Internet Explorer에서 지원되지 않으므로 호환성에 유의해야 합니다.

## 한 줄 요약
`URLSearchParams`는 JavaScript에서 URL 쿼리 문자열을 간편하게 처리하고 조작할 수 있는 인터페이스입니다.