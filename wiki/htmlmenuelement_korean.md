<!--
Meta Description: # HTMLMenuElement: JavaScript에서의 사용법과 예제 ## 개요 HTMLMenuElement는 HTML 문서 내에서 메뉴를 정의하는 요소로, 주로 컨텍스트 메뉴(우클릭 메뉴)나 애플리케이션의 메뉴를 생성하는 데 사용됩니다. JavaScript와 함께...
Meta Keywords: menu, htmlmenuelement는, html, 메뉴를, 있습니다
-->

# HTMLMenuElement: JavaScript에서의 사용법과 예제

## 개요
HTMLMenuElement는 HTML 문서 내에서 메뉴를 정의하는 요소로, 주로 컨텍스트 메뉴(우클릭 메뉴)나 애플리케이션의 메뉴를 생성하는 데 사용됩니다. JavaScript와 함께 활용하여 동적인 메뉴를 구현할 수 있습니다.

## 문서화
HTMLMenuElement는 HTML5에 도입된 요소로, `<menu>` 태그로 정의됩니다. 이 요소는 사용자에게 선택 가능한 명령이나 동작을 제공하는 데 사용됩니다. HTMLMenuElement는 다음과 같은 주요 속성과 메서드를 포함합니다:

### 속성
- **type**: 메뉴의 유형을 정의합니다. 'context' 또는 'toolbar' 값을 가질 수 있습니다.
- **label**: 메뉴의 레이블을 설정합니다.

### 메서드
HTMLMenuElement는 기본적으로 DOM 요소로 사용되므로, 표준 DOM 메서드와 속성을 사용할 수 있습니다. 예를 들어, `appendChild`, `removeChild`와 같은 메서드를 통해 메뉴 항목을 동적으로 추가하거나 제거할 수 있습니다.

### 사용법
HTMLMenuElement는 HTML 문서 내에서 다음과 같이 사용됩니다:
```html
<menu id="myMenu" type="context">
    <li>항목 1</li>
    <li>항목 2</li>
    <li>항목 3</li>
</menu>
```

JavaScript로 이 메뉴를 조작할 수 있습니다:
```javascript
const menu = document.getElementById('myMenu');
menu.label = '내 메뉴';
```

## 예제
### 기본 사용 예
```html
<menu id="myMenu" type="context">
    <li>복사</li>
    <li>붙여넣기</li>
    <li>삭제</li>
</menu>
```
```javascript
document.addEventListener('contextmenu', function(e) {
    e.preventDefault();
    const menu = document.getElementById('myMenu');
    menu.style.display = 'block';
    menu.style.left = e.pageX + 'px';
    menu.style.top = e.pageY + 'px';
});
```

### 동적 메뉴 항목 추가
```javascript
const menu = document.getElementById('myMenu');
const newItem = document.createElement('li');
newItem.textContent = '새 항목';
menu.appendChild(newItem);
```

## 설명
HTMLMenuElement 사용 시 주의할 점:
- 브라우저 호환성: 모든 브라우저가 HTMLMenuElement를 지원하지 않으므로, 사용 시 브라우저 호환성을 확인해야 합니다.
- 스타일링: 기본적으로 제공되는 스타일이 없으므로, CSS를 사용하여 메뉴의 모양을 정의해야 합니다.
- 이벤트 처리: 메뉴 항목을 클릭했을 때의 동작을 명시적으로 정의해야 합니다. 기본적으로는 아무런 동작을 하지 않습니다.

## 한 줄 요약
HTMLMenuElement는 JavaScript에서 동적인 메뉴를 생성하고 조작하는 데 유용한 HTML 요소입니다.