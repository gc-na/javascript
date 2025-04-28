<!--
Meta Description: # CSSStyleDeclaration: 자바스크립트에서 CSS 스타일을 다루는 방법 ## 개요 `CSSStyleDeclaration`은 자바스크립트에서 HTML 요소의 인라인 스타일을 제어하고 조작하는 데 사용되는 객체입니다. 이를 통해 개발자는 CSS 속성을 읽고,...
Meta Keywords: css, 스타일을, element, cssstyledeclaration, style
-->

# CSSStyleDeclaration: 자바스크립트에서 CSS 스타일을 다루는 방법

## 개요
`CSSStyleDeclaration`은 자바스크립트에서 HTML 요소의 인라인 스타일을 제어하고 조작하는 데 사용되는 객체입니다. 이를 통해 개발자는 CSS 속성을 읽고, 수정하고, 추가할 수 있습니다.

## 문서화
`CSSStyleDeclaration` 객체는 DOM (Document Object Model)의 일부로, 특정 HTML 요소에 적용된 스타일을 나타냅니다. 이 객체는 CSS 속성을 프로퍼티로 가지며, 이를 통해 스타일 값을 설정하거나 가져올 수 있습니다.

### 목적
`CSSStyleDeclaration`의 주요 목적은 웹 페이지의 요소에 적용된 CSS 스타일을 동적으로 변경하고 제어하는 것입니다. 이를 통해 사용자 상호작용에 따라 스타일을 변경하거나, 특정 조건에 따라 스타일을 조절할 수 있습니다.

### 사용법
`CSSStyleDeclaration` 객체는 다음과 같이 HTML 요소의 `style` 속성을 통해 접근할 수 있습니다:

```javascript
const element = document.getElementById("myElement");
const styles = element.style;
```

#### 주요 프로퍼티 및 메서드
- `getPropertyValue(property)`: 지정된 CSS 속성의 값을 가져옵니다.
- `setProperty(property, value)`: 지정된 CSS 속성의 값을 설정합니다.
- `removeProperty(property)`: 지정된 CSS 속성을 제거합니다.
- `cssText`: 스타일 선언 블록을 문자열로 가져오거나 설정합니다.

## 예제
### 기본 사용 예
```javascript
// HTML 요소 선택
const element = document.getElementById("myElement");

// 스타일 적용
element.style.color = "blue"; // 텍스트 색상 변경
element.style.backgroundColor = "yellow"; // 배경색 변경
```

### `getPropertyValue`와 `setProperty` 사용 예
```javascript
const element = document.getElementById("myElement");

// CSS 속성 값 가져오기
const color = element.style.getPropertyValue("color");
console.log(color); // 현재 텍스트 색상 출력

// CSS 속성 값 설정하기
element.style.setProperty("font-size", "20px");
```

## 설명
`CSSStyleDeclaration` 객체를 사용할 때 주의할 점은 CSS 속성 이름이 camelCase 형식이 아닌 kebab-case 형식으로 작성된다는 것입니다. 예를 들어, `background-color`는 `backgroundColor`로 사용해야 합니다. 또한, CSS 속성을 설정할 때는 반드시 유효한 값을 제공해야 하며, 잘못된 값은 무시될 수 있습니다.

### 일반적인 함정
1. **속성 이름의 형식**: CSS 속성은 camelCase로 작성해야 하므로, `background-color`를 `backgroundColor`로 사용해야 합니다.
2. **값의 유효성**: 잘못된 CSS 값은 적용되지 않으며, 오류 메시지도 발생하지 않습니다.
3. **스타일 우선순위**: 인라인 스타일은 외부 스타일 시트보다 우선 적용되므로, 기존 스타일을 덮어쓰는 경우가 많습니다.

## 한 줄 요약
`CSSStyleDeclaration`은 자바스크립트를 통해 HTML 요소의 CSS 스타일을 동적으로 조작하는 데 사용되는 객체입니다.