<!--
Meta Description: # JavaScript의 Document 객체: 웹 문서 조작의 기초 ## 개요 JavaScript의 `document` 객체는 HTML 및 XML 문서에 대한 접근 및 조작을 가능하게 하는 중요한 객체입니다. 웹 페이지의 요소를 선택하고 수정하며, 새로운 요소를 생성...
Meta Keywords: document, 있습니다, 새로운, 객체는, 페이지의
-->

# JavaScript의 Document 객체: 웹 문서 조작의 기초

## 개요
JavaScript의 `document` 객체는 HTML 및 XML 문서에 대한 접근 및 조작을 가능하게 하는 중요한 객체입니다. 웹 페이지의 요소를 선택하고 수정하며, 새로운 요소를 생성하고 삭제하는 등의 작업을 수행할 수 있습니다.

## 문서화

### 목적
`document` 객체는 웹 페이지의 DOM(문서 객체 모델)을 대표하며, JavaScript를 통해 웹 페이지의 콘텐츠와 구조를 동적으로 변경할 수 있는 기능을 제공합니다. 이를 통해 사용자는 더 인터랙티브하고 사용자 친화적인 웹 애플리케이션을 구축할 수 있습니다.

### 사용법
`document` 객체는 전역적으로 접근할 수 있으며, 다양한 메서드와 속성을 제공합니다. 이를 통해 HTML 요소를 선택하고 조작할 수 있습니다. 대표적인 메서드로는 `getElementById`, `getElementsByClassName`, `querySelector` 등이 있습니다.

### 세부 사항
- **속성**: `document.title`, `document.body`, `document.head` 등 다양한 속성을 통해 문서의 정보를 접근할 수 있습니다.
- **메서드**: 요소 생성, 삭제, 수정 등의 작업을 위한 메서드가 존재합니다. 예를 들어, `createElement`, `appendChild`, `removeChild` 등이 있습니다.

## 예제

### 기본 사용 예제
```javascript
// 문서의 제목 변경
document.title = "새로운 제목";

// id가 "myElement"인 요소 선택
const myElement = document.getElementById("myElement");

// 요소의 텍스트 변경
myElement.textContent = "안녕하세요, JavaScript!";
```

### 요소 추가 예제
```javascript
// 새로운 div 요소 생성
const newDiv = document.createElement("div");
newDiv.textContent = "새로운 div입니다!";

// body에 새로운 div 추가
document.body.appendChild(newDiv);
```

## 설명
`document` 객체를 사용하는 데 있어 몇 가지 주의할 점이 있습니다. 

1. **DOMContentLoaded 이벤트**: DOM이 완전히 로드되기 전에 `document`를 조작하려고 하면 오류가 발생할 수 있습니다. 따라서 DOMContentLoaded 이벤트를 사용하여 문서가 로드된 후에 스크립트를 실행하는 것이 좋습니다.

   ```javascript
   document.addEventListener("DOMContentLoaded", function() {
       // DOM 조작 코드
   });
   ```

2. **유효한 선택자**: `querySelector`나 `getElementsByClassName`과 같은 메서드를 사용할 때 유효한 선택자를 제공해야 합니다. 잘못된 선택자는 `null`을 반환하거나 오류를 발생시킬 수 있습니다.

3. **성능 고려**: DOM 조작은 성능에 영향을 미칠 수 있으므로, 여러 번의 변경을 한 번의 변경으로 묶거나, DocumentFragment를 사용하는 것이 좋습니다.

## 한 줄 요약
JavaScript의 `document` 객체는 웹 페이지의 DOM에 접근하고 조작하는 데 필수적인 기능을 제공하는 객체입니다.