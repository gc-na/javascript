<!--
Meta Description: # JavaScript의 onstorage 이벤트: 웹 스토리지 변경 감지하기 ## 개요 JavaScript의 `onstorage` 이벤트는 웹 스토리지 API에서 변화를 감지할 수 있게 해주는 기능입니다. 이 이벤트는 다른 탭이나 창에서 로컬 스토리지(Local St...
Meta Keywords: event, 스토리지, onstorage, 이벤트는, 데이터
-->

# JavaScript의 onstorage 이벤트: 웹 스토리지 변경 감지하기

## 개요
JavaScript의 `onstorage` 이벤트는 웹 스토리지 API에서 변화를 감지할 수 있게 해주는 기능입니다. 이 이벤트는 다른 탭이나 창에서 로컬 스토리지(Local Storage) 또는 세션 스토리지(Session Storage)가 변경될 때 발생합니다. 이를 통해 여러 탭에서의 데이터 동기화를 쉽게 처리할 수 있습니다.

## 문서화
`onstorage` 이벤트는 웹 애플리케이션에서 스토리지 데이터가 업데이트될 때 자동으로 호출되는 이벤트입니다. 이 이벤트는 주로 다음과 같은 목적으로 사용됩니다:

- **데이터 동기화**: 사용자가 여러 탭에서 작업할 때, 한 탭에서 데이터가 변경되면 다른 탭에서도 이를 반영할 수 있게 합니다.
- **실시간 업데이트**: 사용자 인터페이스(UI)를 실시간으로 업데이트하여 동적인 웹 애플리케이션을 개선합니다.

### 사용법
`onstorage` 이벤트는 `window` 객체에 바인딩하여 사용할 수 있습니다. 다음은 기본적인 사용 예입니다:

```javascript
window.addEventListener('storage', function(event) {
    console.log('스토리지 키:', event.key);
    console.log('이전 값:', event.oldValue);
    console.log('새로운 값:', event.newValue);
    console.log('스토리지 영역:', event.storageArea);
});
```

이 코드는 스토리지 데이터가 변경될 때마다 해당 정보를 로그로 출력합니다.

## 예제
### 예제 1: 기본 onstorage 이벤트 사용

```javascript
// 다른 탭에서 실행할 수 있는 코드
window.addEventListener('storage', function(event) {
    alert(`변경된 키: ${event.key}, 이전 값: ${event.oldValue}, 새로운 값: ${event.newValue}`);
});

// 로컬 스토리지에 데이터 추가
localStorage.setItem('exampleKey', 'exampleValue');
```

### 예제 2: 데이터 삭제 감지

```javascript
window.addEventListener('storage', function(event) {
    if (event.key === 'exampleKey') {
        console.log('exampleKey가 삭제되었습니다.');
    }
});

// 다른 탭에서 데이터 삭제
localStorage.removeItem('exampleKey');
```

## 설명
`onstorage` 이벤트를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **다른 탭/창에서의 변화**: `onstorage` 이벤트는 동일한 출처(origin)에서 열려 있는 다른 탭이나 창에서의 스토리지 변경 사항만 감지합니다. 현재 탭 내에서의 변경은 감지되지 않습니다.
- **이벤트 객체**: 이벤트 핸들러 함수에서 `event` 객체를 통해 변경된 키와 값을 확인할 수 있습니다.
- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원되지만, 항상 브라우저별 호환성을 확인하는 것이 좋습니다.

## 한 줄 요약
JavaScript의 `onstorage` 이벤트는 웹 스토리지의 변화를 감지하여 여러 탭 간의 데이터 동기화를 가능하게 해주는 기능입니다.