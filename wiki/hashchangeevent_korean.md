<!--
Meta Description: # HashChangeEvent: 자바스크립트에서의 해시 변경 이벤트 ## 개요 HashChangeEvent는 웹 애플리케이션에서 URL의 해시 부분이 변경될 때 발생하는 이벤트입니다. 이 이벤트는 주로 싱글 페이지 애플리케이션(SPA)에서 페이지 간의 상태를 관리하는...
Meta Keywords: 해시가, window, 변경될, location, hash
-->

# HashChangeEvent: 자바스크립트에서의 해시 변경 이벤트

## 개요
HashChangeEvent는 웹 애플리케이션에서 URL의 해시 부분이 변경될 때 발생하는 이벤트입니다. 이 이벤트는 주로 싱글 페이지 애플리케이션(SPA)에서 페이지 간의 상태를 관리하는 데 유용합니다.

## 문서화
### 목적
HashChangeEvent는 URL의 해시가 변경될 때 발생하여, 개발자가 해시 값의 변화를 감지하고 이에 따라 적절한 동작을 수행할 수 있도록 도와줍니다. 이 이벤트는 주로 `window` 객체에서 발생하여 사용자가 페이지를 이동하지 않고도 애플리케이션의 상태를 업데이트할 수 있게 합니다.

### 사용법
HashChangeEvent는 `window.onhashchange` 이벤트 핸들러를 통해 사용할 수 있습니다. 해시 값이 변경될 때마다 이 핸들러가 호출됩니다.

```javascript
window.onhashchange = function() {
    console.log('해시가 변경되었습니다:', location.hash);
};
```

### 세부사항
- **이벤트 속성**:
  - `newURL`: 변경된 해시가 포함된 전체 URL.
  - `oldURL`: 이전 해시가 포함된 전체 URL.
  
- **브라우저 지원**: 대부분의 현대 브라우저에서 지원되지만, 구형 브라우저에서는 지원하지 않을 수 있습니다.

## 예제
### 기본 사용 예제
```javascript
window.onhashchange = function() {
    alert('현재 해시: ' + location.hash);
};

// 해시를 변경하여 이벤트를 발생시킴
window.location.hash = 'new-section';
```

### 여러 해시 변경 예제
```javascript
function changeHash(newHash) {
    window.location.hash = newHash;
}

window.onhashchange = function() {
    console.log('현재 해시:', location.hash);
};

// 해시 변경 호출
changeHash('section1'); // 해시가 section1로 변경
changeHash('section2'); // 해시가 section2로 변경
```

## 설명
HashChangeEvent를 사용할 때 주의해야 할 점은 이벤트가 발생하는 시점입니다. 해시가 변경될 때 페이지가 리로드되지 않기 때문에, 이전 해시와 새 해시를 비교하여 상태를 관리해야 합니다. 또한, 해시 변경은 `pushState`나 `replaceState`와 함께 사용하여 더 나은 사용자 경험을 제공할 수 있습니다.

### 일반적인 함정
- **이벤트 중복 호출**: 브라우저의 뒤로 가기/앞으로 가기 버튼을 사용할 때 여러 번 호출될 수 있습니다.
- **해시 변경 시 페이지 이동 없음**: 해시 변경은 페이지를 이동시키지 않으므로, 사용자 경험을 고려하여 적절한 상태 업데이트를 수행해야 합니다.

## 한줄 요약
HashChangeEvent는 URL의 해시가 변경될 때 발생하여, 웹 애플리케이션에서 상태를 관리하는 데 유용한 이벤트입니다.