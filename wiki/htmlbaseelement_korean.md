<!--
Meta Description: # HTMLBaseElement: 자바스크립트에서의 정의와 사용법 ## 개요 `HTMLBaseElement`는 HTML 문서에서 `<base>` 요소를 나타내는 인터페이스로, 자바스크립트를 이용해 해당 요소를 조작할 수 있게 해줍니다. `<base>` 요소는 페이지 내...
Meta Keywords: html, base, href, htmlbaseelement, url을
-->

# HTMLBaseElement: 자바스크립트에서의 정의와 사용법

## 개요
`HTMLBaseElement`는 HTML 문서에서 `<base>` 요소를 나타내는 인터페이스로, 자바스크립트를 이용해 해당 요소를 조작할 수 있게 해줍니다. `<base>` 요소는 페이지 내의 상대 경로 링크의 기본 URL을 설정하는 데 사용됩니다.

## 문서화
### 목적
`HTMLBaseElement`는 웹 페이지에서 상대 경로를 사용하는 링크와 이미지의 기본 URL을 설정하는데 중요한 역할을 합니다. 이를 통해 여러 링크가 동일한 기본 경로를 따르도록 할 수 있습니다.

### 사용법
`HTMLBaseElement`는 다음과 같은 속성을 가집니다:
- **href**: 기본 URL을 설정하거나 반환합니다.
- **target**: 링크가 열릴 대상 창을 설정합니다.

### 속성 설명
- **href (문자열)**: 기본 URL을 설정합니다. 예를 들어, `<base href="https://example.com/">`는 모든 상대 링크가 `https://example.com/`을 기준으로 해석되도록 합니다.
- **target (문자열)**: 링크의 대상 창을 지정합니다. 예를 들어, `_blank`, `_self`, `_parent`, `_top` 등을 사용할 수 있습니다.

## 예제
```html
<!DOCTYPE html>
<html>
<head>
    <base href="https://example.com/">
    <title>Example</title>
</head>
<body>
    <a href="page.html">상대 링크</a>
    <img src="image.png" alt="이미지">
</body>
</html>
```
위의 예제에서, `<base>` 요소에 설정된 `href` 덕분에 `page.html` 링크와 `image.png` 이미지는 모두 `https://example.com/`을 기준으로 해석됩니다.

## 설명
`HTMLBaseElement`를 사용할 때 주의할 점은 다음과 같습니다:
- 하나의 HTML 문서에는 단 하나의 `<base>` 요소만 포함될 수 있습니다. 여러 개를 사용하면 브라우저가 첫 번째 요소만 인식합니다.
- `<base>` 요소는 `<head>` 섹션에 위치해야 하며, `<body>` 섹션 이전에 정의되어야 합니다.
- `href` 속성을 빈 문자열로 설정하면 기본 URL이 제거됩니다.

## 요약
`HTMLBaseElement`는 자바스크립트에서 상대 경로를 사용하는 링크의 기본 URL을 설정하는 데 필수적인 HTML 요소입니다.