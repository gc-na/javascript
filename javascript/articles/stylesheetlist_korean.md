<!--
Meta Description: # StyleSheetList: JavaScript에서 스타일 시트 목록을 다루는 방법 ## 개요 `StyleSheetList`는 JavaScript에서 스타일 시트를 포함하는 객체로, DOM에서 사용 가능한 스타일 시트의 목록을 제공하는 컬렉션입니다. 이 객체는 현재...
Meta Keywords: 스타일, stylesheets, stylesheetlist, stylesheet, 시트를
-->

# StyleSheetList: JavaScript에서 스타일 시트 목록을 다루는 방법

## 개요
`StyleSheetList`는 JavaScript에서 스타일 시트를 포함하는 객체로, DOM에서 사용 가능한 스타일 시트의 목록을 제공하는 컬렉션입니다. 이 객체는 현재 문서에 로드된 모든 스타일 시트를 배열과 유사한 방식으로 다룰 수 있게 해줍니다.

## 문서화
### 목적
`StyleSheetList`는 웹 페이지에서 사용되는 모든 스타일 시트에 대한 접근을 제공하여, 개발자가 스타일 시트를 추가, 삭제, 수정할 수 있도록 합니다. 이는 동적으로 스타일을 조작해야 하는 경우에 유용합니다.

### 사용법
`StyleSheetList`는 보통 `document.styleSheets` 속성을 통해 접근할 수 있습니다. 이 속성은 현재 문서에 포함된 모든 스타일 시트를 포함하는 `StyleSheetList` 객체를 반환합니다.

```javascript
const styleSheets = document.styleSheets;
```

### 세부 사항
- `StyleSheetList`는 `length` 프로퍼티를 가지고 있어 스타일 시트의 수를 확인할 수 있습니다.
- 각 스타일 시트는 `StyleSheet` 객체로 표현되며, 이 객체는 추가적인 정보 (예: `href`, `media`, `type`)를 포함하고 있습니다.
- 스타일 시트에 접근하려면 인덱스를 사용합니다. 예를 들어, 첫 번째 스타일 시트에 접근하려면 `styleSheets[0]`를 사용합니다.

## 예제
### 기본 사용 예제

```javascript
// 모든 스타일 시트의 개수 출력
const styleSheets = document.styleSheets;
console.log("스타일 시트 개수: " + styleSheets.length);

// 첫 번째 스타일 시트의 href 출력
if (styleSheets.length > 0) {
    console.log("첫 번째 스타일 시트: " + styleSheets[0].href);
}
```

### 스타일 시트 추가 예제
```javascript
// 새로운 스타일 시트 추가
const styleSheet = document.createElement("link");
styleSheet.rel = "stylesheet";
styleSheet.type = "text/css";
styleSheet.href = "styles.css";
document.head.appendChild(styleSheet);
```

## 설명
`StyleSheetList`를 사용할 때 몇 가지 주의해야 할 점이 있습니다:
- 스타일 시트가 비동기적으로 로드될 수 있기 때문에, DOM이 완전히 로드된 후에 `document.styleSheets`를 호출해야 정확한 정보를 얻을 수 있습니다.
- 이 객체는 읽기 전용이므로, 직접적으로 스타일 시트를 수정할 수는 없습니다. 대신, `insertRule`, `deleteRule` 등의 메서드를 사용하여 스타일을 조작해야 합니다.
- 브라우저의 호환성 문제에 유의해야 하며, 특정 속성이나 메서드가 모든 브라우저에서 지원되지 않을 수 있습니다.

## 한 줄 요약
`StyleSheetList`는 JavaScript에서 현재 문서의 모든 스타일 시트를 배열처럼 다루고 조작할 수 있는 객체입니다.