<!--
Meta Description: # JavaScript GamepadEvent: 게임패드 이벤트 처리 ## 개요 GamepadEvent는 웹 브라우저에서 게임패드의 입력을 감지하고 처리할 수 있게 해주는 API입니다. 이 이벤트를 사용하면 JavaScript로 게임패드의 버튼 및 축 입력을 손쉽게 관...
Meta Keywords: gamepad, 게임패드, event, index, console
-->

# JavaScript GamepadEvent: 게임패드 이벤트 처리

## 개요
GamepadEvent는 웹 브라우저에서 게임패드의 입력을 감지하고 처리할 수 있게 해주는 API입니다. 이 이벤트를 사용하면 JavaScript로 게임패드의 버튼 및 축 입력을 손쉽게 관리할 수 있습니다.

## 문서화
### 목적
GamepadEvent는 사용자가 게임패드를 조작할 때 발생하는 이벤트를 통해 입력 상태를 감지하고, 이를 기반으로 게임이나 인터랙티브 애플리케이션의 반응을 구현할 수 있게 합니다. 이 API는 다양한 게임패드에 대한 지원을 제공하며, HTML5 게임 개발에 필수적인 요소입니다.

### 사용법
GamepadEvent는 주로 `gamepadconnected` 및 `gamepaddisconnected` 이벤트와 함께 사용됩니다. 이 이벤트는 게임패드가 연결되거나 연결 해제될 때 발생합니다.

```javascript
window.addEventListener("gamepadconnected", function(event) {
    console.log("게임패드 연결됨: ", event.gamepad);
});

window.addEventListener("gamepaddisconnected", function(event) {
    console.log("게임패드 연결 해제됨: ", event.gamepad);
});
```

### 세부 사항
- **event.gamepad**: 연결된 게임패드에 대한 정보를 담고 있는 객체입니다. 이 객체는 `id`, `index`, `buttons`, `axes`와 같은 프로퍼티를 포함합니다.
- **buttons**: 버튼의 상태를 나타내는 배열입니다. 각 버튼은 `pressed`와 `value` 프로퍼티를 가집니다.
- **axes**: 아날로그 스틱 및 트리거의 위치를 나타내는 배열입니다. 각 축은 -1.0에서 1.0 사이의 값을 가집니다.

## 예시
### 기본 사용 예
```javascript
window.addEventListener("gamepadconnected", function(event) {
    const gamepad = event.gamepad;
    console.log(`게임패드 ${gamepad.index}가 연결되었습니다: ${gamepad.id}`);
    
    // 버튼 상태 출력
    gamepad.buttons.forEach((button, index) => {
        console.log(`버튼 ${index}: ${button.pressed ? '눌림' : '안 눌림'}`);
    });
});
```

### 게임패드 입력 감지
```javascript
function checkGamepadInput() {
    const gamepads = navigator.getGamepads();
    if (gamepads) {
        const gamepad = gamepads[0]; // 첫 번째 게임패드
        if (gamepad) {
            gamepad.buttons.forEach((button, index) => {
                if (button.pressed) {
                    console.log(`버튼 ${index}이 눌렸습니다!`);
                }
            });
        }
    }
}

// 주기적으로 입력 체크
setInterval(checkGamepadInput, 100);
```

## 설명
GamepadEvent를 사용할 때 주의해야 할 점은, 모든 브라우저가 동일하게 지원하지 않을 수 있다는 점입니다. 특히 모바일 브라우저는 게임패드 지원이 제한적일 수 있습니다. 또한, 사용자가 게임패드를 연결한 후, 페이지가 로드되기 전에 이벤트가 발생할 수 있으므로, 초기화 시점을 적절히 조정해야 합니다.

## 한 줄 요약
GamepadEvent는 JavaScript를 통해 웹 애플리케이션에서 게임패드 입력을 감지하고 처리할 수 있게 해주는 API입니다.