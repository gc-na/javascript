<!--
Meta Description: # StorageEvent: JavaScript의 저장소 이벤트 ## 개요 `StorageEvent`는 웹 브라우저의 저장소(예: localStorage, sessionStorage)에서 데이터가 변경될 때 발생하는 이벤트입니다. 이 이벤트는 다른 창이나 탭에서 저장소...
Meta Keywords: 저장소, storageevent, event, 이벤트, 탭에서
-->

# StorageEvent: JavaScript의 저장소 이벤트

## 개요
`StorageEvent`는 웹 브라우저의 저장소(예: localStorage, sessionStorage)에서 데이터가 변경될 때 발생하는 이벤트입니다. 이 이벤트는 다른 창이나 탭에서 저장소의 데이터를 변경했을 때 이를 감지할 수 있게 해줍니다.

## 문서화
`StorageEvent`는 `window` 객체에서 발생하며, 주로 다른 문서에서 저장소의 변경 사항을 수신하는 데 사용됩니다. 이 이벤트는 다음과 같은 속성을 포함합니다:

- `key`: 변경된 저장소 항목의 키
- `oldValue`: 변경되기 전의 값
- `newValue`: 변경된 후의 값
- `url`: 이벤트가 발생한 문서의 URL
- `storageArea`: 이벤트가 발생한 저장소 영역 (localStorage 또는 sessionStorage)

### 사용법
`StorageEvent`를 사용하기 위해서는 `window.addEventListener` 메서드를 통해 이벤트 리스너를 추가해야 합니다. 예를 들어:

```javascript
window.addEventListener('storage', function(event) {
    console.log('저장소 변경 감지:', event);
});
```

이 코드는 저장소에 변화가 생길 때마다 이벤트를 감지하고, 관련된 정보를 콘솔에 출력합니다.

## 예제
다음은 `StorageEvent`의 기본 사용 예입니다.

```javascript
// 이벤트 리스너 추가
window.addEventListener('storage', function(event) {
    console.log('저장소 변경:', {
        key: event.key,
        oldValue: event.oldValue,
        newValue: event.newValue,
        url: event.url,
        storageArea: event.storageArea
    });
});

// 다른 탭에서 저장소 값 변경
localStorage.setItem('testKey', 'newValue');
```

위의 코드에서 첫 번째 탭에서 저장소 이벤트 리스너를 추가하고, 두 번째 탭에서 `localStorage` 값을 변경하면 첫 번째 탭에서 변경 사항을 감지하여 로그를 출력합니다.

## 설명
`StorageEvent`는 여러 탭이나 창 간의 데이터 동기화를 가능하게 합니다. 하지만 몇 가지 주의사항이 있습니다:

1. **동작 범위**: `StorageEvent`는 같은 출처의 다른 창이나 탭에서만 발생합니다. 같은 탭에서의 저장소 변경은 감지되지 않습니다.
2. **이벤트 전파**: 이벤트는 부모 창에서 자식 프레임에도 전파되지 않으므로, 이러한 구조를 고려해야 합니다.
3. **브라우저 지원**: 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 작동하지 않을 수 있습니다.

## 한 줄 요약
`StorageEvent`는 웹 저장소에서 데이터가 변경될 때 발생하며, 다른 탭에서의 저장소 변화 감지에 사용됩니다.