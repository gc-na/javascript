<!--
Meta Description: # JavaScript의 getSelection: 텍스트 선택 기능 이해하기 ## 개요 `getSelection`은 사용자가 웹 페이지에서 선택한 텍스트를 가져오는 데 사용되는 JavaScript 메서드입니다. 이 메서드는 주로 텍스트 편집기, 문서 뷰어 및 기타 인터...
Meta Keywords: selection, getselection, 사용자가, 텍스트, 선택한
-->

# JavaScript의 getSelection: 텍스트 선택 기능 이해하기

## 개요
`getSelection`은 사용자가 웹 페이지에서 선택한 텍스트를 가져오는 데 사용되는 JavaScript 메서드입니다. 이 메서드는 주로 텍스트 편집기, 문서 뷰어 및 기타 인터랙티브 콘텐츠에서 텍스트 선택 상태를 확인하거나 조작할 때 유용합니다.

## 문서화
`getSelection` 메서드는 Document 객체의 메서드로, 현재 사용자가 선택한 텍스트 범위를 반환합니다. 반환되는 객체는 Selection 타입으로, 선택된 텍스트뿐만 아니라 그 위치와 크기 정보도 포함합니다.

### 사용법
```javascript
const selection = window.getSelection();
```

### 주요 세부사항
- **반환 타입**: `Selection` 객체
- **속성**: 선택된 텍스트, 시작 및 끝 위치, 범위 정보
- **범위**: `Selection` 객체는 사용자가 선택한 텍스트와 관련된 여러 범위를 포함할 수 있습니다.

## 예제
### 기본 사용 예제
```javascript
document.addEventListener('mouseup', function() {
    const selection = window.getSelection();
    const selectedText = selection.toString();
    console.log('선택된 텍스트:', selectedText);
});
```
위 코드는 사용자가 마우스를 떼는 순간 선택된 텍스트를 콘솔에 출력합니다.

### 여러 범위 선택 예제
```javascript
document.addEventListener('mouseup', function() {
    const selection = window.getSelection();
    if (selection.rangeCount > 0) {
        for (let i = 0; i < selection.rangeCount; i++) {
            const range = selection.getRangeAt(i);
            console.log('범위:', range);
        }
    }
});
```
이 예제는 사용자가 선택한 모든 범위를 반복하여 출력합니다.

## 설명
`getSelection` 메서드는 매우 유용하지만, 몇 가지 주의해야 할 점이 있습니다. 

- **브라우저 호환성**: `getSelection`은 대부분의 현대 브라우저에서 지원되지만, 구버전 브라우저에서는 문제가 발생할 수 있습니다. 
- **선택 상태**: 사용자가 선택한 텍스트가 없을 경우, 반환되는 `Selection` 객체는 비어 있습니다. 이를 확인하지 않고 사용하려고 하면 오류가 발생할 수 있습니다.
- **DOM 변경**: DOM이 변경되면 선택 상태가 사라질 수 있습니다. 따라서 `getSelection`을 사용한 후 바로 DOM을 변경하는 것은 피해야 합니다.

## 한 줄 요약
`getSelection`은 현재 사용자가 선택한 텍스트를 가져오는 JavaScript 메서드입니다.