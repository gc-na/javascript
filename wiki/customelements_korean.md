<!--
Meta Description: # customElements: JavaScript에서 커스텀 HTML 요소 만들기 ## 개요 `customElements`는 웹 컴포넌트의 핵심 기능으로, 개발자가 자신만의 HTML 요소를 정의하고 사용할 수 있게 해줍니다. 이 기능을 통해 재사용 가능한 UI 컴포넌...
Meta Keywords: 커스텀, html, customelements, 요소의, element
-->

# customElements: JavaScript에서 커스텀 HTML 요소 만들기

## 개요
`customElements`는 웹 컴포넌트의 핵심 기능으로, 개발자가 자신만의 HTML 요소를 정의하고 사용할 수 있게 해줍니다. 이 기능을 통해 재사용 가능한 UI 컴포넌트를 만들고, HTML 문서에 통합할 수 있습니다.

## 문서화
### 목적
`customElements` API는 사용자가 새로운 HTML 태그를 만들고, 해당 태그에 대한 동작과 스타일을 정의할 수 있도록 합니다. 이로 인해 HTML의 확장성이 증가하고 코드의 재사용성이 향상됩니다.

### 사용법
`customElements` API는 `define` 메서드를 사용하여 새로운 커스텀 요소를 정의합니다. 아래는 기본적인 사용 방법입니다.

1. **클래스 정의**: 커스텀 요소의 동작을 정의하는 클래스를 만듭니다. 이 클래스는 `HTMLElement`를 상속받아야 합니다.
2. **요소 등록**: `customElements.define()` 메서드를 사용하여 커스텀 요소를 등록합니다. 이 메서드는 두 개의 인자를 받습니다: 요소의 이름과 클래스입니다.

### 세부사항
- 커스텀 요소의 이름은 반드시 하이픈(-)이 포함되어야 합니다. 예: `my-element`
- 클래스를 정의할 때, `connectedCallback`, `disconnectedCallback`, `attributeChangedCallback`과 같은 라이프사이클 메서드를 오버라이드하여 요소의 동작을 제어할 수 있습니다.
- 커스텀 요소는 HTML 문서 내에서 일반 HTML 요소처럼 사용할 수 있습니다.

## 예제
### 기본 사용 예제
```javascript
// 1. 커스텀 요소 클래스 정의
class MyElement extends HTMLElement {
    constructor() {
        super();
        const shadow = this.attachShadow({ mode: 'open' });
        shadow.innerHTML = `<p>Hello, Custom Element!</p>`;
    }
}

// 2. 커스텀 요소 등록
customElements.define('my-element', MyElement);
```
### HTML에서 사용
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Custom Element 예제</title>
</head>
<body>
    <my-element></my-element>
    <script src="script.js"></script>
</body>
</html>
```

## 설명
- **이름 규칙**: 커스텀 요소의 이름에 하이픈을 포함해야 하며, 그렇지 않으면 오류가 발생합니다.
- **속성 처리**: 커스텀 요소의 속성 변경을 감지하려면 `attributeChangedCallback`을 반드시 구현해야 합니다.
- **Shadow DOM**: 커스텀 요소 내에서 Shadow DOM을 사용하여 스타일과 구조를 캡슐화할 수 있습니다. 이는 다른 요소와의 충돌을 방지합니다.

## 한 문장 요약
`customElements` API를 사용하면 개발자가 자신만의 HTML 요소를 정의하고, 재사용 가능한 웹 컴포넌트를 쉽게 만들 수 있습니다.