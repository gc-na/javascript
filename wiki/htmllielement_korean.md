<!--
Meta Description: # HTMLLIElement: JavaScript에서의 역할과 활용 ## 개요 HTMLLIElement는 HTML의 `<li>` 요소를 나타내는 JavaScript 객체로, 리스트 항목을 조작하고 관리하는 데 사용됩니다. 이 객체는 웹 페이지에서 목록 항목을 동적으로 ...
Meta Keywords: 리스트, 항목을, document, let, innerhtml
-->

# HTMLLIElement: JavaScript에서의 역할과 활용

## 개요
HTMLLIElement는 HTML의 `<li>` 요소를 나타내는 JavaScript 객체로, 리스트 항목을 조작하고 관리하는 데 사용됩니다. 이 객체는 웹 페이지에서 목록 항목을 동적으로 생성하거나 수정할 때 매우 유용합니다.

## 문서화
### 목적
HTMLLIElement는 HTML 문서에서 `<li>` 태그의 속성과 메서드를 활용하여 리스트 항목을 제어하는 데 사용됩니다. 이 객체를 사용하면 JavaScript를 통해 리스트 항목을 추가, 삭제 및 수정할 수 있습니다.

### 사용법
HTMLLIElement는 DOM(Document Object Model)에서 `<li>` 요소를 생성하거나 선택할 때 사용됩니다. 이를 통해 프로그래밍적으로 리스트 항목을 조작할 수 있습니다.

#### 기본 속성
- `value`: 리스트 항목의 값으로, 순서가 있는 리스트(즉, `<ol>`)에서 사용됩니다.
- `innerHTML`: 리스트 항목의 HTML 콘텐츠를 설정하거나 가져옵니다.
- `className`: 리스트 항목에 적용된 CSS 클래스를 설정합니다.

#### 기본 메서드
- `remove()`: 리스트 항목을 DOM에서 제거합니다.
- `setAttribute(name, value)`: 요소의 속성을 설정합니다.
- `getAttribute(name)`: 요소의 속성 값을 가져옵니다.

## 예제
### 기본 사용 예제
```javascript
// 새로운 리스트 항목 생성
let li = document.createElement('li');
li.innerHTML = '새로운 리스트 항목';
document.getElementById('myList').appendChild(li);

// 기존 리스트 항목의 값 변경
let firstItem = document.querySelector('li');
firstItem.innerHTML = '수정된 리스트 항목';

// 리스트 항목 제거
let lastItem = document.querySelector('li:last-child');
lastItem.remove();
```

### 순서가 있는 리스트 예제
```javascript
let orderedList = document.createElement('ol');

// 리스트 항목 추가
for (let i = 1; i <= 5; i++) {
    let li = document.createElement('li');
    li.value = i; // 순서 값 설정
    li.innerHTML = `항목 ${i}`;
    orderedList.appendChild(li);
}

document.body.appendChild(orderedList);
```

## 설명
HTMLLIElement를 사용할 때 주의해야 할 사항은 다음과 같습니다:
- DOM에 추가되기 전에는 리스트 항목의 속성을 설정할 수 없으므로, 필요한 속성은 생성 후 즉시 설정해야 합니다.
- `innerHTML` 속성을 사용할 때, HTML 태그가 포함된 문자열을 입력하면 해당 태그가 해석되어 삽입됩니다. 따라서 XSS(교차 사이트 스크립팅) 공격에 주의해야 합니다.
- 리스트 항목을 삭제하면, 해당 항목에 대한 참조가 더 이상 유효하지 않으므로 이후에 이를 접근하려고 하면 오류가 발생할 수 있습니다.

## 한줄 요약
HTMLLIElement는 JavaScript에서 리스트 항목을 조작하는 데 사용되는 HTML의 `<li>` 요소를 나타내는 객체입니다.