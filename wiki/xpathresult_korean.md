<!--
Meta Description: # XPathResult: JavaScript에서 XPath 결과 처리하기 ## 개요 `XPathResult`는 JavaScript에서 XPath 표현식의 결과를 나타내는 객체로, XML 문서에서 특정 노드 세트를 선택하는 데 사용됩니다. 이는 DOM(Document ...
Meta Keywords: xpathresult, let, xpath, 결과를, result
-->

# XPathResult: JavaScript에서 XPath 결과 처리하기

## 개요
`XPathResult`는 JavaScript에서 XPath 표현식의 결과를 나타내는 객체로, XML 문서에서 특정 노드 세트를 선택하는 데 사용됩니다. 이는 DOM(Document Object Model)과 함께 작업할 때 유용하며, 복잡한 XML 데이터를 효율적으로 탐색하고 처리할 수 있게 해줍니다.

## 문서화

### 목적
`XPathResult` 객체는 XPath 쿼리의 결과를 구조화하여, 개발자가 XML 문서 내에서 원하는 데이터를 쉽게 추출하고 조작할 수 있도록 합니다. 이 객체는 XPath 쿼리의 실행 결과와 관련된 다양한 속성과 메서드를 제공합니다.

### 사용법
`XPathResult` 객체는 `document.evaluate()` 메서드를 통해 생성됩니다. 이 메서드는 XPath 표현식을 기반으로 XML 또는 HTML 문서에서 노드를 검색하는 데 사용됩니다.

#### 기본 문법
```javascript
let result = document.evaluate(xpathExpression, contextNode, namespaceResolver, resultType, result);
```

- `xpathExpression`: XPath 쿼리 문자열.
- `contextNode`: XPath 쿼리를 평가할 기준 노드.
- `namespaceResolver`: 네임스페이스를 해석하기 위한 함수(선택 사항).
- `resultType`: 결과의 유형을 나타내는 정수(예: `XPathResult.ANY_TYPE`).
- `result`: 기존 `XPathResult` 객체(선택 사항).

### 속성과 메서드
`XPathResult` 객체는 다음과 같은 주요 속성과 메서드를 포함합니다:

- **properties**:
  - `resultType`: 결과의 유형.
  - `stringValue`: 문자열 결과를 반환.
  - `numberValue`: 숫자 결과를 반환.
  - `booleanValue`: 불리언 결과를 반환.
  - `singleNodeValue`: 단일 노드를 반환.
  - `invalidIteratorState`: 반복자가 유효하지 않은 경우의 상태.
  
- **메서드**:
  - `iterateNext()`: 다음 노드를 반환하고, 더 이상 노드가 없으면 `null` 반환.
  - `snapshotItem(index)`: 주어진 인덱스의 노드를 반환.

## 예제

### 기본 사용 예제
```javascript
let xmlString = `<books>
                    <book>
                      <title>JavaScript Basics</title>
                      <author>John Doe</author>
                    </book>
                  </books>`;

let parser = new DOMParser();
let xmlDoc = parser.parseFromString(xmlString, "text/xml");

let xpathExpression = "//book/title";
let result = document.evaluate(xpathExpression, xmlDoc, null, XPathResult.STRING_TYPE, null);

console.log(result.stringValue); // "JavaScript Basics"
```

### 반복자를 사용하는 예제
```javascript
let xpathExpression = "//book";
let result = document.evaluate(xpathExpression, xmlDoc, null, XPathResult.ORDERED_NODE_ITERATOR_TYPE, null);

let node;
while (node = result.iterateNext()) {
    console.log(node.getElementsByTagName("title")[0].textContent);
}
// "JavaScript Basics"
```

## 설명
`XPathResult` 객체를 사용할 때 주의해야 할 점은 결과 유형(resultType)을 정확히 설정하는 것입니다. 잘못된 유형을 설정하면 원하는 결과를 얻지 못할 수 있습니다. 또한, 반복자를 사용할 때 끝에 도달했을 때 `null`을 반환하는지 확인하는 것이 중요합니다. 이로 인해 무한 루프에 빠질 위험이 있습니다.

## 한 문장 요약
`XPathResult`는 JavaScript에서 XPath 쿼리의 결과를 표현하고 조작하기 위한 객체입니다.