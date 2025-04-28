<!--
Meta Description: # JavaScript의 Math 객체: 수학 함수와 상수 활용하기 ## 개요 JavaScript의 Math 객체는 수학적 계산을 위한 다양한 함수와 상수를 제공합니다. 이 객체는 수학 관련 기능을 구현할 때 매우 유용하며, 복잡한 계산을 간편하게 처리할 수 있도록 돕...
Meta Keywords: math, 있습니다, log, javascript, let
-->

# JavaScript의 Math 객체: 수학 함수와 상수 활용하기

## 개요
JavaScript의 Math 객체는 수학적 계산을 위한 다양한 함수와 상수를 제공합니다. 이 객체는 수학 관련 기능을 구현할 때 매우 유용하며, 복잡한 계산을 간편하게 처리할 수 있도록 돕습니다.

## 문서화
Math 객체는 JavaScript의 내장 객체로, 수학적 상수와 함수들을 포함하고 있습니다. 이 객체에서 제공하는 함수들은 대개 정적(static) 메서드로 제공되며, 인스턴스를 생성할 필요 없이 직접 호출할 수 있습니다.

### 주요 기능 및 사용법
- **상수**: `Math.PI`, `Math.E` 등과 같은 수학 상수를 제공합니다.
- **기본 함수**: `Math.abs()`, `Math.ceil()`, `Math.floor()`, `Math.round()` 등과 같은 기본적인 수학 함수를 제공합니다.
- **삼각 함수**: `Math.sin()`, `Math.cos()`, `Math.tan()` 등과 같은 삼각함수를 지원합니다.
- **지수 및 로그 함수**: `Math.exp()`, `Math.log()`, `Math.sqrt()` 등과 같은 함수도 포함되어 있습니다.
- **랜덤 숫자 생성**: `Math.random()`을 사용하여 0과 1 사이의 난수를 생성할 수 있습니다.

## 예제
### 절대값
```javascript
let num = -5;
console.log(Math.abs(num)); // 5
```

### 반올림
```javascript
let floatNum = 4.5;
console.log(Math.round(floatNum)); // 5
```

### 랜덤 숫자 생성
```javascript
let randomNum = Math.random(); // 0과 1 사이의 난수
console.log(randomNum);
```

### 제곱근
```javascript
let num = 16;
console.log(Math.sqrt(num)); // 4
```

### 삼각 함수
```javascript
let angle = Math.PI / 4; // 45도
console.log(Math.sin(angle)); // 0.7071067811865475
```

## 설명
Math 객체를 사용할 때 주의해야 할 몇 가지 사항이 있습니다. 먼저, Math 객체의 메서드는 인스턴스를 생성하지 않고도 사용할 수 있지만, 일부 메서드는 특정한 데이터 타입을 요구할 수 있습니다. 예를 들어, `Math.sqrt()`는 음수를 인자로 받을 경우 NaN을 반환합니다. 또한, `Math.random()`은 0 이상 1 미만의 난수를 반환하지만, 특정 범위의 숫자를 생성하려면 추가적인 계산이 필요합니다.

## 한 줄 요약
JavaScript의 Math 객체는 다양한 수학적 계산을 쉽게 수행할 수 있도록 돕는 내장 객체입니다.