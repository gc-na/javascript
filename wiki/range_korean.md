<!--
Meta Description: # JavaScript의 Range: 범위 설정 및 사용법 ## 개요 JavaScript에서 "Range"는 문서 내에서 특정 영역을 선택하거나 조작하는 데 사용되는 기능입니다. 주로 DOM(Document Object Model) API의 일부로, 텍스트 또는 노드의...
Meta Keywords: range, document, 객체는, dom, 범위를
-->

# JavaScript의 Range: 범위 설정 및 사용법

## 개요
JavaScript에서 "Range"는 문서 내에서 특정 영역을 선택하거나 조작하는 데 사용되는 기능입니다. 주로 DOM(Document Object Model) API의 일부로, 텍스트 또는 노드의 범위를 정의하고 조작할 수 있게 해줍니다.

## 문서화
### 목적
Range 객체는 DOM 내에서 특정 범위를 정의하고, 선택된 텍스트를 조작하거나 스타일을 적용하는 데 사용됩니다. 이는 사용자 인터페이스(UI)에서 텍스트 편집기나 하이라이터와 같은 기능을 구현할 때 유용합니다.

### 사용법
Range 객체는 다음과 같은 메서드와 프로퍼티를 제공합니다:

- `setStart(node, offset)`: 범위의 시작점을 설정합니다.
- `setEnd(node, offset)`: 범위의 끝점을 설정합니다.
- `collapse(toStart)`: 범위를 하나의 지점으로 축소합니다.
- `extractContents()`: 범위 내의 내용을 삭제하고 반환합니다.
- `cloneContents()`: 범위 내의 내용을 복제하여 반환합니다.

### 세부사항
Range 객체는 `document.createRange()` 메서드를 통해 생성할 수 있습니다. 이 객체는 텍스트를 선택하거나 DOM 요소를 조작하는 데 매우 유용하며, 특히 Rich Text Editor와 같은 복잡한 UI 컴포넌트를 만들 때 필수적입니다.

## 예제
### 기본 사용 예제
```javascript
// 새로운 Range 객체 생성
let range = document.createRange();

// 특정 노드와 오프셋을 설정
let startNode = document.getElementById('start');
let endNode = document.getElementById('end');

range.setStart(startNode, 0);
range.setEnd(endNode, 0);

// 선택한 텍스트를 하이라이트하기
let selection = window.getSelection();
selection.removeAllRanges(); // 기존의 선택 해제
selection.addRange(range); // 새로운 범위 추가
```

## 설명
### 일반적인 실수 및 주의 사항
- **범위 외부의 노드 선택**: 설정하려는 노드가 범위의 시작 및 종료 지점으로 적절하지 않을 경우 오류가 발생할 수 있습니다.
- **중첩된 Range 객체**: 여러 Range 객체를 동시에 조작할 경우 예상치 못한 결과가 발생할 수 있으므로 주의해야 합니다.
- **브라우저 호환성**: 모든 브라우저에서 동일하게 동작하지 않을 수 있으므로, 사용 전에 호환성과 기능을 확인해야 합니다.

## 한 줄 요약
JavaScript의 Range 객체는 DOM 내에서 특정 텍스트 또는 노드의 범위를 정의하고 조작하는 데 유용한 도구입니다.