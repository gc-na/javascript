<!--
Meta Description: # StaticRange: 자바스크립트에서의 정적 범위 객체 ## 개요 `StaticRange`는 자바스크립트에서 텍스트 노드와 DOM 요소의 정적 범위를 정의하는 객체로, 주로 문서 내에서 텍스트 선택 및 범위 작업을 보다 효율적으로 수행하는 데 사용됩니다. ## 문...
Meta Keywords: staticrange, dom, 텍스트, 범위를, 정의하는
-->

# StaticRange: 자바스크립트에서의 정적 범위 객체

## 개요
`StaticRange`는 자바스크립트에서 텍스트 노드와 DOM 요소의 정적 범위를 정의하는 객체로, 주로 문서 내에서 텍스트 선택 및 범위 작업을 보다 효율적으로 수행하는 데 사용됩니다.

## 문서화

### 목적
`StaticRange`는 특정 DOM 요소 내의 텍스트 또는 다른 요소들을 선택하여 그 범위를 정의하는 데 사용됩니다. 이 객체는 동적 범위와는 달리, 생성 시점에 선택된 상태를 유지합니다.

### 사용법
`StaticRange` 객체는 `new StaticRange()` 생성자를 통해 생성됩니다. 이 생성자는 두 개의 매개변수를 필요로 합니다: 시작과 끝의 DOM 요소 또는 텍스트 노드입니다. 다음은 기본적인 문법입니다:

```javascript
let staticRange = new StaticRange({
    startContainer: <startNode>,
    startOffset: <startOffset>,
    endContainer: <endNode>,
    endOffset: <endOffset>
});
```

### 세부사항
- `startContainer`: 범위의 시작을 정의하는 DOM 요소 또는 텍스트 노드입니다.
- `startOffset`: 시작 컨테이너 내의 시작 위치를 나타내는 정수입니다.
- `endContainer`: 범위의 끝을 정의하는 DOM 요소 또는 텍스트 노드입니다.
- `endOffset`: 끝 컨테이너 내의 끝 위치를 나타내는 정수입니다.

`StaticRange` 객체는 범위를 정의한 후, 여러 메서드를 통해 해당 범위 내의 텍스트를 조작하거나 읽을 수 있도록 도와줍니다.

## 예제

### 기본 사용 예제
```javascript
// 문서의 특정 요소에서 StaticRange 생성
const startNode = document.getElementById('startElement');
const endNode = document.getElementById('endElement');

const staticRange = new StaticRange({
    startContainer: startNode,
    startOffset: 0,
    endContainer: endNode,
    endOffset: endNode.childNodes.length
});

// 범위의 정보 출력
console.log(staticRange.startContainer); // 시작 노드 출력
console.log(staticRange.endContainer); // 끝 노드 출력
```

## 설명
`StaticRange`는 범위를 정의하는 데 유용하지만, 몇 가지 주의사항이 있습니다:

1. **범위의 유효성**: `startContainer`와 `endContainer`는 반드시 DOM 트리 내의 유효한 노드여야 하며, 선택하는 범위가 서로 겹치지 않아야 합니다.
2. **정적 특성**: `StaticRange`는 동적이지 않으므로, DOM 변경 후에는 범위가 유효하지 않을 수 있습니다. 이 경우 새로운 범위를 생성해야 합니다.
3. **브라우저 호환성**: 모든 브라우저에서 지원되지 않을 수 있으므로, 호환성을 확인해야 합니다.

## 한 줄 요약
`StaticRange`는 자바스크립트에서 DOM 요소 내의 정적 텍스트 범위를 정의하고 조작하는 객체입니다.