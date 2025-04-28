<!--
Meta Description: # HTMLSourceElement: JavaScript에서 HTML 소스 요소 다루기 ## 개요 `HTMLSourceElement`는 HTML 문서 내에서 `<source>` 요소를 나타내는 인터페이스로, 주로 `<audio>` 및 `<video>` 요소와 함께 사용...
Meta Keywords: video, 미디어, source, 요소를, 있습니다
-->

# HTMLSourceElement: JavaScript에서 HTML 소스 요소 다루기

## 개요
`HTMLSourceElement`는 HTML 문서 내에서 `<source>` 요소를 나타내는 인터페이스로, 주로 `<audio>` 및 `<video>` 요소와 함께 사용되어 다양한 미디어 소스를 정의합니다. 이 요소를 통해 브라우저는 적절한 형식의 미디어 파일을 선택하여 재생할 수 있습니다.

## 문서화
`HTMLSourceElement`는 JavaScript에서 미디어 소스의 속성과 메서드를 다루기 위한 객체입니다. 주로 `<source>` 태그와 연관되어 있으며, 이 요소는 다양한 미디어 형식을 지원하여 최적의 재생 경험을 제공합니다.

### 목적
HTMLSourceElement는 개발자가 미디어를 효율적으로 로드하고 조작할 수 있도록 돕습니다. 여러 형식의 소스를 제공함으로써, 브라우저가 가장 적합한 형식을 선택하게 할 수 있습니다.

### 사용법
HTMLSourceElement는 일반적으로 `<video>` 및 `<audio>` 요소 내에서 사용됩니다. JavaScript를 사용하여 소스 요소를 동적으로 추가하거나 수정할 수 있습니다.

### 속성
- `src`: 미디어 파일의 URL을 지정합니다.
- `type`: 미디어 파일의 MIME 타입을 정의합니다. 예: `audio/mpeg`, `video/mp4`.

### 메서드
HTMLSourceElement는 메서드를 제공하지 않으며, 속성을 통해 직접 조작합니다.

## 예제
다음은 HTMLSourceElement를 사용하는 기본 예제입니다.

### HTML 코드
```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  Your browser does not support the video tag.
</video>
```

### JavaScript 코드
```javascript
// 비디오 요소 선택
const videoElement = document.querySelector('video');

// 새로운 소스 요소 생성
const newSource = document.createElement('source');
newSource.src = 'movie.webm';
newSource.type = 'video/webm';

// 비디오 요소에 소스 추가
videoElement.appendChild(newSource);
```

## 설명
HTMLSourceElement를 사용할 때 주의해야 할 몇 가지 점이 있습니다.

- **소스 우선 순위**: 브라우저는 소스 요소를 순서대로 검사하며, 첫 번째로 지원되는 형식을 재생합니다. 따라서 더 일반적인 형식은 마지막에 배치하는 것이 좋습니다.
- **타입 속성**: `type` 속성을 명확히 지정하면 브라우저가 올바른 소스를 선택하는 데 도움이 됩니다.
- **동적 추가**: JavaScript를 사용하여 동적으로 소스를 추가할 수 있지만, 변경 후 비디오/오디오 요소를 다시 로드해야 할 수 있습니다.

## 한 줄 요약
HTMLSourceElement는 JavaScript에서 `<source>` 요소를 조작하여 다양한 미디어 형식을 지원하는 기능을 제공합니다.