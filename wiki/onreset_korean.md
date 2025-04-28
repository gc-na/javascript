<!--
Meta Description: # JavaScript onreset 이벤트에 대한 완벽 가이드 ## 개요 JavaScript의 `onreset` 이벤트는 HTML 양식(form) 요소에서 사용되며, 사용자가 양식의 리셋 버튼을 클릭할 때 발생하는 이벤트입니다. 이 이벤트를 활용하면 양식이 초기 상태...
Meta Keywords: form, onreset, 있습니다, html, input
-->

# JavaScript onreset 이벤트에 대한 완벽 가이드

## 개요
JavaScript의 `onreset` 이벤트는 HTML 양식(form) 요소에서 사용되며, 사용자가 양식의 리셋 버튼을 클릭할 때 발생하는 이벤트입니다. 이 이벤트를 활용하면 양식이 초기 상태로 돌아갈 때 특정 작업을 수행하도록 할 수 있습니다.

## 문서화
`onreset` 이벤트는 `<form>` 요소에서 발생하며, 사용자가 양식의 내용을 초기화할 때 트리거됩니다. 기본적으로 브라우저는 양식의 입력 필드를 초기값으로 되돌리지만, JavaScript를 사용하여 이 이벤트에 대한 핸들러를 정의할 수 있습니다. 이를 통해 양식이 리셋될 때 추가적인 작업을 수행하도록 할 수 있습니다.

### 사용법
`onreset` 이벤트를 처리하기 위해 HTML에서 `<form>` 태그에 `onreset` 속성을 추가하거나 JavaScript에서 이벤트 리스너를 사용할 수 있습니다.

#### HTML 속성 사용 예:
```html
<form onreset="resetFormHandler()">
    <input type="text" name="name" value="이름">
    <input type="reset" value="리셋">
</form>
```

#### JavaScript 이벤트 리스너 사용 예:
```javascript
const form = document.querySelector('form');
form.addEventListener('reset', function(event) {
    // 리셋 시 수행할 작업
    console.log('양식이 리셋되었습니다.');
});
```

## 예제
### 예제 1: 간단한 리셋 핸들러
```html
<form onreset="alert('양식이 초기화되었습니다!')">
    <input type="text" placeholder="이름">
    <input type="reset" value="리셋">
</form>
```

### 예제 2: JavaScript를 통한 리셋 핸들링
```html
<form id="myForm">
    <input type="text" placeholder="이름">
    <input type="reset" value="리셋">
</form>

<script>
    document.getElementById('myForm').addEventListener('reset', function() {
        console.log('양식이 리셋되었습니다!');
    });
</script>
```

## 설명
`onreset` 이벤트에 대한 몇 가지 주의사항이 있습니다:

- **브라우저 호환성**: 대부분의 최신 브라우저에서 `onreset` 이벤트를 지원하지만, 구형 브라우저에서는 동작이 다를 수 있습니다.
- **기본 동작 차단**: 이벤트 핸들러 내에서 `event.preventDefault()`를 호출하면 기본 리셋 동작이 차단되므로 주의해야 합니다. 이를 통해 리셋된 후의 행동을 세밀하게 제어할 수 있습니다.
- **양식 유효성 검사**: 양식 리셋 시 유효성 검사를 요구하는 경우, 이를 수동으로 처리해야 합니다.

## 한 줄 요약
`onreset` 이벤트는 사용자가 HTML 양식의 리셋 버튼을 클릭할 때 발생하며, 이를 통해 양식 초기화 시 특정 작업을 수행할 수 있습니다.