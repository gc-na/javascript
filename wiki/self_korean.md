<!--
Meta Description: # JavaScript의 "self": 전역 객체에 대한 이해 ## 개요 JavaScript에서 "self"는 현재 실행 중인 전역 객체를 참조하는 데 사용되는 키워드입니다. 이를 통해 코드의 다양한 컨텍스트에서 전역 변수를 접근하거나, 전역 객체의 속성에 접근할 수 ...
Meta Keywords: self, 있습니다, 객체를, 접근할, 비동기
-->

# JavaScript의 "self": 전역 객체에 대한 이해

## 개요
JavaScript에서 "self"는 현재 실행 중인 전역 객체를 참조하는 데 사용되는 키워드입니다. 이를 통해 코드의 다양한 컨텍스트에서 전역 변수를 접근하거나, 전역 객체의 속성에 접근할 수 있습니다.

## 문서화
"self"는 JavaScript의 전역 객체를 참조하는 강력한 도구입니다. 브라우저 환경에서는 "self"가 Window 객체를 가리키며, 웹 워커에서는 WorkerGlobalScope를 가리킵니다. 이 키워드는 주로 이벤트 핸들러나 비동기 함수 내에서 전역 객체에 접근할 필요가 있을 때 유용합니다.

### 사용법
"self"는 별도로 선언할 필요 없이 어디서나 사용할 수 있으며, 전역 변수나 함수에 접근할 수 있게 해줍니다. 예를 들어, 다음과 같은 코드에서 "self"를 사용하여 전역 변수를 참조할 수 있습니다.

```javascript
var globalVar = "Hello, World!";
function showGlobal() {
    console.log(self.globalVar); // "Hello, World!"
}
showGlobal();
```

### 세부 사항
- "self"는 전역 객체를 참조하기 때문에, 이 객체에 정의된 모든 속성과 메서드에 접근할 수 있습니다.
- "self"는 특히 비동기 프로그래밍에서 유용합니다. 예를 들어, Promise나 setTimeout과 같은 비동기 함수 내에서 "self"를 사용하여 전역 상태를 안전하게 참조할 수 있습니다.

## 예제
### 기본 사용 예제

```javascript
// 전역 변수
var myNumber = 42;

function getNumber() {
    return self.myNumber; // 42 반환
}

console.log(getNumber());
```

### 비동기 환경에서의 사용

```javascript
var count = 0;

function increment() {
    setTimeout(function() {
        self.count++; // 전역 변수 count 증가
        console.log(self.count); // 1, 2, 3
    }, 1000);
}

increment(); // 1초 후 1이 출력됨
increment(); // 1초 후 2가 출력됨
increment(); // 1초 후 3이 출력됨
```

## 설명
"self"를 사용할 때 주의할 점은 전역 객체의 속성과 메서드에 접근하기 때문에, 이를 잘못 사용하면 이름 충돌이나 예기치 않은 결과를 초래할 수 있습니다. 예를 들어, "self"가 다른 컨텍스트에서 사용될 경우, 원치 않는 동작이 발생할 수 있습니다. 또한, ES6의 블록 스코프 변수가 도입되면서 "self"가 전역 객체를 참조하게 되면, 스코프에 따라 접근할 수 있는 변수가 달라질 수 있습니다.

## 한 줄 요약
JavaScript에서 "self"는 현재 실행 중인 전역 객체를 참조하여 전역 변수와 메서드에 접근할 수 있게 해주는 키워드입니다.