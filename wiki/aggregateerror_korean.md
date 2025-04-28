<!--
Meta Description: # AggregateError: JavaScript에서의 집계 오류 처리 ## 개요 `AggregateError`는 JavaScript에서 여러 오류를 하나의 오류 객체로 집계하여 처리할 수 있는 기능을 제공합니다. 이는 주로 프로미스의 병렬 처리 과정에서 발생하는 여...
Meta Keywords: aggregateerror, error, new, errors, 오류를
-->

# AggregateError: JavaScript에서의 집계 오류 처리

## 개요
`AggregateError`는 JavaScript에서 여러 오류를 하나의 오류 객체로 집계하여 처리할 수 있는 기능을 제공합니다. 이는 주로 프로미스의 병렬 처리 과정에서 발생하는 여러 오류를 효율적으로 관리하는 데 유용합니다.

## 문서화
### 목적
`AggregateError`는 여러 오류를 배열 형태로 그룹화하여 사용자에게 더 명확한 오류 메시지를 제공합니다. 이는 특히 `Promise.any()`와 같은 비동기 작업에서 유용합니다.

### 사용법
`AggregateError`를 사용하려면 다음과 같이 새로운 인스턴스를 생성할 수 있습니다:

```javascript
const errors = [new Error('첫 번째 오류'), new Error('두 번째 오류')];
const aggregateError = new AggregateError(errors, '다음 오류가 발생했습니다.');
```

### 세부사항
- **생성자**: `AggregateError`의 생성자는 두 개의 인자를 받습니다.
  - `errors`: 오류 객체의 배열
  - `message`: 오류 메시지 (선택적)
  
- **속성**:
  - `errors`: 집계된 오류 객체의 배열을 반환합니다.
  
이 오류는 `Promise.any()` 메서드가 모든 프로미스가 거부될 경우 발생합니다.

## 예시
### 기본 사용 예
```javascript
try {
    Promise.any([
        Promise.reject(new Error('첫 번째 실패')),
        Promise.reject(new Error('두 번째 실패')),
        Promise.reject(new Error('세 번째 실패'))
    ]).catch((e) => {
        if (e instanceof AggregateError) {
            console.log(e.errors); // 모든 오류를 배열로 출력
            console.log(e.message); // '다음 오류가 발생했습니다.' 출력
        }
    });
} catch (error) {
    console.error(error);
}
```

### 집계 오류 처리 예
```javascript
const errors = [
    new Error('네트워크 오류'),
    new Error('타임아웃 오류'),
];

const aggregateError = new AggregateError(errors, '요청 중 오류가 발생했습니다.');
console.log(aggregateError.message); // '요청 중 오류가 발생했습니다.'
console.log(aggregateError.errors); // [Error: 네트워크 오류, Error: 타임아웃 오류]
```

## 설명
`AggregateError`는 주로 여러 개의 비동기 작업이 실패할 때 발생합니다. 이를 통해 사용자는 발생한 모든 오류를 한 번에 확인할 수 있으며, 각 오류를 개별적으로 처리할 필요가 없습니다. 

### 일반적인 함정
- **올바른 사용 시점**: `AggregateError`는 `Promise.any()`와 같은 메서드에서 주로 사용되며, 다른 프로미스 관련 메서드에서는 사용되지 않을 수 있습니다.
- **메시지의 명확성**: 오류 메시지는 명확하고 직관적으로 작성해야 사용자가 쉽게 이해할 수 있습니다. 

## 한 줄 요약
`AggregateError`는 JavaScript에서 여러 오류를 하나의 오류 객체로 집계하여 효율적으로 관리할 수 있게 해주는 기능입니다.