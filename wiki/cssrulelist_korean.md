<!--
Meta Description: # CSSRuleList: 자바스크립트에서의 CSS 규칙 목록 ## 개요 `CSSRuleList`는 JavaScript에서 CSS 스타일 규칙의 목록을 나타내는 객체입니다. 이 객체는 `CSSStyleSheet` 인터페이스의 일부로, 스타일 시트 내의 모든 규칙을 관리...
Meta Keywords: 규칙을, cssrules, cssrulelist, 스타일, rules
-->

# CSSRuleList: 자바스크립트에서의 CSS 규칙 목록

## 개요
`CSSRuleList`는 JavaScript에서 CSS 스타일 규칙의 목록을 나타내는 객체입니다. 이 객체는 `CSSStyleSheet` 인터페이스의 일부로, 스타일 시트 내의 모든 규칙을 관리하고 조작하는 데 사용됩니다.

## 문서화
### 목적
`CSSRuleList`는 특정 스타일 시트에 포함된 모든 CSS 규칙을 배열처럼 다룰 수 있도록 해줍니다. 이를 통해 개발자는 기존의 스타일 규칙을 조회, 수정 또는 삭제할 수 있습니다.

### 사용법
`CSSRuleList` 객체는 `CSSStyleSheet`의 `cssRules` 또는 `rules` 속성을 통해 접근할 수 있습니다. `cssRules` 속성은 읽기 전용이며, 스타일 시트에 정의된 모든 규칙을 포함하는 `CSSRuleList` 객체를 반환합니다.

#### 예시
```javascript
// 스타일 시트 가져오기
var styleSheet = document.styleSheets[0];

// CSS 규칙 목록 가져오기
var cssRules = styleSheet.cssRules;

// 모든 규칙을 콘솔에 출력하기
for (var i = 0; i < cssRules.length; i++) {
    console.log(cssRules[i].cssText);
}
```

## 예제
### 기본 사용 예제
```javascript
// 첫 번째 스타일 시트에서 모든 CSS 규칙을 출력
var sheet = document.styleSheets[0];
var rules = sheet.cssRules;

for (var i = 0; i < rules.length; i++) {
    console.log(`규칙 ${i + 1}: ${rules[i].cssText}`);
}

// 특정 규칙 수정
if (rules.length > 0) {
    rules[0].style.color = 'blue'; // 첫 번째 규칙의 글자색을 파란색으로 변경
}
```

## 설명
`CSSRuleList`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **읽기 전용 속성**: `cssRules`는 읽기 전용이므로 새로운 규칙을 추가하거나 삭제할 수는 없습니다. 이를 위해서는 `insertRule()` 또는 `deleteRule()` 메서드를 사용해야 합니다.
- **IE 호환성**: Internet Explorer에서는 `rules` 속성을 사용해야 할 수 있으며, `cssRules` 속성이 지원되지 않을 수 있습니다. 이를 고려하여 코드 작성 시 브라우저 호환성을 확인해야 합니다.
- **규칙 유형**: `CSSRuleList` 내의 각 규칙은 다양한 유형(CSSStyleRule, CSSMediaRule 등)을 가질 수 있으므로, 규칙을 조작하기 전에 타입을 확인하는 것이 좋습니다.

## 한 줄 요약
`CSSRuleList`는 자바스크립트에서 CSS 스타일 시트 내의 모든 규칙을 배열처럼 다룰 수 있게 하는 객체입니다.