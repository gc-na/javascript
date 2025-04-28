<!--
Meta Description: # JavaScript의 Promise: 비동기 프로그래밍의 핵심 ## 개요 JavaScript의 Promise는 비동기 작업의 완료 또는 실패를 나타내는 객체입니다. Promise를 사용하면 비동기 코드의 가독성을 높이고, 에러 처리를 보다 간편하게 할 수 있습니다....
Meta Keywords: 비동기, promise, promise는, resolve, reject
-->

# JavaScript의 Promise: 비동기 프로그래밍의 핵심

## 개요
JavaScript의 Promise는 비동기 작업의 완료 또는 실패를 나타내는 객체입니다. Promise를 사용하면 비동기 코드의 가독성을 높이고, 에러 처리를 보다 간편하게 할 수 있습니다.

## 문서화

### 목적
Promise는 비동기 작업의 결과를 나타내며, 이러한 작업이 성공적으로 완료되었는지 또는 실패했는지를 확인할 수 있는 방법을 제공합니다. 이는 특히 AJAX 요청, 타이머, 파일 I/O 등 비동기 작업에서 유용합니다.

### 사용법
Promise는 `new Promise(executor)` 구문을 사용하여 생성합니다. `executor`는 두 개의 매개변수(`resolve`와 `reject`)를 가지는 함수입니다. 

```javascript
const myPromise = new Promise((resolve, reject) => {
    // 비동기 작업 수행
    if (/* 작업 성공 */) {
        resolve('성공!');
    } else {
        reject('실패!');
    }
});
```

Promise는 `.then()`과 `.catch()` 메서드를 사용하여 결과를 처리할 수 있습니다.

### 세부사항
- **상태**: Promise는 세 가지 상태를 가집니다.
  - `대기(pending)`: 초기 상태, 비동기 작업이 완료되지 않음.
  - `이행(fulfilled)`: 비동기 작업이 성공적으로 완료됨.
  - `거부(rejected)`: 비동기 작업이 실패함.

- **체인 가능성**: Promise는 연속적으로 `.then()`과 `.catch()`를 체이닝할 수 있어, 비동기 작업의 흐름을 쉽게 관리할 수 있습니다.

## 예제

### 기본 사용 예제
```javascript
const fetchData = new Promise((resolve, reject) => {
    setTimeout(() => {
        const data = { id: 1, name: 'John' };
        resolve(data);
    }, 2000);
});

fetchData
    .then(data => {
        console.log('데이터:', data);
    })
    .catch(error => {
        console.error('오류:', error);
    });
```

### 에러 처리 예제
```javascript
const fetchDataWithError = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject('데이터를 가져오는 데 실패했습니다.');
    }, 2000);
});

fetchDataWithError
    .then(data => {
        console.log('데이터:', data);
    })
    .catch(error => {
        console.error('오류:', error);
    });
```

## 설명
Promise를 사용할 때 주의할 점은 다음과 같습니다:
- **중첩된 Promise**: Promise 안에서 또 다른 Promise를 사용할 때는 체인 구조를 유지해야 합니다. 그렇지 않으면 예기치 않은 동작을 할 수 있습니다.
- **에러 전파**: Promise 체인 내에서 에러가 발생하면, 그 에러는 체인의 마지막에 있는 `.catch()`로 전파됩니다. 따라서 적절한 에러 핸들링이 필요합니다.
- **Promise.all()**: 여러 개의 Promise를 동시에 처리하려면 `Promise.all()`을 사용하여 모든 Promise가 완료될 때까지 기다릴 수 있습니다.

## 한 줄 요약
JavaScript의 Promise는 비동기 작업을 관리하고 에러 처리를 단순화하는 강력한 도구입니다.