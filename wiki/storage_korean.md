<!--
Meta Description: # JavaScript 저장소(Storage) - 웹 애플리케이션 데이터 저장 방법 ## 개요 JavaScript에서 "저장소(Storage)"는 웹 브라우저에서 클라이언트의 데이터를 지속적으로 저장하기 위한 API입니다. 주로 `localStorage`와 `sessi...
Meta Keywords: 데이터, 데이터를, localstorage, sessionstorage, username
-->

# JavaScript 저장소(Storage) - 웹 애플리케이션 데이터 저장 방법

## 개요
JavaScript에서 "저장소(Storage)"는 웹 브라우저에서 클라이언트의 데이터를 지속적으로 저장하기 위한 API입니다. 주로 `localStorage`와 `sessionStorage`를 사용하여 데이터를 저장하고 관리할 수 있습니다.

## 문서화
### 목적
JavaScript의 저장소 API는 웹 애플리케이션에서 사용자 데이터를 클라이언트 측에 저장할 수 있는 편리한 방법을 제공합니다. 이를 통해 사용자는 브라우저를 새로 고치거나 다시 방문할 때도 데이터를 유지할 수 있습니다.

### 사용법
- **localStorage**: 브라우저에 데이터를 영구적으로 저장하는 방법으로, 브라우저 세션이 종료되어도 데이터가 유지됩니다.
- **sessionStorage**: 현재 세션에만 데이터를 저장하는 방법으로, 브라우저 탭이 닫히면 데이터가 사라집니다.

### 주요 메소드
- `setItem(key, value)`: 지정한 키에 값을 저장합니다.
- `getItem(key)`: 지정한 키에 해당하는 값을 반환합니다.
- `removeItem(key)`: 지정한 키에 해당하는 데이터를 삭제합니다.
- `clear()`: 모든 저장된 데이터를 삭제합니다.
- `key(index)`: 저장소에서 지정한 인덱스의 키를 반환합니다.
- `length`: 저장소에 저장된 데이터의 수를 반환합니다.

## 예제
### localStorage 사용 예
```javascript
// 데이터 저장
localStorage.setItem('username', 'user123');

// 데이터 조회
const username = localStorage.getItem('username');
console.log(username); // 'user123'

// 데이터 삭제
localStorage.removeItem('username');

// 모든 데이터 삭제
localStorage.clear();
```

### sessionStorage 사용 예
```javascript
// 데이터 저장
sessionStorage.setItem('sessionID', 'abc123');

// 데이터 조회
const sessionID = sessionStorage.getItem('sessionID');
console.log(sessionID); // 'abc123'

// 데이터 삭제
sessionStorage.removeItem('sessionID');

// 모든 데이터 삭제
sessionStorage.clear();
```

## 설명
- **저장 용량**: 일반적으로 `localStorage`와 `sessionStorage`는 각각 약 5MB의 데이터를 저장할 수 있습니다. 용량이 초과되면 데이터가 저장되지 않습니다.
- **데이터 유형**: 저장되는 데이터는 문자열 형태로만 저장됩니다. 객체나 배열을 저장하고 싶다면 JSON.stringify()를 사용하여 문자열로 변환해야 하며, JSON.parse()를 통해 다시 객체로 변환할 수 있습니다.
- **보안**: 저장소에 저장된 데이터는 클라이언트 측에서 접근할 수 있으므로, 민감한 정보는 저장하지 않는 것이 좋습니다.

## 한 줄 요약
JavaScript의 저장소 API는 웹 애플리케이션에서 클라이언트 데이터를 영구적 또는 세션별로 저장할 수 있는 방법을 제공합니다.