<!--
Meta Description: # CSSPageRule: JavaScript에서 CSS 규칙을 조작하는 방법 ## 개요 CSSPageRule은 JavaScript를 사용하여 CSS 스타일 시트의 페이지 규칙을 생성하고 수정하는 데 사용되는 인터페이스입니다. 이 규칙은 인쇄 및 미디어 쿼리와 같은 페...
Meta Keywords: 규칙을, 페이지, 스타일, csspagerule은, stylesheet
-->

# CSSPageRule: JavaScript에서 CSS 규칙을 조작하는 방법

## 개요
CSSPageRule은 JavaScript를 사용하여 CSS 스타일 시트의 페이지 규칙을 생성하고 수정하는 데 사용되는 인터페이스입니다. 이 규칙은 인쇄 및 미디어 쿼리와 같은 페이지 기반 스타일을 정의하는 데 유용합니다.

## 문서화
CSSPageRule 인터페이스는 CSS 스타일 시트 내에서 페이지 규칙을 나타냅니다. 이러한 규칙은 @page 규칙을 사용하여 정의되며, 인쇄 시에 페이지의 모양을 제어하는 데 도움이 됩니다. CSSPageRule은 CSSStyleRule과 유사하지만, 페이지 레이아웃을 특정하는 데 중점을 둡니다.

### 사용법
CSSPageRule은 JavaScript에서 다음과 같이 사용할 수 있습니다:
1. 스타일 시트를 가져옵니다.
2. 규칙을 추가하거나 수정합니다.

CSSPageRule의 주요 속성과 메서드는 다음과 같습니다:
- **selectorText**: 규칙의 선택기를 나타냅니다.
- **style**: 규칙에 적용된 스타일을 포함하는 CSSStyleDeclaration 객체입니다.
- **insertRule()**: 스타일 시트에 새로운 규칙을 추가합니다.
- **deleteRule()**: 스타일 시트에서 규칙을 삭제합니다.

### 예제
```javascript
// 스타일 시트 가져오기
let stylesheet = document.styleSheets[0];

// 새 페이지 규칙 생성
let pageRule = '@page { margin: 1in; }';

// 페이지 규칙을 스타일 시트에 추가
stylesheet.insertRule(pageRule, stylesheet.cssRules.length);

// 페이지 규칙 수정
let rule = stylesheet.cssRules[stylesheet.cssRules.length - 1];
rule.style.margin = '2in';
```

## 설명
CSSPageRule을 사용할 때 주의해야 할 몇 가지 사항이 있습니다:
- CSSPageRule은 모든 브라우저에서 지원되지 않을 수 있으므로, 호환성을 확인해야 합니다.
- 페이지 규칙은 인쇄 미디어에 주로 사용되므로, 일반적인 웹 페이지에서는 잘 사용되지 않을 수 있습니다.
- 규칙을 추가하거나 삭제할 때 인덱스를 정확히 지정해야 합니다. 잘못된 인덱스는 오류를 발생시킬 수 있습니다.

## 한 줄 요약
CSSPageRule은 JavaScript를 통해 CSS 스타일 시트의 페이지 규칙을 생성하고 관리하는 데 사용되는 인터페이스입니다.