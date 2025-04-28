<!--
Meta Description: # matchMedia: JavaScript에서 미디어 쿼리 관리하기 ## 개요 `matchMedia`는 JavaScript에서 CSS 미디어 쿼리를 프로그램matically 체크하고 반응형 웹 디자인을 구현하는 데 사용되는 API입니다. 이를 통해 사용자는 특정 조건...
Meta Keywords: matchmedia, mediaquerylist, 미디어, 있습니다, 600px
-->

# matchMedia: JavaScript에서 미디어 쿼리 관리하기

## 개요
`matchMedia`는 JavaScript에서 CSS 미디어 쿼리를 프로그램matically 체크하고 반응형 웹 디자인을 구현하는 데 사용되는 API입니다. 이를 통해 사용자는 특정 조건에 따라 스타일을 동적으로 조정할 수 있습니다.

## 문서화
`matchMedia` 메서드는 브라우저의 뷰포트 크기 및 기타 미디어 특성에 따라 조건을 평가하는 데 사용됩니다. 이 메서드는 `MediaQueryList` 객체를 반환하며, 이 객체는 주어진 미디어 쿼리가 현재의 뷰포트와 일치하는지 여부를 확인할 수 있는 메서드와 이벤트를 포함하고 있습니다.

### 사용법
```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');
```

### 주요 속성 및 메서드
- **matches**: 현재 미디어 쿼리가 일치하는지의 여부를 boolean 값으로 반환합니다.
- **addListener(listener)**: 미디어 쿼리의 상태가 변경될 때 호출되는 콜백 함수를 등록합니다.
- **removeListener(listener)**: 등록된 콜백 함수를 제거합니다.

## 예제
### 기본 사용 예제
```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');

function handleMediaChange(event) {
  if (event.matches) {
    console.log('화면이 600px 이하입니다.');
  } else {
    console.log('화면이 600px 초과입니다.');
  }
}

// 초기 확인
handleMediaChange(mediaQueryList);

// 리스너 추가
mediaQueryList.addListener(handleMediaChange);
```

### CSS 클래스 토글 예제
```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');

function toggleClass(event) {
  const element = document.body;

  if (event.matches) {
    element.classList.add('mobile-view');
  } else {
    element.classList.remove('mobile-view');
  }
}

mediaQueryList.addListener(toggleClass);
toggleClass(mediaQueryList); // 초기 체크
```

## 설명
`matchMedia`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **브라우저 호환성**: `matchMedia`는 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 사용할 수 없습니다. 이를 확인하는 것이 중요합니다.
  
2. **리스너 관리**: `addListener` 메서드로 추가한 리스너는 적절히 관리해야 하며, 필요시에 `removeListener`로 제거해야 합니다. 그렇지 않으면 메모리 누수가 발생할 수 있습니다.

3. **성능 고려**: 너무 많은 리스너를 추가하면 성능에 부정적인 영향을 미칠 수 있습니다. 필요한 경우에만 리스너를 등록하세요.

## 한 줄 요약
`matchMedia`는 JavaScript에서 CSS 미디어 쿼리를 평가하고, 반응형 웹 디자인을 위한 동적 스타일 조정을 가능하게 하는 API입니다.