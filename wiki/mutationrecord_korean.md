<!--
Meta Description: # MutationRecord: JavaScript의 DOM 변경 감지 및 관리 ## 개요 MutationRecord는 JavaScript의 MutationObserver API의 일부로, DOM의 변경 사항을 감지하고 기록하는데 사용됩니다. 이 객체는 DOM 트리의 ...
Meta Keywords: dom, mutation, console, log, mutationobserver
-->

# MutationRecord: JavaScript의 DOM 변경 감지 및 관리

## 개요
MutationRecord는 JavaScript의 MutationObserver API의 일부로, DOM의 변경 사항을 감지하고 기록하는데 사용됩니다. 이 객체는 DOM 트리의 변화(예: 노드 추가, 제거, 속성 변경 등)를 상세하게 설명하며, 이러한 변경 사항을 효과적으로 관리할 수 있도록 돕습니다.

## 문서화
### 목적
MutationRecord는 DOM의 변화를 추적하고, 이러한 변화를 효과적으로 처리하기 위한 정보를 제공합니다. 이를 통해 웹 애플리케이션은 실시간으로 DOM 변경에 반응하거나, 성능을 최적화할 수 있습니다.

### 사용법
MutationRecord 객체는 MutationObserver의 콜백 함수 내에서 제공됩니다. 이 객체는 각 변경 사항에 대한 여러 속성을 포함하고 있습니다.

#### 주요 속성
- `type`: 발생한 변경의 유형("childList", "attributes", "characterData" 중 하나).
- `target`: 변경이 발생한 DOM 노드.
- `addedNodes`: 추가된 노드 리스트 (NodeList).
- `removedNodes`: 제거된 노드 리스트 (NodeList).
- `previousSibling`: 이전 형제 노드.
- `nextSibling`: 다음 형제 노드.
- `attributeName`: 변경된 속성의 이름 (속성 변경 시).
- `oldValue`: 변경 이전의 속성 값 (속성 변경 시).

### 사용 예시
```javascript
// MutationObserver 생성
const observer = new MutationObserver((mutations) => {
    mutations.forEach((mutation) => {
        console.log('변경 유형:', mutation.type);
        if (mutation.type === 'childList') {
            console.log('추가된 노드:', mutation.addedNodes);
            console.log('제거된 노드:', mutation.removedNodes);
        } else if (mutation.type === 'attributes') {
            console.log('변경된 속성:', mutation.attributeName);
            console.log('이전 값:', mutation.oldValue);
        }
    });
});

// 관찰할 DOM 요소 선택
const targetNode = document.getElementById('target');

// MutationObserver 옵션 설정
const config = {
    childList: true,
    attributes: true,
    attributeOldValue: true,
};

// 관찰 시작
observer.observe(targetNode, config);

// DOM 변경 예시
targetNode.appendChild(document.createElement('div'));
targetNode.setAttribute('data-example', 'newValue');
```

## 설명
MutationRecord를 사용할 때 유의해야 할 점은 다음과 같습니다:
- **성능**: 많은 DOM 변경이 감지될 경우, 관찰자는 많은 수의 MutationRecord를 생성할 수 있습니다. 이는 성능 저하를 초래할 수 있으므로, 필요한 경우에만 사용해야 합니다.
- **콜백 함수**: MutationObserver의 콜백 함수는 변경이 발생할 때마다 호출되므로, 불필요한 연산을 피하기 위해 최적화가 필요합니다.
- **정리**: MutationObserver를 사용한 후에는 `disconnect()` 메서드를 호출하여 관찰을 중지하고 메모리 누수를 방지해야 합니다.

## 한 문장 요약
MutationRecord는 DOM 변경 사항을 추적하고 기록하는 JavaScript 객체로, 웹 애플리케이션이 실시간으로 DOM 변화에 반응할 수 있게 돕습니다.