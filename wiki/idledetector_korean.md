<!--
Meta Description: # IdleDetector: 자바스크립트에서의 비활성 감지 기능 ## 개요 IdleDetector는 사용자가 일정 시간 동안 상호작용을 하지 않을 때 이를 감지하는 JavaScript API로, 웹 애플리케이션의 사용자 경험을 개선하는 데 도움을 줍니다. ## 문서화 ...
Meta Keywords: idledetector, 비활성, 있습니다, javascript, 사용자가
-->

# IdleDetector: 자바스크립트에서의 비활성 감지 기능

## 개요
IdleDetector는 사용자가 일정 시간 동안 상호작용을 하지 않을 때 이를 감지하는 JavaScript API로, 웹 애플리케이션의 사용자 경험을 개선하는 데 도움을 줍니다.

## 문서화

### 목적
IdleDetector는 사용자의 비활성 상태를 감지하여, 이를 기반으로 다양한 동작을 수행할 수 있도록 합니다. 예를 들어, 사용자가 일정 시간 동안 마우스나 키보드를 사용하지 않으면 자동으로 로그아웃하거나 경고 메시지를 표시하는 기능을 구현할 수 있습니다.

### 사용법
IdleDetector API는 다음과 같은 방식으로 사용할 수 있습니다:

1. **IdleDetector 인스턴스 생성**  
   `IdleDetector` 객체를 생성하고 이벤트 리스너를 추가하여 사용자의 비활성 상태를 모니터링합니다.

   ```javascript
   const idleDetector = new IdleDetector();
   ```

2. **비활성 감지 시작**  
   `start()` 메서드를 호출하여 감지를 시작합니다.

   ```javascript
   idleDetector.start();
   ```

3. **이벤트 리스너 추가**  
   비활성 상태가 감지되면 `idle` 이벤트가 발생합니다. 이에 대한 핸들러를 추가할 수 있습니다.

   ```javascript
   idleDetector.addEventListener('idle', () => {
       console.log('사용자가 비활성 상태입니다.');
   });
   ```

4. **비활성 감지 중지**  
   더 이상 비활성을 감지할 필요가 없을 경우 `stop()` 메서드를 호출하여 감지를 중지합니다.

   ```javascript
   idleDetector.stop();
   ```

### 세부 사항
- **속성**: `IdleDetector`는 사용자의 비활성 상태를 감지하기 위해 `threshold` 속성을 설정할 수 있습니다. 이 값은 사용자가 비활성 상태로 간주되는 시간(밀리초 단위)을 정의합니다.
- **이벤트**: `idle` 외에도 `active` 이벤트가 있어 사용자가 다시 활동을 시작했을 때 이를 감지할 수 있습니다.

## 예제

### 기본 사용 예제

```javascript
const idleDetector = new IdleDetector();

idleDetector.addEventListener('idle', () => {
    console.log('비활성 상태입니다.');
});

idleDetector.addEventListener('active', () => {
    console.log('활성 상태로 복귀했습니다.');
});

idleDetector.start();
```

### 사용자 정의 비활성 시간 설정

```javascript
const idleDetector = new IdleDetector({ threshold: 30000 }); // 30초 비활성 감지
idleDetector.start();
```

## 설명
- **일부 브라우저 지원**: `IdleDetector`는 모든 브라우저에서 지원되지 않을 수 있습니다. 최신 브라우저에서만 사용 가능하므로, 사용하기 전에 지원 여부를 확인해야 합니다.
- **비활성 감지 정확성**: 사용자의 비활성 상태를 감지하는 정확성은 브라우저와 운영 체제에 따라 달라질 수 있습니다. 일부 브라우저에서는 더 빠르게 감지할 수 있습니다.
- **타이머 설정**: 비활성 상태 감지 시 타이머를 설정하여 사용자가 다시 활동하게 되면 자동으로 비활성 상태를 해제할 수 있습니다.

## 한 줄 요약
IdleDetector는 JavaScript에서 사용자의 비활성 상태를 감지하여 웹 애플리케이션의 사용자 경험을 향상시키는 API입니다.