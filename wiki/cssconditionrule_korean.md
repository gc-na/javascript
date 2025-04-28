<!--
Meta Description: # CSSConditionRule: 자바스크립트에서의 사용법과 예제 ## 개요 CSSConditionRule은 CSS 스타일 시트 내에서 조건부 규칙을 정의할 수 있는 객체입니다. 이 객체는 미디어 쿼리와 같은 조건에 따라 CSS 규칙을 적용하거나 수정하는 데 사용됩니...
Meta Keywords: css, 규칙을, mediarule, 미디어, 있습니다
-->

# CSSConditionRule: 자바스크립트에서의 사용법과 예제

## 개요
CSSConditionRule은 CSS 스타일 시트 내에서 조건부 규칙을 정의할 수 있는 객체입니다. 이 객체는 미디어 쿼리와 같은 조건에 따라 CSS 규칙을 적용하거나 수정하는 데 사용됩니다.

## 문서화
### 목적
CSSConditionRule은 CSS 스타일 시트의 조건부 규칙을 다루기 위해 설계되었습니다. 이를 통해 개발자는 특정 조건에 따라 동적으로 스타일을 변경할 수 있습니다. 이 객체는 CSS @media, @supports와 같은 규칙을 포함하며, 자바스크립트를 통해 이를 조작할 수 있습니다.

### 사용법
CSSConditionRule 객체는 다음과 같이 생성됩니다:
```javascript
let conditionRule = new CSSConditionRule();
```
그러나 일반적으로 직접 생성하기보다는 document.styleSheets의 CSSRuleList에서 가져오는 것이 일반적입니다. 예를 들어, 특정 미디어 쿼리 규칙을 가져올 수 있습니다.

```javascript
let mediaRules = document.styleSheets[0].cssRules;
for (let rule of mediaRules) {
    if (rule instanceof CSSMediaRule) {
        console.log(rule.conditionText); // 미디어 쿼리 조건 출력
    }
}
```

### 세부사항
- **속성**: 
  - `conditionText`: 규칙의 조건 문자열을 반환합니다.
  - `cssRules`: 조건을 만족하는 CSS 규칙의 목록을 반환합니다.
  
- **메서드**:
  - `insertRule()`: 새로운 CSS 규칙을 삽입합니다.
  - `deleteRule()`: 기존 CSS 규칙을 삭제합니다.

## 예제
### 기본 사용 예제
1. 미디어 쿼리 규칙 접근하기:
```javascript
const styleSheet = document.styleSheets[0];
const mediaRule = styleSheet.cssRules[0]; // 첫 번째 규칙 가져오기

if (mediaRule instanceof CSSMediaRule) {
    console.log(mediaRule.conditionText); // "@media screen and (max-width: 600px)" 출력
}
```

2. 새로운 규칙 추가하기:
```javascript
if (mediaRule instanceof CSSMediaRule) {
    mediaRule.insertRule("body { background-color: lightblue; }", mediaRule.cssRules.length);
}
```

## 설명
- **일반적인 함정**: CSSConditionRule을 사용할 때, 올바른 CSS 규칙을 선택하는 것이 중요합니다. 예를 들어, CSS 조건 규칙이 아닌 다른 규칙을 선택하려고 하면 오류가 발생할 수 있습니다. 
- **브라우저 호환성**: 모든 브라우저가 CSSConditionRule을 지원하지 않을 수 있으므로, 사용 전에 호환성을 확인하는 것이 좋습니다.

## 한 줄 요약
CSSConditionRule은 자바스크립트를 사용하여 조건부 CSS 규칙을 동적으로 생성하고 수정하는 데 유용한 객체입니다.