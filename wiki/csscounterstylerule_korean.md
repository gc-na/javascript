<!--
Meta Description: # CSSCounterStyleRule: 자바스크립트에서의 사용법과 기능 ## 개요 CSSCounterStyleRule은 CSS에서 사용자 정의 카운터 스타일을 정의하는 데 사용되는 규칙으로, 자바스크립트를 통해 이를 조작할 수 있습니다. 이 규칙을 활용하면 리스트 항...
Meta Keywords: 카운터, style, stylesheet, document, 스타일을
-->

# CSSCounterStyleRule: 자바스크립트에서의 사용법과 기능

## 개요
CSSCounterStyleRule은 CSS에서 사용자 정의 카운터 스타일을 정의하는 데 사용되는 규칙으로, 자바스크립트를 통해 이를 조작할 수 있습니다. 이 규칙을 활용하면 리스트 항목의 숫자 형식을 사용자 정의할 수 있어, 웹 페이지 디자인의 유연성을 높여줍니다.

## 문서화
### 목적
CSSCounterStyleRule은 웹 페이지에서 카운터 스타일을 생성하고 조작하는 기능을 제공합니다. 이를 통해 개발자는 리스트의 숫자 또는 기호 앞에 표시되는 형식을 자유롭게 설정할 수 있습니다.

### 사용법
CSSCounterStyleRule은 CSSStyleSheet의 `insertRule` 메서드를 사용하여 추가할 수 있으며, DOM의 특정 요소에 적용할 수 있습니다. 기본적으로, 카운터 스타일은 `@counter-style` 규칙에 따라 정의됩니다.

#### 예시 코드
```javascript
// 카운터 스타일 추가
const styleSheet = document.styleSheets[0];
styleSheet.insertRule(`
  @counter-style my-style {
    system: numeric;
    symbols: "Ⅰ, Ⅱ, Ⅲ";
  }
`, styleSheet.cssRules.length);

// 카운터 스타일 적용
const list = document.querySelector('ul');
list.style.listStyleType = 'my-style';
```

## 예제
### 기본 사용 예시
```javascript
// 카운터 스타일 정의
const styleSheet = document.styleSheets[0];
styleSheet.insertRule(`
  @counter-style custom-counter {
    system: numeric;
    symbols: "A, B, C, D";
  }
`, styleSheet.cssRules.length);

// 리스트에 적용
const ul = document.createElement('ul');
ul.style.listStyleType = 'custom-counter';
document.body.appendChild(ul);

for (let i = 0; i < 4; i++) {
  const li = document.createElement('li');
  li.textContent = `항목 ${i + 1}`;
  ul.appendChild(li);
}
```

## 설명
- **공통 오류**: CSSCounterStyleRule을 정의할 때 시스템이 지원하지 않는 카운터 스타일을 사용하면 예상치 못한 결과가 발생할 수 있습니다.
- **브라우저 지원**: 일부 오래된 브라우저에서는 지원하지 않을 수 있으므로, 반드시 호환성에 대한 검토가 필요합니다.
- **디자인 고려**: 사용자 정의 카운터 스타일을 사용할 때는 전체적인 디자인과 일관성을 유지하는 것이 중요합니다.

## 한 줄 요약
CSSCounterStyleRule은 자바스크립트를 통해 사용자 정의 카운터 스타일을 만들고 적용할 수 있게 해주는 CSS 규칙입니다.