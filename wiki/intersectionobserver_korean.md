<!--
Meta Description: # IntersectionObserver: JavaScript로 스크롤 관찰하기 ## 개요 IntersectionObserver는 웹 페이지에서 특정 요소가 뷰포트(사용자가 현재 보고 있는 화면 영역)에 들어오거나 나가는 것을 비동기적으로 관찰할 수 있는 API입니다....
Meta Keywords: intersectionobserver, 요소가, observer, const, 스크롤
-->

# IntersectionObserver: JavaScript로 스크롤 관찰하기

## 개요
IntersectionObserver는 웹 페이지에서 특정 요소가 뷰포트(사용자가 현재 보고 있는 화면 영역)에 들어오거나 나가는 것을 비동기적으로 관찰할 수 있는 API입니다. 이 기능은 성능 최적화 및 사용자 경험 개선에 유용합니다.

## 문서화

### 목적
IntersectionObserver는 웹 애플리케이션에서 요소의 가시성을 효율적으로 추적하여 스크롤 이벤트를 최적화하고, 필요할 때만 리소스를 로드하거나 특정 작업을 수행하도록 도와줍니다.

### 사용법
IntersectionObserver를 사용하기 위해서는 다음 단계를 따릅니다:

1. **IntersectionObserver 인스턴스 생성**: 관찰할 요소와 콜백 함수를 인자로 전달합니다.
2. **요소 관찰 시작**: `observe()` 메서드를 사용하여 관찰할 요소를 등록합니다.
3. **관찰 중지** (선택적): 필요에 따라 `unobserve()` 메서드를 사용하여 관찰을 중지할 수 있습니다.

### 세부사항
- **콜백 함수**: 관찰하는 요소가 뷰포트에 들어오거나 나갈 때 호출됩니다. 이 함수는 두 개의 인자를 받습니다: `entries`와 `observer`.
- **옵션**: `root`, `rootMargin`, `threshold`와 같은 옵션을 설정하여 관찰 조건을 조정할 수 있습니다.

## 예제

```javascript
// 1. IntersectionObserver 인스턴스 생성
const options = {
  root: null, // 뷰포트
  rootMargin: '0px',
  threshold: 0.1 // 10% 가시성
};

const callback = (entries, observer) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      console.log('요소가 뷰포트에 들어왔습니다!');
    } else {
      console.log('요소가 뷰포트에서 나갔습니다!');
    }
  });
};

const observer = new IntersectionObserver(callback, options);

// 2. 요소 관찰 시작
const target = document.querySelector('.target-element');
observer.observe(target);
```

## 설명
IntersectionObserver를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **성능**: 기존의 스크롤 이벤트 리스너보다 성능이 뛰어나지만, 콜백이 너무 많은 작업을 수행하면 여전히 성능 저하를 유발할 수 있습니다.
- **브라우저 호환성**: 모든 브라우저에서 지원되지 않을 수 있으므로, 사용 전 브라우저 호환성을 확인해야 합니다.
- **옵션 조정**: `threshold` 값이 너무 낮거나 높으면 원하는 결과를 얻지 못할 수 있으니 적절한 값을 설정해야 합니다.

## 한 줄 요약
IntersectionObserver는 요소의 가시성을 비동기적으로 관찰하여 성능을 최적화하는 JavaScript API입니다.