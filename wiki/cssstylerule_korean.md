<!--
Meta Description: # CSSStyleRule: 자바스크립트에서 CSS 스타일 규칙 다루기 ## 개요 CSSStyleRule은 JavaScript에서 CSS 스타일 규칙을 표현하고 조작하는 데 사용되는 객체입니다. 이 객체는 CSS 스타일 시트 내의 규칙을 다루는 데 유용하며, 스타일을 ...
Meta Keywords: 스타일, 규칙을, css, 있습니다, 속성을
-->

# CSSStyleRule: 자바스크립트에서 CSS 스타일 규칙 다루기

## 개요
CSSStyleRule은 JavaScript에서 CSS 스타일 규칙을 표현하고 조작하는 데 사용되는 객체입니다. 이 객체는 CSS 스타일 시트 내의 규칙을 다루는 데 유용하며, 스타일을 프로그래밍적으로 변경하거나 읽어오는 데 활용됩니다.

## 문서화
### 목적
CSSStyleRule은 CSS 규칙을 자바스크립트로 다룰 수 있게 해 주며, 이를 통해 웹 페이지의 스타일을 동적으로 조작할 수 있습니다. 이 객체는 스타일 시트의 각 규칙을 나타내며, 선택자, 스타일 속성 및 값을 포함합니다.

### 사용법
CSSStyleRule 객체는 `CSSStyleSheet` 객체의 `cssRules` 또는 `rules` 속성을 통해 접근할 수 있습니다. 이 속성은 스타일 시트 내의 모든 규칙을 배열 형태로 반환합니다. 각 규칙은 CSSStyleRule 객체를 통해 접근할 수 있으며, 선택자와 스타일 속성을 수정할 수 있습니다.

### 세부사항
- `selectorText`: CSS 규칙의 선택자를 나타내는 문자열입니다.
- `style`: 해당 규칙의 CSS 스타일을 조작할 수 있는 CSSStyleDeclaration 객체입니다.

## 예제
### 기본 사용 예제
```javascript
// 문서의 첫 번째 스타일 시트를 가져옵니다.
const styleSheet = document.styleSheets[0];

// 첫 번째 규칙을 가져옵니다.
const cssRule = styleSheet.cssRules[0];

// 선택자와 스타일 속성을 출력합니다.
console.log(cssRule.selectorText); // 예: ".example"
console.log(cssRule.style.cssText); // 예: "color: red; font-size: 16px;"

// 스타일 속성을 변경합니다.
cssRule.style.color = "blue";
```

## 설명
- **일반적인 함정**: `cssRules` 속성에 접근할 때, 해당 스타일 시트가 CORS 정책을 위반하면 접근할 수 없습니다. 이 경우, `SecurityError`가 발생할 수 있습니다.
- **스타일 시트의 순서**: 여러 스타일 시트가 있는 경우, 각 스타일 시트의 규칙은 인덱스 순서로 정렬됩니다. 따라서 인덱스를 잘못 지정하면 예기치 않은 규칙을 수정할 수 있습니다.
- **브라우저 호환성**: 모든 브라우저에서 동일한 방식으로 동작하지 않을 수 있으므로, 브라우저 호환성을 확인하는 것이 중요합니다.

## 한 줄 요약
CSSStyleRule은 자바스크립트에서 CSS 스타일 규칙을 표현하고 조작할 수 있는 객체입니다.