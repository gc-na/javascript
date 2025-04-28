<!--
Meta Description: # KeyboardLayoutMap: 자바스크립트에서의 키보드 레이아웃 맵 ## 개요 `KeyboardLayoutMap`은 자바스크립트에서 사용자의 현재 키보드 레이아웃과 관련된 정보를 제공하는 객체입니다. 이 객체를 통해 다양한 키 입력에 대한 정보를 쉽게 처리할 수...
Meta Keywords: 키보드, keyboardlayoutmap, 사용자의, 정보를, event
-->

# KeyboardLayoutMap: 자바스크립트에서의 키보드 레이아웃 맵

## 개요
`KeyboardLayoutMap`은 자바스크립트에서 사용자의 현재 키보드 레이아웃과 관련된 정보를 제공하는 객체입니다. 이 객체를 통해 다양한 키 입력에 대한 정보를 쉽게 처리할 수 있으며, 특히 다국어 지원 및 키 입력 이벤트를 다루는 데 유용합니다.

## 문서화
### 목적
`KeyboardLayoutMap`은 웹 애플리케이션이 사용자의 키보드 레이아웃을 인식하고 이에 따라 적절한 키 값을 처리할 수 있도록 돕는 기능을 제공합니다. 이는 특히 다양한 언어와 키보드 레이아웃을 지원하는 애플리케이션에서 중요합니다.

### 사용법
`KeyboardLayoutMap` 객체는 `KeyboardEvent.getKeyboardLayoutMap()` 메서드를 통해 접근할 수 있습니다. 이 메서드는 현재 키보드 레이아웃에 대한 맵을 반환하며, 각 키의 인식된 값을 포함합니다.

### 세부 사항
- **타입**: `KeyboardLayoutMap`은 키보드 레이아웃 정보를 담고 있는 `Map` 객체입니다.
- **키**: 각 키의 식별자는 문자열 형식으로, 각 키의 물리적 위치를 나타냅니다.
- **값**: 각 키에 대한 값은 사용자의 키보드 레이아웃에 따라 달라지는 문자열입니다.

## 예시
### 기본 사용 예제
다음은 `KeyboardLayoutMap`을 사용하는 기본적인 예제입니다.

```javascript
document.addEventListener('keydown', async (event) => {
    const layoutMap = await event.getKeyboardLayoutMap();
    const keyValue = layoutMap.get(event.key);
    
    console.log(`Pressed key: ${event.key}, Value: ${keyValue}`);
});
```

이 코드는 키보드에서 누른 키에 대한 값을 콘솔에 출력합니다.

## 설명
- **일반적인 함정**: `KeyboardLayoutMap`은 모든 브라우저에서 지원되지 않을 수 있습니다. 따라서, 이 기능을 사용하기 전에 브라우저 호환성을 확인하는 것이 중요합니다.
- **키 매핑 차이**: 동일한 키라도 다양한 키보드 레이아웃에 따라 다른 값을 가질 수 있으므로, 다국어 지원이 필요한 애플리케이션에서는 이를 고려해야 합니다.
- **비동기 처리**: `getKeyboardLayoutMap()` 메서드는 비동기적으로 동작하므로, 항상 `await` 키워드를 사용하여 결과를 처리해야 합니다.

## 한 줄 요약
`KeyboardLayoutMap`은 자바스크립트에서 사용자의 키보드 레이아웃을 인식하고 해당 키에 대한 정보를 제공하는 객체입니다.