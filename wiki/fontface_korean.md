<!--
Meta Description: # FontFace: 자바스크립트에서의 글꼴 설정 방법 ## 개요 `FontFace`는 JavaScript에서 웹 폰트를 프로그래밍적으로 로드하고 사용할 수 있게 해주는 인터페이스입니다. 이를 통해 개발자들은 동적으로 폰트를 추가하고 스타일을 적용할 수 있습니다. ##...
Meta Keywords: fontface, font, error, document, fonts
-->

# FontFace: 자바스크립트에서의 글꼴 설정 방법

## 개요
`FontFace`는 JavaScript에서 웹 폰트를 프로그래밍적으로 로드하고 사용할 수 있게 해주는 인터페이스입니다. 이를 통해 개발자들은 동적으로 폰트를 추가하고 스타일을 적용할 수 있습니다.

## 문서화
### 목적
`FontFace` 인터페이스는 웹 페이지에서 사용할 글꼴을 정의하고 로드할 수 있는 기능을 제공합니다. 이를 통해 CSS에서 직접 지정할 수 없는 동적 글꼴 추가가 가능해집니다.

### 사용법
`FontFace`를 사용하기 위해서는 먼저 `FontFace` 객체를 생성해야 합니다. 생성자는 글꼴의 이름과 URL을 받습니다. 다음은 기본적인 사용법입니다.

```javascript
const font = new FontFace('MyFont', 'url(/path/to/font.woff2)');

// 글꼴을 로드합니다.
font.load().then(function(loadedFont) {
    // 로드된 글꼴을 문서에 추가합니다.
    document.fonts.add(loadedFont);
    // 글꼴을 사용할 수 있는 CSS 스타일을 적용합니다.
    document.body.style.fontFamily = 'MyFont, sans-serif';
}).catch(function(error) {
    console.error('Font loading failed:', error);
});
```

### 세부 사항
- `FontFace` 생성자에 전달하는 첫 번째 매개변수는 글꼴의 이름입니다. 이 이름은 CSS에서 사용하는 글꼴 이름과 동일해야 합니다.
- 두 번째 매개변수는 글꼴 파일의 URL입니다. 다양한 포맷의 폰트를 지원하기 위해 여러 URL을 지정할 수 있습니다.
- `load()` 메소드는 Promise를 반환하며, 글꼴이 성공적으로 로드되면 `then()` 블록이 실행됩니다. 반면 에러가 발생하면 `catch()` 블록에서 처리할 수 있습니다.

## 예제
### 기본 예제
```javascript
const myFont = new FontFace('MyCustomFont', 'url(my-font.woff2)');

myFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'MyCustomFont';
}).catch(function(error) {
    console.error('Failed to load the font:', error);
});
```

### 여러 글꼴 로드
```javascript
const fonts = [
    new FontFace('FontOne', 'url(font1.woff2)'),
    new FontFace('FontTwo', 'url(font2.woff2)')
];

Promise.all(fonts.map(font => font.load()))
    .then(loadedFonts => {
        loadedFonts.forEach(font => document.fonts.add(font));
        document.body.style.fontFamily = 'FontOne, FontTwo, sans-serif';
    })
    .catch(error => console.error('Error loading fonts:', error));
```

## 설명
- **브라우저 호환성**: 모든 브라우저가 `FontFace`를 지원하는 것은 아닙니다. 특히 오래된 브라우저에서는 지원되지 않을 수 있으므로, 필요한 경우 대체 스타일을 제공해야 합니다.
- **로딩 시간**: 폰트를 로드하는 데 시간이 걸릴 수 있으므로, 사용자 경험을 고려하여 로딩 상태를 표시하거나 기본 글꼴을 미리 설정하는 것이 좋습니다.
- **CSS Font Loading API**: `FontFace`는 CSS Font Loading API의 일부로, 이 API를 사용하면 더 많은 기능을 활용할 수 있습니다.

## 한 줄 요약
`FontFace`는 JavaScript를 통해 웹 폰트를 동적으로 로드하고 사용할 수 있게 해주는 인터페이스입니다.