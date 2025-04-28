<!--
Meta Description: # JavaScript의 Fence: 비동기 처리를 위한 패턴 ## 개요 JavaScript에서 "Fence"는 비동기 처리를 제어하는 데 사용되는 패턴으로, 동시 실행을 제한하고 특정 조건을 충족하는 경우에만 실행되는 작업을 관리하는 데 유용합니다. 이 패턴은 특히 ...
Meta Keywords: resolve, 비동기, promise, fence, task
-->

# JavaScript의 Fence: 비동기 처리를 위한 패턴

## 개요
JavaScript에서 "Fence"는 비동기 처리를 제어하는 데 사용되는 패턴으로, 동시 실행을 제한하고 특정 조건을 충족하는 경우에만 실행되는 작업을 관리하는 데 유용합니다. 이 패턴은 특히 대규모 애플리케이션에서 성능과 안정성을 높이는 데 도움이 됩니다.

## 문서화
### 목적
Fence 패턴은 비동기 작업의 실행을 조절하여 자원 경쟁을 방지하고, 작업 실행 순서를 관리함으로써 애플리케이션의 효율성을 향상시키는 것을 목적으로 합니다.

### 사용법
Fence 패턴은 주로 Promise 및 async/await 구문과 함께 사용됩니다. 일반적으로, 여러 개의 비동기 작업을 동시에 실행할 때, 한 번에 처리할 수 있는 작업의 수를 제한하여 자원 소모를 최소화합니다.

### 세부사항
- **비동기 작업 제한**: 한 번에 실행할 수 있는 비동기 작업의 수를 제한합니다. 예를 들어, 최대 3개의 작업만 동시에 실행하도록 설정할 수 있습니다.
- **작업 큐**: 실행할 작업을 대기열에 추가하고, 활성 작업이 종료될 때마다 대기열에서 다음 작업을 실행합니다.
- **에러 처리**: 작업 중 오류가 발생한 경우, 적절한 에러 처리를 통해 애플리케이션의 안정성을 높입니다.

## 예제
```javascript
async function fence(limit, tasks) {
    const results = [];
    const executing = new Set();

    for (const task of tasks) {
        const p = Promise.resolve().then(() => task());
        results.push(p);

        executing.add(p);
        if (executing.size >= limit) {
            await Promise.race(executing);
        }

        p.then(() => executing.delete(p));
    }

    return Promise.all(results);
}

// 사용 예시
const tasks = [
    () => new Promise(resolve => setTimeout(() => { console.log('Task 1'); resolve(); }, 1000)),
    () => new Promise(resolve => setTimeout(() => { console.log('Task 2'); resolve(); }, 500)),
    () => new Promise(resolve => setTimeout(() => { console.log('Task 3'); resolve(); }, 2000)),
    () => new Promise(resolve => setTimeout(() => { console.log('Task 4'); resolve(); }, 100)),
    () => new Promise(resolve => setTimeout(() => { console.log('Task 5'); resolve(); }, 1500)),
];

fence(3, tasks);
```

## 설명
- **공통 오류**: Fence 패턴을 잘못 구현하면, 모든 작업이 동시에 실행되거나, 대기열이 무한히 늘어날 수 있습니다. 따라서 작업 수를 정확히 설정하고 상태를 관리하는 것이 중요합니다.
- **성능 고려**: 너무 많은 작업을 동시에 실행하면, 자원 소모가 급격히 증가할 수 있습니다. 따라서 적절한 제한을 설정하는 것이 필요합니다.
- **비동기 처리의 이해**: JavaScript의 비동기 처리 방식에 대한 기본적인 이해가 필요합니다. Promise와 async/await의 사용법을 숙지해야 합니다.

## 한 줄 요약
JavaScript의 Fence 패턴은 비동기 작업의 실행을 제한하여 성능과 안정성을 향상시키는 유용한 방법입니다.