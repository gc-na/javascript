<!--
Meta Description: # HTMLTemplateElement: JavaScript에서의 템플릿 요소 사용법 ## 개요 `HTMLTemplateElement`는 HTML 문서에서 재사용 가능한 템플릿을 정의하는 데 사용되는 특수한 요소입니다. JavaScript와 함께 사용하여 동적으로 HT...
Meta Keywords: template, document, clone, 템플릿, const
-->

# HTMLTemplateElement: JavaScript에서의 템플릿 요소 사용법

## 개요
`HTMLTemplateElement`는 HTML 문서에서 재사용 가능한 템플릿을 정의하는 데 사용되는 특수한 요소입니다. JavaScript와 함께 사용하여 동적으로 HTML을 생성하고 조작할 수 있는 강력한 도구입니다.

## 문서화
`HTMLTemplateElement`는 HTML5에서 도입된 요소로, `<template>` 태그로 정의됩니다. 이 요소는 문서의 DOM에 추가되지 않으며, 스크립트를 통해 쿼리하거나 클론하여 사용할 수 있습니다. 템플릿 내부의 내용은 브라우저에 의해 렌더링되지 않으며, 이를 통해 동적인 콘텐츠 생성을 용이하게 합니다.

### 목적
- 재사용 가능한 HTML 구조를 정의하기 위해 사용됩니다.
- 자바스크립트를 통해 동적으로 콘텐츠를 추가할 수 있습니다.

### 사용법
템플릿 요소는 다음과 같이 정의됩니다:

```html
<template id="myTemplate">
    <div>
        <h1>템플릿 제목</h1>
        <p>이것은 템플릿 내용입니다.</p>
    </div>
</template>
```

JavaScript를 사용하여 템플릿의 내용을 클론하고 DOM에 추가할 수 있습니다:

```javascript
const template = document.getElementById('myTemplate');
const clone = document.importNode(template.content, true);
document.body.appendChild(clone);
```

## 예제
1. 기본 템플릿 사용 예제:

```html
<template id="simpleTemplate">
    <p>안녕하세요, {{name}}님!</p>
</template>

<script>
    const template = document.getElementById('simpleTemplate');
    const clone = document.importNode(template.content, true);
    clone.querySelector('p').textContent = clone.querySelector('p').textContent.replace('{{name}}', '홍길동');
    document.body.appendChild(clone);
</script>
```

2. 여러 개의 템플릿 클론 예제:

```html
<template id="listItemTemplate">
    <li>아이템: {{item}}</li>
</template>

<script>
    const items = ['사과', '바나나', '체리'];
    const template = document.getElementById('listItemTemplate');
    
    const list = document.createElement('ul');
    
    items.forEach(item => {
        const clone = document.importNode(template.content, true);
        clone.querySelector('li').textContent = clone.querySelector('li').textContent.replace('{{item}}', item);
        list.appendChild(clone);
    });
    
    document.body.appendChild(list);
</script>
```

## 설명
`HTMLTemplateElement`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- 템플릿 내용은 초기에는 DOM에 추가되지 않으며, 반드시 JavaScript를 통해 클론해서 사용해야 합니다.
- 템플릿 내부의 스크립트는 실행되지 않으므로, 동적인 내용은 JavaScript로 추가해야 합니다.
- 여러 번 클론할 수 있지만, 원본 템플릿은 변경되지 않습니다.

## 한 줄 요약
`HTMLTemplateElement`는 재사용 가능한 HTML 구조를 정의하고 JavaScript를 통해 동적으로 콘텐츠를 추가할 수 있는 기능을 제공합니다.