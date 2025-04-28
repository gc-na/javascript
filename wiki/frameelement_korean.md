<!--
Meta Description: # frameElement: JavaScript에서 프레임 요소 접근하기 ## 개요 `frameElement`는 JavaScript에서 현재 문서가 포함된 iframe 또는 frame 요소에 대한 참조를 제공하는 속성입니다. 이 속성은 주로 iframe 내부에서 부모 ...
Meta Keywords: frameelement, iframe, 문서가, 요소에, 포함된
-->

# frameElement: JavaScript에서 프레임 요소 접근하기

## 개요
`frameElement`는 JavaScript에서 현재 문서가 포함된 iframe 또는 frame 요소에 대한 참조를 제공하는 속성입니다. 이 속성은 주로 iframe 내부에서 부모 문서에 대한 정보를 얻거나 상호작용할 때 사용됩니다.

## 문서
### 목적
`frameElement`는 현재 문서가 iframe 또는 frame의 일부일 때, 그 요소에 대한 참조를 반환합니다. 이 속성을 사용하면 문서가 어떤 프레임에 속하는지 알 수 있으며, 부모 문서와의 상호작용을 가능하게 합니다.

### 사용법
`frameElement`는 Window 객체의 속성으로, 다음과 같이 접근할 수 있습니다:

```javascript
var frameRef = window.frameElement;
```

이 속성을 호출하면, 현재 문서가 포함된 iframe 또는 frame 요소에 대한 참조가 반환됩니다. 문서가 프레임에 포함되어 있지 않을 경우, `null`이 반환됩니다.

### 세부 정보
- **타입**: HTMLIFrameElement 또는 HTMLFrameElement (프레임을 사용하는 경우)
- **브라우저 지원**: 대부분의 현대 웹 브라우저에서 지원됩니다.
- **읽기 전용**: `frameElement`는 읽기 전용 속성입니다. 즉, 값을 설정할 수 없습니다.

## 예제
### 기본 사용 예제
iframe 내부에서 부모 문서에 접근하는 기본적인 예제는 다음과 같습니다:

```html
<!-- 부모 문서 -->
<iframe src="iframe.html" id="myFrame"></iframe>
```

```html
<!-- iframe.html -->
<script>
    // 현재 문서가 포함된 iframe 요소에 접근
    var frameRef = window.frameElement;
    if (frameRef) {
        console.log('이 문서는 다음 iframe에 포함되어 있습니다:', frameRef.id);
    } else {
        console.log('이 문서는 프레임에 포함되어 있지 않습니다.');
    }
</script>
```

## 설명
- **일반적인 함정**: `frameElement`를 사용할 때, 문서가 프레임에 포함되어 있지 않으면 `null`을 반환합니다. 이 경우, `frameElement`를 사용하기 전에 반드시 null 체크를 해야 합니다.
  
- **보안 제한**: 다른 도메인에서 로드된 iframe의 `frameElement`에 접근하려고 하면, 동일 출처 정책(Same-Origin Policy)으로 인해 에러가 발생할 수 있습니다.

- **상호작용 제한**: 프레임 요소를 통해 부모 문서와 상호작용할 때, 부모 문서의 JavaScript 실행 환경에 따라 제한이 있을 수 있습니다. 

## 한 줄 요약
`frameElement`는 현재 문서가 포함된 iframe 또는 frame 요소에 대한 참조를 제공하는 JavaScript 속성입니다.