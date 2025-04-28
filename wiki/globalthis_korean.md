<!--
Meta Description: # JavaScript의 globalThis: 전역 객체에 대한 완벽한 가이드 ## 개요 `globalThis`는 JavaScript에서 전역 객체에 접근할 수 있는 표준화된 방법을 제공합니다. 모든 환경(브라우저, Node.js 등)에서 동일한 방식으로 전역 객체를 ...
Meta Keywords: globalthis, 객체에, 접근할, node, 제공합니다
-->

# JavaScript의 globalThis: 전역 객체에 대한 완벽한 가이드

## 개요
`globalThis`는 JavaScript에서 전역 객체에 접근할 수 있는 표준화된 방법을 제공합니다. 모든 환경(브라우저, Node.js 등)에서 동일한 방식으로 전역 객체를 참조할 수 있게 해줍니다.

## 문서화

### 목적
`globalThis`는 JavaScript의 전역 환경을 나타내는 객체입니다. 브라우저에서는 `window` 객체, Node.js에서는 `global` 객체를 사용하여 전역 변수를 관리합니다. `globalThis`를 사용하면 이러한 차이를 신경 쓸 필요 없이 항상 동일한 방식으로 전역 객체에 접근할 수 있습니다.

### 사용법
`globalThis`는 전역 객체를 참조하는 데 사용되며, 별도의 인스턴스나 메소드를 필요로 하지 않습니다. 코드에서 `globalThis`를 사용하려면, 다음과 같이 간단히 접근하면 됩니다:

```javascript
console.log(globalThis);
```

### 세부 사항
- **ECMAScript 2020**에서 도입되었습니다.
- 모든 전역 변수를 `globalThis`를 통해 접근할 수 있습니다.
- 브라우저와 Node.js에서의 호환성을 제공합니다.
- 전역 객체에 새로운 속성을 추가하거나 수정할 때 유용합니다.

## 예제

### 기본 사용 예제
```javascript
// 전역 변수 설정
globalThis.myGlobalVar = "Hello, World!";

// 전역 변수 접근
console.log(globalThis.myGlobalVar); // 출력: "Hello, World!"
```

### 전역 함수 정의
```javascript
globalThis.myGlobalFunction = function() {
    return "This is a global function!";
};

console.log(globalThis.myGlobalFunction()); // 출력: "This is a global function!"
```

## 설명
- **호환성 문제**: `globalThis`는 모든 주요 브라우저 및 Node.js에서 지원되지만, 구형 브라우저에서는 사용할 수 없습니다. 따라서, 구형 브라우저를 지원해야 할 경우에는 폴리필을 고려해야 합니다.
- **전역 네임스페이스 오염**: 전역 객체에 속성을 추가하는 것은 네임스페이스 오염의 위험이 있습니다. 이로 인해 다른 코드와의 충돌이 발생할 수 있으니 주의해야 합니다.
- **strict mode에서의 차이**: strict mode에서는 `this`가 `undefined`가 되므로, `globalThis`를 사용하여 전역 객체에 접근하는 것이 중요합니다.

## 한 줄 요약
`globalThis`는 JavaScript에서 모든 환경에서 전역 객체에 접근할 수 있는 표준화된 방법을 제공합니다.