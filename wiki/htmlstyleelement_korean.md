<!--
Meta Description: # HTMLStyleElement: JavaScript에서 스타일 요소를 다루는 방법 ## 개요 `HTMLStyleElement`는 HTML 문서에서 `<style>` 요소를 나타내며, JavaScript를 통해 동적으로 스타일을 조작할 수 있는 기능을 제공합니다. 이...
Meta Keywords: style, css, htmlstyleelement, 스타일, 스타일을
-->

# HTMLStyleElement: JavaScript에서 스타일 요소를 다루는 방법

## 개요
`HTMLStyleElement`는 HTML 문서에서 `<style>` 요소를 나타내며, JavaScript를 통해 동적으로 스타일을 조작할 수 있는 기능을 제공합니다. 이를 통해 웹 페이지의 스타일을 프로그래밍적으로 추가, 수정 또는 삭제할 수 있습니다.

## 문서화
`HTMLStyleElement`는 DOM의 일부로, HTML 문서에서 스타일 시트를 정의하는 데 사용됩니다. 이 요소는 CSS 규칙을 포함하며, 이를 통해 문서의 시각적 표현을 제어할 수 있습니다. `HTMLStyleElement`는 `style` 속성을 통해 CSS 스타일을 설정하거나, `sheet` 속성을 통해 CSSStyleSheet 객체에 접근할 수 있습니다.

### 사용법
자바스크립트에서 `HTMLStyleElement`를 사용하기 위해서는 다음과 같은 방법으로 접근할 수 있습니다:

1. **요소 생성**: `document.createElement`를 사용하여 새로운 `<style>` 요소를 생성합니다.
2. **스타일 추가**: `textContent` 또는 `innerHTML`을 사용하여 CSS 규칙을 추가합니다.
3. **문서에 추가**: `document.head` 또는 `document.body`에 생성한 `<style>` 요소를 추가합니다.

### 세부정보
- **속성**:
  - `type`: 스타일 시트의 타입을 지정합니다 (예: "text/css").
  - `media`: 스타일 시트가 적용될 미디어 유형을 정의합니다.
  - `sheet`: 해당 스타일 요소의 CSSStyleSheet 객체에 대한 참조를 제공합니다.

- **메서드**: 
  - `insertRule()`: 새로운 CSS 규칙을 스타일 시트에 추가합니다.
  - `deleteRule()`: 기존 CSS 규칙을 삭제합니다.

## 예제
다음은 `HTMLStyleElement`를 사용하여 동적으로 스타일을 추가하는 기본 예제입니다.

```javascript
// 새로운 <style> 요소 생성
let style = document.createElement('style');

// CSS 규칙 추가
style.textContent = `
  body {
    background-color: lightblue;
  }
  h1 {
    color: navy;
  }
`;

// <style> 요소를 head에 추가
document.head.appendChild(style);
```

## 설명
`HTMLStyleElement`를 사용할 때 주의해야 할 점은 CSS 규칙의 적용 순서입니다. 나중에 추가된 스타일이 이전 스타일을 덮어쓸 수 있으므로, 스타일 적용 순서를 고려해야 합니다. 또한, 동적으로 스타일을 추가할 때는 성능을 고려하여 너무 많은 스타일을 반복적으로 추가하지 않도록 주의해야 합니다.

## 한 문장 요약
`HTMLStyleElement`는 JavaScript를 통해 HTML 문서에서 동적으로 CSS 스타일을 추가하고 조작할 수 있는 기능을 제공합니다.