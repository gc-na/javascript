<!--
Meta Description: # ShadowRoot: 자바스크립트에서의 기본 개념과 사용법 ## 개요 ShadowRoot는 웹 컴포넌트의 일부로, DOM의 캡슐화를 통해 스타일과 스크립트를 격리하는 데 사용되는 객체입니다. 이를 통해 개발자는 더 안전하고 재사용 가능한 컴포넌트를 만들 수 있습니다...
Meta Keywords: shadow, const, shadowroot, dom, open
-->

# ShadowRoot: 자바스크립트에서의 기본 개념과 사용법

## 개요
ShadowRoot는 웹 컴포넌트의 일부로, DOM의 캡슐화를 통해 스타일과 스크립트를 격리하는 데 사용되는 객체입니다. 이를 통해 개발자는 더 안전하고 재사용 가능한 컴포넌트를 만들 수 있습니다.

## 문서화
### 목적
ShadowRoot는 웹 컴포넌트의 Shadow DOM을 구현하기 위해 사용됩니다. Shadow DOM은 DOM 트리의 일부로, 외부 스타일과 스크립트의 영향을 받지 않도록 설계되었습니다. 이를 통해 컴포넌트의 내부 구조를 보호하고, 재사용성을 높이며, 코드의 유지보수를 용이하게 합니다.

### 사용법
ShadowRoot는 `Element.attachShadow()` 메서드를 통해 생성됩니다. 이 메서드는 Shadow DOM을 특정 요소에 연결하여 해당 요소의 내부를 정의합니다.

```javascript
const hostElement = document.querySelector('#host');
const shadowRoot = hostElement.attachShadow({ mode: 'open' }); // 'open' 또는 'closed' 모드 선택
```

- **모드**: `mode` 속성은 'open'이나 'closed'를 선택할 수 있습니다.
  - 'open': 외부에서 ShadowRoot에 접근할 수 있습니다.
  - 'closed': 외부에서 ShadowRoot에 접근할 수 없습니다.

### 세부 사항
ShadowRoot를 사용하면 다음과 같은 기능을 활용할 수 있습니다:
- **스타일 캡슐화**: Shadow DOM 안의 스타일은 외부 스타일에 영향을 받지 않으며, 외부 스타일 또한 Shadow DOM 안에 영향을 미치지 않습니다.
- **구조적 캡슐화**: Shadow DOM 안의 요소는 외부 DOM에서 접근할 수 없으므로, 내부 구현 세부사항을 숨길 수 있습니다.

## 예제
### 기본 사용 예제
```html
<div id="host"></div>
<script>
  const hostElement = document.querySelector('#host');
  const shadowRoot = hostElement.attachShadow({ mode: 'open' });

  const para = document.createElement('p');
  para.textContent = '이것은 Shadow DOM 안의 문단입니다.';
  shadowRoot.appendChild(para);
</script>
```

### 스타일 캡슐화 예제
```html
<div id="host"></div>
<script>
  const hostElement = document.querySelector('#host');
  const shadowRoot = hostElement.attachShadow({ mode: 'open' });

  const style = document.createElement('style');
  style.textContent = `
    p {
      color: blue;
      font-weight: bold;
    }
  `;
  
  const para = document.createElement('p');
  para.textContent = '이 문단은 독립적인 스타일을 가집니다.';
  
  shadowRoot.appendChild(style);
  shadowRoot.appendChild(para);
</script>
```

## 설명
### 일반적인 문제점 및 주의사항
- **접근성**: 'closed' 모드로 설정한 경우, ShadowRoot 내부에 접근할 수 없으므로 외부에서의 조작이 불가능합니다. 따라서, 필요한 경우 'open' 모드를 고려해야 합니다.
- **브라우저 호환성**: Shadow DOM은 최신 브라우저에서 지원되지만, 구형 브라우저에서는 지원되지 않을 수 있습니다. 따라서, 브라우저 호환성을 고려한 폴리필 사용을 추천합니다.
- **이벤트 전파**: Shadow DOM 내부에서 발생한 이벤트는 외부 DOM에 전파되지 않을 수 있으므로, 이벤트 리스너를 적절히 설정해야 합니다.

## 한 줄 요약
ShadowRoot는 웹 컴포넌트를 위한 DOM 캡슐화를 제공하여 스타일과 스크립트를 격리하는 기능을 합니다.