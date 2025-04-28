<!--
Meta Description: # CSSRule: JavaScript로 CSS 규칙을 다루는 방법 ## 개요 `CSSRule`은 JavaScript에서 CSS 스타일 규칙을 나타내는 객체로, DOM의 스타일시트와 관련된 작업을 수행할 수 있는 인터페이스를 제공합니다. 이 객체를 사용하면 CSS 규칙...
Meta Keywords: 규칙을, stylesheets, cssrule, css, const
-->

# CSSRule: JavaScript로 CSS 규칙을 다루는 방법

## 개요
`CSSRule`은 JavaScript에서 CSS 스타일 규칙을 나타내는 객체로, DOM의 스타일시트와 관련된 작업을 수행할 수 있는 인터페이스를 제공합니다. 이 객체를 사용하면 CSS 규칙을 동적으로 수정하거나 생성할 수 있습니다.

## 문서화

### 목적
`CSSRule` 객체는 CSS 스타일시트 내의 개별 규칙을 표현하는 데 사용됩니다. 이 객체는 CSS의 다양한 규칙(예: 선택자, 스타일 속성) 및 관련 정보를 조작할 수 있는 메소드를 제공합니다.

### 사용법
`CSSRule`은 JavaScript의 `document.styleSheets`를 통해 접근할 수 있는 스타일시트 내의 규칙을 참조합니다. 각 스타일시트는 여러 개의 규칙을 가질 수 있으며, `CSSRule` 객체는 이러한 규칙을 나타냅니다.

#### 기본 속성
- `type`: 규칙의 유형을 나타내는 숫자입니다. (예: `CSSStyleRule`, `CSSMediaRule` 등)
- `selectorText`: 규칙의 선택자를 나타내는 문자열입니다.
- `style`: 해당 규칙에 적용된 스타일을 나타내는 `CSSStyleDeclaration` 객체입니다.

#### 기본 메소드
- `deleteRule(index)`: 특정 인덱스의 규칙을 삭제합니다.
- `insertRule(rule, index)`: 특정 인덱스에 새로운 규칙을 삽입합니다.

## 예제

### 예제 1: 스타일시트의 규칙 접근하기
```javascript
// 모든 스타일시트를 가져온 후, 첫 번째 스타일시트의 첫 번째 규칙을 출력
const styleSheets = document.styleSheets;
const firstRule = styleSheets[0].cssRules[0];
console.log(firstRule.selectorText); // 규칙의 선택자 출력
```

### 예제 2: 새로운 규칙 추가하기
```javascript
// 첫 번째 스타일시트에 새로운 규칙 추가
const styleSheets = document.styleSheets;
const newRule = "body { background-color: lightblue; }";
styleSheets[0].insertRule(newRule, styleSheets[0].cssRules.length);
```

### 예제 3: 규칙 삭제하기
```javascript
// 첫 번째 스타일시트의 첫 번째 규칙 삭제
const styleSheets = document.styleSheets;
styleSheets[0].deleteRule(0);
```

## 설명
`CSSRule`을 사용할 때 주의해야 할 점은 다음과 같습니다:

- **규칙의 유형**: 각 `CSSRule`은 다양한 유형이 있으며, 이를 잘 이해하고 사용해야 합니다. 예를 들어, `CSSStyleRule`은 일반적인 스타일 규칙을 나타내고, `CSSMediaRule`은 미디어 쿼리를 나타냅니다.
- **브라우저 지원**: 모든 브라우저가 동일하게 `CSSRule`을 지원하지 않을 수 있으며, 특히 구형 브라우저에서는 예외가 발생할 수 있습니다.
- **규칙 인덱스**: 스타일시트의 규칙은 인덱스를 기반으로 관리되므로, 삭제나 삽입 시 인덱스가 변경될 수 있습니다. 따라서 인덱스를 조작할 때 주의가 필요합니다.

## 한 줄 요약
`CSSRule`은 JavaScript에서 CSS 스타일 규칙을 동적으로 조작할 수 있는 객체입니다.