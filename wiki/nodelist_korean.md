<!--
Meta Description: # NodeList: 자바스크립트에서의 노드 리스트 이해하기 ## 개요 NodeList는 자바스크립트에서 DOM(Document Object Model) 요소를 다루기 위해 사용되는 객체로, HTML 문서의 노드(Node) 컬렉션을 표현합니다. 주로 `document....
Meta Keywords: nodelist는, document, queryselectorall, div, 요소를
-->

# NodeList: 자바스크립트에서의 노드 리스트 이해하기

## 개요
NodeList는 자바스크립트에서 DOM(Document Object Model) 요소를 다루기 위해 사용되는 객체로, HTML 문서의 노드(Node) 컬렉션을 표현합니다. 주로 `document.querySelectorAll()`과 같은 메서드의 결과로 반환됩니다.

## 문서화

### 목적
NodeList는 HTML 문서 내의 여러 노드를 그룹화하여, 이를 순회하거나 조작할 수 있도록 해주는 객체입니다. NodeList는 배열과 유사하지만, 배열의 메서드(예: `map`, `filter`)를 직접 사용할 수 없습니다.

### 사용법
NodeList는 DOM 요소를 선택하는 다양한 메서드에서 생성됩니다. 가장 일반적인 방법은 `document.querySelectorAll()` 메서드를 사용하는 것입니다.

#### 예제
```javascript
// 모든 <p> 요소 선택
const paragraphs = document.querySelectorAll('p');

// NodeList를 순회하며 각 <p> 요소의 텍스트 내용 출력
paragraphs.forEach((paragraph) => {
    console.log(paragraph.textContent);
});
```

### 세부사항
- NodeList는 `length` 프로퍼티를 가지며, 이는 포함된 노드의 수를 나타냅니다.
- NodeList는 정적(dynamic)이고, 이는 DOM의 변경 사항이 NodeList에 반영되지 않음을 의미합니다.
- HTMLCollection과 유사하지만, NodeList는 다양한 노드 유형(예: 요소 노드, 텍스트 노드 등)을 포함할 수 있습니다.

## 예제
```javascript
// 모든 <div> 요소를 선택
const divs = document.querySelectorAll('div');

// 각 <div>의 배경색을 변경
divs.forEach((div) => {
    div.style.backgroundColor = 'lightblue';
});
```

```javascript
// 특정 클래스명을 가진 모든 요소 선택
const items = document.querySelectorAll('.item');

// 선택한 요소의 수 출력
console.log(`선택된 요소의 수: ${items.length}`);
```

## 설명
NodeList를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:
- NodeList는 배열처럼 보이지만, 배열 메서드를 사용할 수 없으므로, `Array.from()` 또는 스프레드 연산자(...)를 사용해 배열로 변환해야 합니다.
- NodeList는 DOM의 변화를 반영하지 않으므로, 동적으로 변경되는 목록을 다룰 때는 주의가 필요합니다. 예를 들어, 페이지에서 요소를 추가하거나 제거할 경우, NodeList는 업데이트되지 않습니다.

## 한 줄 요약
NodeList는 자바스크립트에서 여러 DOM 노드를 표현하는 객체로, `document.querySelectorAll()` 메서드를 통해 생성됩니다.