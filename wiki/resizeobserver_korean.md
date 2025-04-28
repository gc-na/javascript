<!--
Meta Description: # ResizeObserver: 자바스크립트에서 요소 크기 변화를 감지하는 방법 ## 개요 `ResizeObserver`는 DOM 요소의 크기 변화에 대한 변화를 감지하고 이를 처리할 수 있도록 도와주는 자바스크립트 API입니다. 이를 통해 웹 개발자는 동적으로 크기가...
Meta Keywords: resizeobserver, observer, box, const, entries
-->

# ResizeObserver: 자바스크립트에서 요소 크기 변화를 감지하는 방법

## 개요
`ResizeObserver`는 DOM 요소의 크기 변화에 대한 변화를 감지하고 이를 처리할 수 있도록 도와주는 자바스크립트 API입니다. 이를 통해 웹 개발자는 동적으로 크기가 변하는 요소에 적절히 대응할 수 있습니다.

## 문서
`ResizeObserver`는 요소의 크기가 변경될 때 콜백 함수를 호출하는 관찰자(observer)를 생성하는 기능을 제공합니다. 이 API는 주로 반응형 웹 디자인과 UI 최적화에 유용하며, 다양한 사용자 화면에서의 요소 크기 변화를 실시간으로 처리할 수 있습니다.

### 사용법
1. **ResizeObserver 생성**: `ResizeObserver`를 생성할 때 콜백 함수를 전달해야 합니다.
2. **관찰할 요소 등록**: `observe` 메서드를 사용하여 크기를 감지할 DOM 요소를 등록합니다.
3. **관찰 종료**: 더 이상 관찰할 필요가 없을 경우 `unobserve` 메서드를 사용하여 등록을 해제합니다.

### 기본 문법
```javascript
const observer = new ResizeObserver(callback);
observer.observe(targetElement);
```

### 파라미터
- **callback**: 크기 변화가 감지될 때 호출되는 함수. 두 개의 인자를 받습니다.
  - **entries**: 크기 변화가 감지된 요소에 대한 정보 객체 배열.
  - **observer**: ResizeObserver 인스턴스.

## 예제
### 기본 사용 예제
```javascript
const box = document.querySelector('.box');

const observer = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log(`Width: ${entry.contentRect.width}, Height: ${entry.contentRect.height}`);
    }
});

observer.observe(box);
```

### 요소의 크기 변화에 따른 스타일 변경
```javascript
const box = document.querySelector('.box');

const observer = new ResizeObserver(entries => {
    for (let entry of entries) {
        if (entry.contentRect.width < 500) {
            box.style.backgroundColor = 'red';
        } else {
            box.style.backgroundColor = 'green';
        }
    }
});

observer.observe(box);
```

## 설명
`ResizeObserver`를 사용할 때 주의할 점은 다음과 같습니다:
- **성능**: 빈번한 크기 변화가 발생하는 요소에 대해 사용하면 성능에 영향을 줄 수 있습니다. 필요하지 않을 때는 관찰을 중지하는 것이 좋습니다.
- **브라우저 호환성**: 최신 브라우저에서 지원되지만, 구형 브라우저에서는 지원되지 않을 수 있으므로 폴리필을 고려해야 합니다.
- **무한 루프 방지**: 콜백 내에서 크기를 변경하는 경우, 무한 루프를 피하기 위해 신중하게 설계해야 합니다.

## 한 줄 요약
`ResizeObserver`는 자바스크립트에서 DOM 요소의 크기 변화를 감지하고 이를 처리하는 API입니다.