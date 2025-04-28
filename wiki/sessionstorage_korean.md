<!--
Meta Description: # sessionStorage: JavaScript에서의 세션 스토리지 사용법 ## 개요 `sessionStorage`는 웹 브라우저에서 세션 데이터 저장을 위한 JavaScript API로, 사용자가 페이지를 새로 고치거나 탭을 변경하더라도 데이터를 유지할 수 있습니...
Meta Keywords: sessionstorage, 데이터, 데이터를, 사용하여, 있습니다
-->

# sessionStorage: JavaScript에서의 세션 스토리지 사용법

## 개요
`sessionStorage`는 웹 브라우저에서 세션 데이터 저장을 위한 JavaScript API로, 사용자가 페이지를 새로 고치거나 탭을 변경하더라도 데이터를 유지할 수 있습니다. 데이터는 탭이나 브라우저 세션이 종료될 때까지 유지되며, 보안과 데이터 무결성을 고려한 저장소입니다.

## 문서화
`sessionStorage`는 웹 애플리케이션에서 임시 데이터를 저장하고 관리하는 데 유용한 기능입니다. `localStorage`와 유사하지만, `sessionStorage`는 특정 세션에서만 데이터를 유지합니다. 데이터는 문자열 형태로 저장되며, 최대 용량은 약 5MB입니다.

### 사용법
- **데이터 저장**: `sessionStorage.setItem(key, value)` 메소드를 사용하여 데이터를 저장합니다.
- **데이터 조회**: `sessionStorage.getItem(key)` 메소드를 사용하여 저장된 데이터를 조회합니다.
- **데이터 삭제**: `sessionStorage.removeItem(key)` 메소드를 사용하여 특정 데이터를 삭제합니다.
- **모든 데이터 삭제**: `sessionStorage.clear()` 메소드를 사용하여 모든 세션 데이터를 삭제합니다.

### 속성 및 메소드
- **length**: 현재 저장소에 저장된 데이터 항목의 수를 반환합니다.
- **key(index)**: 지정된 인덱스에 해당하는 데이터의 키를 반환합니다.

## 예제
다음은 `sessionStorage`의 기본적인 사용 예제입니다.

```javascript
// 데이터 저장
sessionStorage.setItem('username', 'JohnDoe');

// 데이터 조회
const username = sessionStorage.getItem('username');
console.log(username); // JohnDoe

// 데이터 삭제
sessionStorage.removeItem('username');

// 모든 데이터 삭제
sessionStorage.clear();
```

## 설명
`sessionStorage`를 사용할 때 유의해야 할 몇 가지 사항이 있습니다.
1. **데이터 유형**: `sessionStorage`는 문자열만 저장할 수 있습니다. 객체나 배열을 저장하려면 JSON.stringify()를 사용하여 문자열로 변환해야 하며, 조회 시 JSON.parse()를 사용하여 다시 객체로 변환해야 합니다.
2. **세션 종료**: 브라우저 탭이나 창을 닫으면 `sessionStorage`에 저장된 데이터가 삭제됩니다. 이는 `localStorage`와의 주요 차이점입니다.
3. **도메인 제한**: `sessionStorage`는 동일한 도메인 내에서만 접근할 수 있습니다. 다른 도메인에서 저장한 데이터는 접근할 수 없습니다.
4. **브라우저 호환성**: 대부분의 최신 브라우저에서 지원하지만, 구 버전의 브라우저에서는 지원되지 않을 수 있습니다.

## 한 줄 요약
`sessionStorage`는 웹 세션 동안 데이터를 임시로 저장하고 관리할 수 있는 JavaScript API입니다.