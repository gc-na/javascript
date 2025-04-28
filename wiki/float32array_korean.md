<!--
Meta Description: # Float32Array: 자바스크립트에서의 고정 소수점 배열 ## 개요 `Float32Array`는 JavaScript에서 32비트 부동 소수점 숫자를 저장하는 배열을 제공하는 형식화된 배열입니다. 이 배열은 웹 브라우저와 Node.js 환경에서 고성능 수치 계산 ...
Meta Keywords: float32array, const, new, f32array, 소수점
-->

# Float32Array: 자바스크립트에서의 고정 소수점 배열

## 개요
`Float32Array`는 JavaScript에서 32비트 부동 소수점 숫자를 저장하는 배열을 제공하는 형식화된 배열입니다. 이 배열은 웹 브라우저와 Node.js 환경에서 고성능 수치 계산 및 이진 데이터 처리를 가능하게 합니다.

## 문서
`Float32Array`는 ECMAScript 2015(ES6)에서 도입된 Typed Array 중 하나로, 고정된 크기의 32비트 부동 소수점 숫자를 효과적으로 저장하고 조작할 수 있는 기능을 제공합니다. 이는 주로 WebGL과 같은 그래픽 처리, 오디오 처리, 그리고 대량의 수치 데이터를 다루는 애플리케이션에서 유용하게 사용됩니다.

### 사용법
`Float32Array`는 다음과 같은 방법으로 생성할 수 있습니다:

1. **길이를 지정하여 생성하기**
   ```javascript
   const array = new Float32Array(5); // 길이 5의 빈 Float32Array 생성
   ```

2. **기존 배열로부터 생성하기**
   ```javascript
   const array = new Float32Array([1.5, 2.5, 3.5]); // 배열로부터 Float32Array 생성
   ```

3. **ArrayBuffer로부터 생성하기**
   ```javascript
   const buffer = new ArrayBuffer(16); // 16바이트 크기의 ArrayBuffer 생성
   const floatArray = new Float32Array(buffer); // ArrayBuffer로부터 Float32Array 생성
   ```

### 주요 메서드 및 속성
- **length**: `Float32Array`의 길이를 반환합니다.
- **set()**: 다른 배열 또는 Typed Array의 값을 현재 배열에 복사합니다.
- **subarray()**: 특정 범위의 하위 배열을 반환합니다.

## 예제
```javascript
// Float32Array 생성 및 값 설정
const f32Array = new Float32Array(3);
f32Array[0] = 1.1;
f32Array[1] = 2.2;
f32Array[2] = 3.3;

console.log(f32Array); // Float32Array(3) [ 1.1, 2.2, 3.3 ]

// 기존 배열로부터 Float32Array 생성
const fromArray = new Float32Array([4.4, 5.5, 6.6]);
console.log(fromArray); // Float32Array(3) [ 4.4, 5.5, 6.6 ]

// ArrayBuffer로부터 생성
const buffer = new ArrayBuffer(12); // 3개의 Float32를 저장할 수 있는 버퍼
const floatView = new Float32Array(buffer);
floatView[0] = 7.7;

console.log(floatView); // Float32Array(3) [ 7.7, 0, 0 ]
```

## 설명
`Float32Array`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **정밀도 제한**: 32비트 부동 소수점은 정밀도가 제한되어 있어, 아주 큰 숫자나 아주 작은 숫자를 표현할 때 오류가 발생할 수 있습니다.
- **메모리 관리**: Typed Array는 메모리를 직접 관리하므로, 사용 후에는 불필요한 메모리 사용을 피하기 위해 적절히 해제하는 것이 좋습니다.
- **크기 고정**: `Float32Array`는 생성 시 지정한 크기로 고정되므로, 동적으로 크기를 변경할 수 없습니다. 필요할 경우 새로운 배열을 만들어야 합니다.

## 한 줄 요약
`Float32Array`는 JavaScript에서 32비트 부동 소수점 숫자를 효율적으로 저장하고 조작하기 위한 형식화된 배열입니다.