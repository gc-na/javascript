<!--
Meta Description: # JavaScript localStorage: 웹 스토리지 API의 활용 ## 개요 `localStorage`는 웹 브라우저에서 데이터를 클라이언트 측에 저장할 수 있도록 해주는 JavaScript의 기능입니다. 이는 사용자가 페이지를 새로고침하거나 브라우저를 닫아도...
Meta Keywords: localstorage, javascript, 데이터를, 데이터, username
-->

# JavaScript localStorage: 웹 스토리지 API의 활용

## 개요
`localStorage`는 웹 브라우저에서 데이터를 클라이언트 측에 저장할 수 있도록 해주는 JavaScript의 기능입니다. 이는 사용자가 페이지를 새로고침하거나 브라우저를 닫아도 데이터가 유지되며, 간단한 키-값 쌍 형태로 정보를 저장, 조회, 삭제할 수 있게 해줍니다.

## 문서화

### 목적
`localStorage`는 웹 애플리케이션에서 데이터를 영구적으로 저장할 수 있는 방법을 제공합니다. 이를 통해 사용자의 설정, 세션 정보, 애플리케이션 상태 등을 지속적으로 관리할 수 있습니다.

### 사용법
`localStorage`는 전역 객체 `window`의 프로퍼티로 접근할 수 있으며, 다양한 메소드를 통해 데이터를 관리합니다. 주요 메소드는 다음과 같습니다:

- `setItem(key, value)`: 지정한 키에 대한 값을 저장합니다.
- `getItem(key)`: 지정한 키에 대한 값을 조회합니다.
- `removeItem(key)`: 지정한 키에 대한 값을 삭제합니다.
- `clear()`: 모든 데이터를 삭제합니다.
- `key(index)`: 주어진 인덱스에 해당하는 키를 반환합니다.
- `length`: 저장된 항목의 수를 반환합니다.

### 세부사항
- 데이터는 문자열 형태로 저장됩니다. 객체나 배열을 저장할 경우 `JSON.stringify()`를 사용하여 문자열로 변환해야 하며, 조회 시 `JSON.parse()`를 통해 다시 객체로 변환해야 합니다.
- `localStorage`는 도메인별로 데이터를 저장합니다. 즉, 같은 도메인 내에서만 접근할 수 있습니다.
- 저장 용량은 브라우저에 따라 다르지만, 일반적으로 5MB 정도입니다.

## 예제

### 데이터 저장
```javascript
localStorage.setItem('username', 'JohnDoe');
```

### 데이터 조회
```javascript
const username = localStorage.getItem('username');
console.log(username); // JohnDoe
```

### 데이터 삭제
```javascript
localStorage.removeItem('username');
```

### 모든 데이터 삭제
```javascript
localStorage.clear();
```

### 객체 저장 및 조회
```javascript
const user = { name: 'John', age: 30 };
localStorage.setItem('user', JSON.stringify(user));

const retrievedUser = JSON.parse(localStorage.getItem('user'));
console.log(retrievedUser.name); // John
```

## 설명
`localStorage`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- `localStorage`에 저장된 데이터는 도메인과 프로토콜에 따라 다르게 관리됩니다. 즉, 다른 도메인에서는 접근할 수 없습니다.
- 데이터가 문자열로만 저장되기 때문에, 객체를 저장할 때는 반드시 JSON으로 변환해야 하며, 이를 잊지 않도록 주의해야 합니다.
- 브라우저의 저장 용량 제한을 초과하면 데이터 저장이 실패합니다.

## 한 줄 요약
`localStorage`는 웹 브라우저에서 데이터를 영구적으로 저장하고 관리할 수 있는 JavaScript의 유용한 기능입니다.