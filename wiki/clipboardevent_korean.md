<!--
Meta Description: # ClipboardEvent: 자바스크립트에서 클립보드 이벤트 다루기 ## 개요 ClipboardEvent는 웹 애플리케이션에서 클립보드와 관련된 작업을 처리하기 위한 이벤트입니다. 이 이벤트는 복사, 잘라내기, 붙여넣기와 같은 클립보드 행위를 감지하고 제어할 수 있...
Meta Keywords: event, 이벤트, clipboarddata, javascript, preventdefault
-->

# ClipboardEvent: 자바스크립트에서 클립보드 이벤트 다루기

## 개요
ClipboardEvent는 웹 애플리케이션에서 클립보드와 관련된 작업을 처리하기 위한 이벤트입니다. 이 이벤트는 복사, 잘라내기, 붙여넣기와 같은 클립보드 행위를 감지하고 제어할 수 있도록 도와줍니다.

## 문서화
ClipboardEvent는 사용자가 클립보드와 상호작용할 때 발생하는 이벤트를 나타냅니다. 이 이벤트는 다음과 같은 상황에서 발생합니다:

- `copy`: 사용자가 클립보드에 내용을 복사할 때
- `cut`: 사용자가 클립보드에 내용을 잘라낼 때
- `paste`: 사용자가 클립보드의 내용을 붙여넣을 때

### 사용법
ClipboardEvent를 사용하려면 JavaScript의 이벤트 리스너를 통해 해당 이벤트를 수신하고 처리해야 합니다. 다음은 기본적인 사용법입니다:

```javascript
document.addEventListener('copy', function(event) {
    // 클립보드에 복사할 내용 설정
    event.clipboardData.setData('text/plain', '복사할 텍스트');
    event.preventDefault(); // 기본 복사 동작 방지
});
```

### 주요 속성
- `clipboardData`: 클립보드와 상호작용할 수 있는 데이터를 제공하는 ClipboardData 객체입니다.

## 예제
### 1. 복사 이벤트 처리
```javascript
document.addEventListener('copy', function(event) {
    event.clipboardData.setData('text/plain', 'Hello, World!');
    event.preventDefault(); // 기본 복사 동작 방지
});
```

### 2. 붙여넣기 이벤트 처리
```javascript
document.addEventListener('paste', function(event) {
    const pastedData = event.clipboardData.getData('text/plain');
    console.log('붙여넣은 데이터:', pastedData);
    event.preventDefault(); // 기본 붙여넣기 동작 방지
});
```

### 3. 잘라내기 이벤트 처리
```javascript
document.addEventListener('cut', function(event) {
    event.clipboardData.setData('text/plain', '잘라낼 데이터');
    event.preventDefault(); // 기본 잘라내기 동작 방지
});
```

## 설명
ClipboardEvent를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **브라우저 지원**: 모든 브라우저에서 ClipboardEvent를 동일하게 지원하지 않으므로, 호환성 문제를 고려해야 합니다.
- **보안 제한**: 클립보드 접근은 특정 사용자 상호작용(예: 클릭) 후에만 가능하므로, 자동으로 클립보드를 조작하는 것은 불가능합니다.
- **이벤트 전파**: 이벤트의 기본 동작을 방지하려면 `event.preventDefault()`를 호출해야 합니다. 그렇지 않으면 기본 동작이 실행됩니다.

## 한 줄 요약
ClipboardEvent는 웹 애플리케이션에서 클립보드와 상호작용할 수 있도록 해주는 JavaScript 이벤트입니다.