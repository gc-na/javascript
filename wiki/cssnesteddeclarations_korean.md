<!--
Meta Description: # CSS 중첩 선언 (CSS Nested Declarations)과 JavaScript의 관계 ## 개요 CSS 중첩 선언(CSS Nested Declarations)은 CSS 규칙을 다른 CSS 규칙 내부에 작성할 수 있는 기능으로, JavaScript와 함께 사용...
Meta Keywords: css, header, container, javascript와, 있습니다
-->

# CSS 중첩 선언 (CSS Nested Declarations)과 JavaScript의 관계

## 개요
CSS 중첩 선언(CSS Nested Declarations)은 CSS 규칙을 다른 CSS 규칙 내부에 작성할 수 있는 기능으로, JavaScript와 함께 사용될 때 스타일링을 더 효율적으로 관리할 수 있습니다. 이 기능은 일반적으로 CSS 전처리기(예: SASS, LESS)에서 제공되지만, 최근 CSS의 표준에 통합될 가능성도 있습니다.

## 문서화
### 목적
CSS 중첩 선언은 복잡한 스타일링 구조를 단순화하고, 코드의 가독성을 높이며, 재사용성을 증가시키는 데 도움을 줍니다. JavaScript를 통해 동적으로 스타일을 변경해야 할 때, 중첩된 CSS 규칙은 더욱 효율적인 방법으로 적용됩니다.

### 사용법
CSS 중첩 선언은 CSS 전처리기에서 주로 사용되며, JavaScript와 함께 사용할 때는 스타일 시트를 동적으로 생성하거나 수정하는 데 유용합니다. 예를 들어, JavaScript를 사용하여 클래스명을 추가하거나 제거함으로써 중첩된 CSS 스타일 규칙을 적용할 수 있습니다.

```scss
// SASS 예제
.container {
  color: blue;
  
  .header {
    font-size: 20px;
    
    &:hover {
      color: red;
    }
  }
}
```

위의 코드에서 `.header`는 `.container`의 자식 클래스로 정의되며, hover 상태에서는 색상이 빨간색으로 변경됩니다.

## 예제
다음은 JavaScript와 함께 사용하는 간단한 CSS 중첩 선언 예제입니다:

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container {
            color: blue;
        }
        .container .header {
            font-size: 20px;
        }
        .container .header:hover {
            color: red;
        }
    </style>
    <title>CSS Nested Declarations Example</title>
</head>
<body>
    <div class="container">
        <div class="header">Hover over me!</div>
    </div>

    <script>
        const header = document.querySelector('.header');
        header.addEventListener('click', () => {
            header.classList.toggle('active');
        });
    </script>
</body>
</html>
```

## 설명
### 일반적인 함정 및 주의사항
- **브라우저 호환성**: 중첩 선언은 CSS 전처리기에서 지원되지만, CSS의 기본 기능으로는 지원되지 않기 때문에, 실제 프로덕션 코드에서는 주의가 필요합니다.
- **가독성 저하**: 중첩이 너무 깊어지면 코드의 가독성이 떨어질 수 있으며, 이는 유지보수를 어렵게 만들 수 있습니다.
- **성능 문제**: 중첩된 스타일 규칙이 많아지면 CSS의 성능에 영향을 줄 수 있으므로, 필요한 경우에만 사용해야 합니다.

## 한 줄 요약
CSS 중첩 선언은 JavaScript와 함께 사용될 때 코드의 가독성과 효율성을 높이는 강력한 기능입니다.