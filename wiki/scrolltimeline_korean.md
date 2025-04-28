<!--
Meta Description: # ScrollTimeline: 자바스크립트에서 스크롤 애니메이션 제어하기 ## 개요 ScrollTimeline은 웹 페이지의 스크롤 위치에 따라 애니메이션을 제어할 수 있도록 하는 기능으로, 자바스크립트를 사용하여 보다 매끄럽고 직관적인 사용자 경험을 제공합니다. #...
Meta Keywords: 스크롤, scrolltimeline, scrolltimeline은, animate, transform
-->

# ScrollTimeline: 자바스크립트에서 스크롤 애니메이션 제어하기

## 개요
ScrollTimeline은 웹 페이지의 스크롤 위치에 따라 애니메이션을 제어할 수 있도록 하는 기능으로, 자바스크립트를 사용하여 보다 매끄럽고 직관적인 사용자 경험을 제공합니다.

## 문서
### 목적
ScrollTimeline은 CSS 애니메이션과 자바스크립트를 결합하여 스크롤 이벤트에 기반한 애니메이션을 생성할 수 있도록 설계되었습니다. 이를 통해 사용자는 페이지 스크롤에 따라 다양한 시각 효과를 구현할 수 있습니다.

### 사용법
ScrollTimeline은 `ScrollTimeline` 클래스를 사용하여 생성합니다. 이 클래스는 스크롤 이벤트에 반응하는 타임라인을 설정합니다. 기본적인 사용법은 다음과 같습니다:

```javascript
const timeline = new ScrollTimeline({
    scrollSources: [document.querySelector('your-scrollable-element')],
    timeRange: 1000 // 스크롤에 따른 시간 범위 (밀리초 단위)
});
```

이 타임라인을 CSS 애니메이션에 연결하면, 스크롤 위치에 따라 애니메이션이 재생됩니다.

### 세부 사항
- **scrollSources**: 애니메이션이 트리거될 스크롤 가능한 요소를 지정합니다.
- **timeRange**: 스크롤이 완료되는 데 걸리는 시간을 정의합니다. 이 값에 따라 애니메이션의 속도가 결정됩니다.
- **progress**: 사용자가 스크롤하는 정도에 따라 0에서 1로 변하는 값입니다.

## 예제
아래는 ScrollTimeline을 사용하는 간단한 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ScrollTimeline 예제</title>
    <style>
        .animate {
            transform: translateY(0);
            transition: transform 0.5s;
        }
        .animate.scroll {
            transform: translateY(100px);
        }
    </style>
</head>
<body>
    <div style="height: 200vh;">스크롤하세요!</div>
    <div class="animate">애니메이션 요소</div>
    
    <script>
        const element = document.querySelector('.animate');
        const timeline = new ScrollTimeline({
            scrollSources: [document],
            timeRange: 1000
        });
        
        element.animate([
            { transform: 'translateY(0)' },
            { transform: 'translateY(100px)' }
        ], {
            timeline: timeline
        });
    </script>
</body>
</html>
```

## 설명
- **일반적인 오류**: ScrollTimeline을 사용할 때 잘못된 요소를 `scrollSources`에 지정하면 애니메이션이 작동하지 않을 수 있습니다. 항상 올바른 DOM 요소를 선택했는지 확인해야 합니다.
- **브라우저 지원**: ScrollTimeline은 최신 브라우저에서 지원되며, 구형 브라우저에서는 동작하지 않을 수 있습니다. 따라서 호환성 확인이 필요합니다.

## 한 줄 요약
ScrollTimeline은 스크롤 위치에 따라 애니메이션을 제어할 수 있도록 돕는 자바스크립트 기능입니다.