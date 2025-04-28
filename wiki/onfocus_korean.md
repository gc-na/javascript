<!--
Meta Description: # JavaScript의 onfocus 이벤트: 사용법 및 예제 ## 개요 `onfocus`는 HTML 요소가 포커스를 받을 때 발생하는 이벤트로, 주로 입력 필드와 같은 사용자 인터페이스 요소에서 사용됩니다. JavaScript를 통해 이 이벤트를 처리하여 사용자 경...
Meta Keywords: onfocus, html, 이벤트, 이벤트는, 있습니다
-->

# JavaScript의 onfocus 이벤트: 사용법 및 예제

## 개요
`onfocus`는 HTML 요소가 포커스를 받을 때 발생하는 이벤트로, 주로 입력 필드와 같은 사용자 인터페이스 요소에서 사용됩니다. JavaScript를 통해 이 이벤트를 처리하여 사용자 경험을 향상시킬 수 있습니다.

## 문서화
`onfocus` 이벤트는 사용자가 입력 필드, 버튼, 링크 등과 같은 요소를 클릭하거나 탭 키를 통해 활성화할 때 발생합니다. 이 이벤트는 사용자가 해당 요소에 포커스를 주었음을 나타내며, 일반적으로 입력 상자에 대한 유효성 검사, 스타일 변경, 추가 정보 표시 등 다양한 작업을 트리거하는 데 사용됩니다.

### 사용법
`onfocus` 이벤트는 다음과 같이 HTML 요소에 직접 속성으로 추가하거나, JavaScript를 통해 이벤트 리스너를 등록하여 사용할 수 있습니다.

#### HTML 속성으로 사용
```html
<input type="text" onfocus="alert('포커스가 주어졌습니다!')">
```

#### JavaScript로 사용
```javascript
const inputField = document.getElementById('myInput');
inputField.onfocus = function() {
    console.log('입력 필드에 포커스가 주어졌습니다.');
};
```

### 세부사항
- `onfocus` 이벤트는 기본적으로 이벤트 전파가 발생하지 않으며, 이는 부모 요소의 포커스 이벤트가 발생하지 않음을 의미합니다.
- 입력 필드가 포커스를 잃을 때는 `onblur` 이벤트가 발생합니다.
- 이 이벤트는 마우스 클릭뿐만 아니라 키보드의 Tab 키를 사용하여도 발생합니다.

## 예제
### 1. 기본 입력 필드 사용 예
```html
<input type="text" id="username" onfocus="this.style.backgroundColor = '#e0f7fa';" placeholder="사용자 이름 입력">
```

### 2. JavaScript 이벤트 리스너 사용 예
```html
<input type="text" id="email" placeholder="이메일 입력">
<script>
    document.getElementById('email').addEventListener('focus', function() {
        this.style.borderColor = 'blue';
    });
</script>
```

## 설명
`onfocus` 이벤트를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **이벤트 전파**: `onfocus`는 이벤트 전파가 발생하지 않기 때문에, 만약 부모 요소에 대한 포커스 이벤트를 감지하고 싶다면 별도로 구현해야 합니다.
- **브라우저 호환성**: 모든 브라우저에서 `onfocus` 이벤트는 지원되지만, 모바일 기기에서는 다르게 동작할 수 있습니다. 예를 들어, 모바일 브라우저에서 `onfocus`가 즉시 발생하지 않을 수 있습니다.
- **접근성**: 화면 판독기와 같은 시각 장애인을 위한 도구에서 포커스 변경을 인식할 수 있도록 적절한 ARIA 속성을 추가하여 접근성을 향상시켜야 합니다.

## 한 줄 요약
`onfocus`는 HTML 요소가 포커스를 받을 때 발생하는 이벤트로, 사용자 인터페이스의 상호작용을 향상시키는 데 사용됩니다.