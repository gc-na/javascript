<!--
Meta Description: # CustomElementRegistry: JavaScript의 사용자 정의 요소 등록기 ## 개요 CustomElementRegistry는 JavaScript에서 사용자 정의 HTML 요소를 정의하고 등록할 수 있는 API입니다. 이 API를 사용하면 웹 개발자는 ...
Meta Keywords: 사용자, 요소를, html, 있습니다, 요소의
-->

# CustomElementRegistry: JavaScript의 사용자 정의 요소 등록기

## 개요
CustomElementRegistry는 JavaScript에서 사용자 정의 HTML 요소를 정의하고 등록할 수 있는 API입니다. 이 API를 사용하면 웹 개발자는 새로운 HTML 요소를 생성하여 재사용 가능하고 확장 가능한 웹 컴포넌트를 구축할 수 있습니다.

## 문서화
### 목적
CustomElementRegistry는 웹 표준의 일환으로, 개발자가 HTML 태그를 확장하고 신규 태그를 정의할 수 있게 해줍니다. 이를 통해 개발자는 재사용 가능한 UI 구성 요소를 만들고, 웹 애플리케이션의 구조를 더욱 깔끔하고 유지보수 가능하게 할 수 있습니다.

### 사용법
CustomElementRegistry는 `window.customElements` 객체를 통해 접근할 수 있습니다. 이 객체의 주요 메서드는 다음과 같습니다:
- **define(name: string, constructor: Function, options?: Object)**: 새로운 사용자 정의 요소를 등록합니다.
- **get(name: string)**: 등록된 사용자 정의 요소의 생성자를 반환합니다.
- **whenDefined(name: string)**: 특정 요소가 정의될 때까지 대기하는 프로미스를 반환합니다.

### 세부 사항
1. **이름 규칙**: 사용자 정의 요소의 이름은 반드시 하이픈(`-`)을 포함해야 하며, 일반 HTML 요소 이름과 충돌하지 않도록 해야 합니다.
2. **생성자**: 사용자 정의 요소는 `HTMLElement`를 확장하여 만들어야 하며, 생성자에서 `super()`를 호출해야 합니다.
3. **옵션**: `define` 메서드는 선택적으로 `options` 객체를 받습니다. 이 객체는 요소의 정의에 대한 추가 정보를 제공합니다.

## 예제
```javascript
// 사용자 정의 요소 정의하기
class MyElement extends HTMLElement {
    constructor() {
        super();
        this.innerHTML = "<p>안녕하세요, 사용자 정의 요소!</p>";
    }
}

// 사용자 정의 요소 등록하기
customElements.define('my-element', MyElement);

// 사용자 정의 요소 사용하기
const myElementInstance = document.createElement('my-element');
document.body.appendChild(myElementInstance);
```

## 설명
- **일반적인 실수**: 사용자 정의 요소의 이름에 하이픈을 포함하지 않거나, `HTMLElement`를 상속하지 않으면 오류가 발생합니다.
- **정의 대기**: `whenDefined` 메서드를 사용하면 요소가 정의될 때까지 기다릴 수 있어, 비동기적으로 요소를 사용할 수 있습니다.
- **라이프사이클 메서드**: 사용자 정의 요소는 `connectedCallback`, `disconnectedCallback`, `attributeChangedCallback`과 같은 라이프사이클 메서드를 구현하여 요소의 생명주기를 관리할 수 있습니다.

## 한줄 요약
CustomElementRegistry는 JavaScript에서 사용자 정의 HTML 요소를 정의하고 관리할 수 있는 기능을 제공하는 API입니다.