<!--
Meta Description: # NodeIterator: JavaScript에서 DOM 노드를 순회하는 방법 ## 개요 NodeIterator는 JavaScript에서 DOM(Document Object Model) 노드를 순회하는 데 사용되는 인터페이스입니다. 이를 통해 개발자는 특정 조건에 맞...
Meta Keywords: 노드를, dom, nodeiterator는, 있습니다, nodeiterator
-->

# NodeIterator: JavaScript에서 DOM 노드를 순회하는 방법

## 개요
NodeIterator는 JavaScript에서 DOM(Document Object Model) 노드를 순회하는 데 사용되는 인터페이스입니다. 이를 통해 개발자는 특정 조건에 맞는 노드를 효율적으로 탐색하고 조작할 수 있습니다.

## 문서화

### 목적
NodeIterator는 DOM 트리의 노드를 반복적으로 순회할 수 있도록 설계되었습니다. 이 인터페이스는 주어진 조건에 맞는 노드를 필터링하여 순회하는 기능을 제공합니다.

### 사용법
NodeIterator는 `document.createNodeIterator()` 메서드를 통해 생성됩니다. 이 메서드는 다음과 같은 매개변수를 받습니다:

1. **root**: 탐색을 시작할 DOM 노드.
2. **whatToShow**: 노드 유형을 필터링하는 정수 값. 기본적으로 모든 노드가 포함됩니다.
3. **filter**: 선택적으로 노드에 대한 필터링 함수를 제공할 수 있습니다.
4. **entityReferenceExpansion**: 참조 노드를 확장할 지 여부를 결정하는 부울 값.

#### NodeIterator의 기본 메서드
- **nextNode()**: 다음 노드로 이동하고 그 노드를 반환합니다.
- **previousNode()**: 이전 노드로 이동하고 그 노드를 반환합니다.
- **detach()**: NodeIterator를 해제하여 더 이상 사용할 수 없도록 합니다.

## 예제

```javascript
// DOM 노드를 순회하는 NodeIterator 예제
const root = document.getElementById('myElement');
const nodeIterator = document.createNodeIterator(
  root,
  NodeFilter.SHOW_ELEMENT,
  null,
  false
);

let currentNode;
while (currentNode = nodeIterator.nextNode()) {
  console.log(currentNode.tagName); // 현재 노드의 태그 이름을 출력합니다.
}
```

## 설명
NodeIterator를 사용할 때 주의해야 할 점은 다음과 같습니다:

- `whatToShow` 매개변수를 적절히 설정하지 않으면 원치 않는 노드까지 포함될 수 있습니다. 예를 들어, `NodeFilter.SHOW_TEXT`를 사용하면 텍스트 노드만 반환됩니다.
- 필터 기능을 사용할 때는 반드시 함수가 반환하는 값이 `NodeFilter.FILTER_ACCEPT` 또는 `NodeFilter.FILTER_REJECT` 중 하나여야 합니다.
- NodeIterator는 생성된 후 DOM이 변경되면 영향을 받을 수 있습니다. 노드가 추가되거나 삭제되면 NodeIterator는 올바르지 않은 상태가 될 수 있습니다.

## 한 줄 요약
NodeIterator는 JavaScript에서 DOM 노드를 효율적으로 순회하고 필터링하는 인터페이스입니다.