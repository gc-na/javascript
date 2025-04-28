<!--
Meta Description: # 가상 키보드 기하학 변경 이벤트 (VirtualKeyboardGeometryChangeEvent) - 자바스크립트 ## 개요 가상 키보드 기하학 변경 이벤트는 웹 애플리케이션에서 가상 키보드의 크기나 위치가 변경될 때 발생하는 이벤트입니다. 이 이벤트는 특히 모바일...
Meta Keywords: 이벤트는, event, 키보드, 키보드의, 키보드가
-->

# 가상 키보드 기하학 변경 이벤트 (VirtualKeyboardGeometryChangeEvent) - 자바스크립트

## 개요
가상 키보드 기하학 변경 이벤트는 웹 애플리케이션에서 가상 키보드의 크기나 위치가 변경될 때 발생하는 이벤트입니다. 이 이벤트는 특히 모바일 디바이스에서 입력 필드의 UI를 동적으로 조정할 수 있는 기회를 제공합니다.

## 문서화
가상 키보드 기하학 변경 이벤트는 주로 모바일 웹 애플리케이션에서 사용됩니다. 사용자가 텍스트 입력 필드를 클릭하여 가상 키보드가 나타나거나 사라질 때, 이 이벤트는 해당 변화에 대한 정보를 제공합니다.

### 목적
- 모바일 브라우저에서 가상 키보드의 표시 상태가 변경될 때 UI를 업데이트할 수 있도록 합니다.

### 사용법
`VirtualKeyboardGeometryChangeEvent`는 `window` 객체에서 발생합니다. 이벤트 리스너를 추가하여 이 이벤트를 감지할 수 있습니다.

```javascript
window.addEventListener('virtualkeyboardgeometrychange', (event) => {
    const { height, width } = event.geometry;
    console.log(`가상 키보드 높이: ${height}, 너비: ${width}`);
});
```

### 세부 사항
- **이벤트 객체**: `VirtualKeyboardGeometryChangeEvent`는 `geometry` 속성을 포함하고 있으며, 이 속성은 가상 키보드의 높이와 너비에 대한 정보를 제공합니다.
- **호환성**: 현재 이 이벤트는 일부 최신 모바일 브라우저에서만 지원됩니다. 따라서 사용하기 전에 브라우저 호환성을 확인해야 합니다.

## 예시
1. **가상 키보드가 나타날 때**:
```javascript
window.addEventListener('virtualkeyboardgeometrychange', (event) => {
    if (event.geometry.height > 0) {
        console.log('가상 키보드가 표시되었습니다.');
    }
});
```

2. **가상 키보드가 사라질 때**:
```javascript
window.addEventListener('virtualkeyboardgeometrychange', (event) => {
    if (event.geometry.height === 0) {
        console.log('가상 키보드가 사라졌습니다.');
    }
});
```

## 설명
- **일반적인 함정**: 모든 브라우저가 `VirtualKeyboardGeometryChangeEvent`를 지원하지 않으므로, 이벤트를 사용할 때는 항상 호환성 확인이 필요합니다.
- **이벤트 발생 빈도**: 가상 키보드의 기하학이 변경될 때마다 이벤트가 발생하므로, 불필요한 호출을 방지하기 위해 최적화가 필요할 수 있습니다.

## 한 줄 요약
가상 키보드 기하학 변경 이벤트는 가상 키보드의 크기와 위치 변경을 감지하여 UI를 동적으로 조정할 수 있도록 돕는 자바스크립트 이벤트입니다.