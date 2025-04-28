<!--
Meta Description: # JavaScript에서 CustomEvent: 사용자 정의 이벤트 생성하기 ## 개요 `CustomEvent`는 JavaScript에서 사용자 정의 이벤트를 생성할 수 있는 기능을 제공합니다. 이를 통해 개발자는 특정 상황에서 발생하는 이벤트를 정의하고, 이를 다른...
Meta Keywords: customevent, 이벤트, event, 사용자, 이벤트를
-->

# JavaScript에서 CustomEvent: 사용자 정의 이벤트 생성하기

## 개요
`CustomEvent`는 JavaScript에서 사용자 정의 이벤트를 생성할 수 있는 기능을 제공합니다. 이를 통해 개발자는 특정 상황에서 발생하는 이벤트를 정의하고, 이를 다른 코드나 컴포넌트에서 수신하여 처리할 수 있습니다.

## 문서화
`CustomEvent`는 사용자 정의 이벤트를 생성하는 데 사용됩니다. 기본적으로는 `Event` 클래스를 확장하여 사용하며, 추가적인 데이터를 전달할 수 있는 기능을 제공합니다.

### 사용법
`CustomEvent`를 생성하려면 다음과 같이 `new` 키워드를 사용하여 인스턴스를 생성합니다:

```javascript
const event = new CustomEvent("eventName", {
  detail: { key: "value" } // 추가 데이터
});
```

- **eventName**: 사용자 정의 이벤트의 이름입니다.
- **detail**: 이벤트와 함께 전달될 추가 데이터입니다. 이는 선택적이며 객체 형태로 제공됩니다.

### 이벤트 발생시키기
이벤트를 발생시키려면 대상 요소에서 `dispatchEvent` 메서드를 사용합니다:

```javascript
const element = document.getElementById("myElement");
element.dispatchEvent(event);
```

### 이벤트 수신하기
이벤트를 수신하려면 `addEventListener` 메서드를 사용하여 리스너를 등록합니다:

```javascript
element.addEventListener("eventName", function(event) {
  console.log(event.detail); // { key: "value" }
});
```

## 예제
```javascript
// 사용자 정의 이벤트 생성
const myEvent = new CustomEvent("myCustomEvent", {
  detail: { message: "Hello, World!" }
});

// 이벤트 리스너 등록
const myElement = document.getElementById("myElement");
myElement.addEventListener("myCustomEvent", function(event) {
  console.log(event.detail.message); // "Hello, World!"
});

// 이벤트 발생
myElement.dispatchEvent(myEvent);
```

## 설명
`CustomEvent` 사용 시 유의할 점은 다음과 같습니다:

1. **이벤트 전파**: `CustomEvent`는 기본적으로 이벤트 전파가 가능합니다. 이는 부모 요소에 이벤트가 전달될 수 있음을 의미합니다. 필요에 따라 `bubbles` 속성을 `true`로 설정하면 됩니다.
   
2. **이벤트 취소**: 기본 이벤트처럼 `CustomEvent`도 `preventDefault` 메서드를 통해 기본 동작을 취소할 수 있습니다.

3. **브라우저 호환성**: 일부 구형 브라우저에서는 `CustomEvent`를 지원하지 않을 수 있으므로, 이를 고려하여 폴리필을 사용하는 것이 좋습니다.

## 한 줄 요약
`CustomEvent`는 JavaScript에서 사용자 정의 이벤트를 생성하고, 추가 데이터를 전달할 수 있는 강력한 기능입니다.