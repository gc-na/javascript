<!--
Meta Description: # AnimationPlaybackEvent: 자바스크립트 애니메이션 이벤트의 이해 ## 개요 `AnimationPlaybackEvent`는 자바스크립트에서 CSS 애니메이션의 재생 상태 변경을 감지하는 데 사용되는 이벤트입니다. 이 이벤트는 애니메이션이 재생되거나 일...
Meta Keywords: element, 애니메이션의, 애니메이션이, animation, animationplaybackevent
-->

# AnimationPlaybackEvent: 자바스크립트 애니메이션 이벤트의 이해

## 개요
`AnimationPlaybackEvent`는 자바스크립트에서 CSS 애니메이션의 재생 상태 변경을 감지하는 데 사용되는 이벤트입니다. 이 이벤트는 애니메이션이 재생되거나 일시 정지될 때 발생하며, 애니메이션의 상태를 관리하는 데 유용합니다.

## 문서화
`AnimationPlaybackEvent`는 애니메이션의 재생 관련 정보를 담고 있는 이벤트 객체입니다. 이 이벤트는 `Animation` 인터페이스의 메서드와 함께 사용되며, 애니메이션이 시작되거나 중지될 때 발생합니다. 주요 속성으로는 `type`, `target`, `currentTime`, `timelineTime`, `elapsedTime` 등이 있습니다.

### 주요 속성
- **type**: 이벤트의 종류를 나타냅니다. (예: 'play', 'pause')
- **target**: 이벤트가 발생한 애니메이션 객체를 참조합니다.
- **currentTime**: 애니메이션의 현재 재생 시간을 나타냅니다.
- **timelineTime**: 타임라인에서의 시간입니다.
- **elapsedTime**: 이벤트 발생 시점부터 애니메이션이 재생된 시간입니다.

### 사용법
`AnimationPlaybackEvent`는 CSS 애니메이션의 상태 변화를 감지하는 데 사용됩니다. 이 이벤트를 사용하여 애니메이션의 시작, 일시 정지 또는 재개 시 특정 작업을 수행할 수 있습니다.

```javascript
const element = document.querySelector('.my-animation');
const animation = element.animate(/* animation keyframes */, /* options */);

element.addEventListener('animationplay', (event) => {
    console.log('애니메이션이 재생 중입니다.');
});

element.addEventListener('animationpause', (event) => {
    console.log('애니메이션이 일시 정지되었습니다.');
});
```

## 예제
1. **애니메이션 재생 이벤트 감지**

```javascript
const element = document.querySelector('.animate-me');
const animation = element.animate([{ opacity: 0 }, { opacity: 1 }], {
    duration: 1000,
    fill: 'forwards'
});

element.addEventListener('animationplay', (event) => {
    console.log('애니메이션이 시작되었습니다.');
});
```

2. **애니메이션 일시 정지 이벤트 감지**

```javascript
const element = document.querySelector('.animate-me');
const animation = element.animate([{ transform: 'scale(1)' }, { transform: 'scale(1.5)' }], {
    duration: 2000,
    fill: 'forwards'
});

animation.pause();

element.addEventListener('animationpause', (event) => {
    console.log('애니메이션이 일시 정지되었습니다.');
});
```

## 설명
`AnimationPlaybackEvent`를 활용할 때 주의해야 할 점은 이벤트가 발생하는 시점입니다. 애니메이션의 상태 변화에 따라 여러 번 발생할 수 있으며, 이를 정확히 처리하지 않으면 중복된 로직이 실행될 수 있습니다. 또한, 이벤트 핸들러가 비동기 작업을 포함할 경우, 애니메이션의 상태를 적절히 추적하는 것이 중요합니다.

## 한 줄 요약
`AnimationPlaybackEvent`는 자바스크립트에서 CSS 애니메이션의 재생 상태 변화를 감지하는 이벤트입니다.