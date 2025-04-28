<!--
Meta Description: # CSSStyleSheet: 자바스크립트에서 CSS 스타일 시트 조작하기 ## 개요 `CSSStyleSheet`는 자바스크립트를 사용하여 CSS 스타일 시트를 동적으로 조작할 수 있게 해주는 객체입니다. 이를 통해 웹 개발자는 스타일을 추가, 수정 또는 삭제하여 사용...
Meta Keywords: 스타일, cssstylesheet, css, 규칙을, 시트를
-->

# CSSStyleSheet: 자바스크립트에서 CSS 스타일 시트 조작하기

## 개요
`CSSStyleSheet`는 자바스크립트를 사용하여 CSS 스타일 시트를 동적으로 조작할 수 있게 해주는 객체입니다. 이를 통해 웹 개발자는 스타일을 추가, 수정 또는 삭제하여 사용자 경험을 향상시킬 수 있습니다.

## 문서화
`CSSStyleSheet`는 HTML 문서에서 사용되는 CSS 스타일 시트를 나타내며, JavaScript를 통해 접근할 수 있습니다. 이 객체는 다양한 속성과 메서드를 제공하여 스타일 규칙을 조작할 수 있습니다.

### 목적
- 웹 페이지의 스타일을 동적으로 변경할 수 있게 해줍니다.
- CSS 스타일 시트를 생성하고 수정하는 기능을 제공합니다.

### 사용법
`CSSStyleSheet` 객체는 일반적으로 `document.styleSheets` 컬렉션을 통해 접근합니다. 각 스타일 시트는 여러 개의 규칙을 포함하고 있으며, 이들 규칙은 `insertRule()` 및 `deleteRule()` 메서드를 통해 조작할 수 있습니다.

### 주요 속성 및 메서드
- **`cssRules`**: 스타일 시트의 모든 규칙을 포함하는 컬렉션입니다.
- **`insertRule(rule, index)`**: 지정된 위치에 새로운 규칙을 추가합니다.
- **`deleteRule(index)`**: 지정된 위치의 규칙을 삭제합니다.

## 예제
다음은 `CSSStyleSheet`를 사용하여 스타일 시트를 조작하는 기본 예제입니다.

```javascript
// 첫 번째 스타일 시트 가져오기
const styleSheet = document.styleSheets[0];

// 새로운 규칙 추가
styleSheet.insertRule('body { background-color: lightblue; }', styleSheet.cssRules.length);

// 규칙 삭제
styleSheet.deleteRule(0); // 첫 번째 규칙 삭제
```

## 설명
- **공통적인 실수**: `insertRule` 메서드를 사용할 때 규칙 문자열이 올바른 CSS 구문이어야 합니다. 잘못된 구문은 오류를 발생시킵니다.
- **인덱스 문제**: 규칙을 삭제할 때 인덱스가 올바른지 확인해야 합니다. 잘못된 인덱스를 사용하면 예외가 발생합니다.
- **브라우저 호환성**: 모든 브라우저가 `CSSStyleSheet` API를 동일하게 지원하지 않을 수 있으므로, 특정 기능을 사용하기 전 호환성을 검토해야 합니다.

## 한 줄 요약
`CSSStyleSheet`는 자바스크립트를 통해 웹 페이지의 CSS 스타일 시트를 동적으로 조작할 수 있게 해주는 객체입니다.