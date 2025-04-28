<!--
Meta Description: # JavaScript에서 "closed"의 의미와 사용법 ## 개요 JavaScript에서 "closed"는 일반적으로 웹 브라우저의 창이나 탭이 닫혀 있는지 여부를 확인하는 데 사용됩니다. 이는 주로 `Window` 객체와 관련된 메서드와 프로퍼티에서 나타납니다. ...
Meta Keywords: closed, popup, console, log, window
-->

# JavaScript에서 "closed"의 의미와 사용법

## 개요
JavaScript에서 "closed"는 일반적으로 웹 브라우저의 창이나 탭이 닫혀 있는지 여부를 확인하는 데 사용됩니다. 이는 주로 `Window` 객체와 관련된 메서드와 프로퍼티에서 나타납니다.

## 문서화
"closed"는 웹 브라우저에서 특정 창이 닫혔는지를 확인하는 `Window` 객체의 속성입니다. 이 속성은 Boolean 값을 반환하며, 창이 닫혀 있으면 `true`, 그렇지 않으면 `false`를 반환합니다. 주로 팝업 창을 열고 닫는 상황에서 유용하게 사용됩니다.

### 사용법
`closed` 속성은 `Window` 객체의 인스턴스에서 접근할 수 있습니다. 예를 들어, 팝업 창을 열고 그 창의 상태를 확인하는 데 사용됩니다.

```javascript
let popup = window.open("http://example.com", "popupWindow", "width=600,height=400");

// 팝업이 열려 있는지 확인
if (popup && !popup.closed) {
    console.log("팝업이 열려 있습니다.");
} else {
    console.log("팝업이 닫혔습니다.");
}
```

## 예제
```javascript
// 팝업 창 열기
let myWindow = window.open("", "myWindow", "width=200,height=100");

// 2초 후에 상태 확인
setTimeout(function() {
    if (myWindow.closed) {
        console.log("창이 닫혔습니다.");
    } else {
        console.log("창이 열려 있습니다.");
    }
}, 2000);

// 팝업 창 닫기
myWindow.close();
```

## 설명
"closed" 속성을 사용할 때 주의해야 할 점은 팝업 창이 사용자의 행동에 따라 닫힐 수 있으므로, 비동기적으로 창의 상태를 체크해야 한다는 점입니다. 또한, 팝업 창이 정상적으로 열리지 않거나, 보안 설정에 의해 차단될 경우 `popup` 변수는 `null`이 될 수 있습니다. 이 경우 `closed` 속성에 접근하기 전에 `popup`이 유효한지 확인해야 합니다.

```javascript
if (popup) {
    if (popup.closed) {
        console.log("팝업이 닫혔습니다.");
    } else {
        console.log("팝업이 열려 있습니다.");
    }
} else {
    console.log("팝업 창이 열리지 않았습니다.");
}
```

## 한 줄 요약
JavaScript에서 "closed"는 특정 창이 닫혔는지를 확인하는 `Window` 객체의 Boolean 속성입니다.