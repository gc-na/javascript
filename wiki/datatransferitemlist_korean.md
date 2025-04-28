<!--
Meta Description: # DataTransferItemList: 자바스크립트에서의 데이터 전송 항목 목록 ## 개요 `DataTransferItemList`는 HTML5 Drag and Drop API의 일부로, 드래그 앤 드롭 기능에서 데이터 항목을 관리하는 데 사용됩니다. 이 객체는 드...
Meta Keywords: datatransferitemlist, 데이터, 드래그, datatransfer, 있습니다
-->

# DataTransferItemList: 자바스크립트에서의 데이터 전송 항목 목록

## 개요
`DataTransferItemList`는 HTML5 Drag and Drop API의 일부로, 드래그 앤 드롭 기능에서 데이터 항목을 관리하는 데 사용됩니다. 이 객체는 드래그된 데이터의 목록을 나타내며, 각 항목은 `DataTransferItem` 객체로 표현됩니다.

## 문서화
`DataTransferItemList`는 사용자가 드래그 앤 드롭을 통해 데이터를 전송할 때, 전송될 데이터 항목을 추가하거나 제거할 수 있는 기능을 제공합니다. 이 객체는 `DataTransfer` 객체의 `items` 속성을 통해 접근할 수 있습니다.

### 목적
`DataTransferItemList`의 주된 목적은 여러 종류의 데이터를 드래그 앤 드롭 할 때, 해당 데이터를 관리하고 조작할 수 있도록 하는 것입니다. 이를 통해 개발자는 사용자 인터페이스를 보다 직관적으로 만들 수 있습니다.

### 사용법
1. 드래그 앤 드롭 이벤트가 발생한 요소에서 `DataTransfer` 객체를 생성합니다.
2. `DataTransfer` 객체의 `items` 속성을 통해 `DataTransferItemList`에 접근합니다.
3. `add()` 메서드를 사용하여 데이터 항목을 추가하고, `remove()` 메서드를 사용하여 항목을 제거할 수 있습니다.

## 예제
```javascript
// 드래그 앤 드롭을 위한 이벤트 리스너 설정
const dropArea = document.getElementById('drop-area');

dropArea.addEventListener('dragover', (event) => {
    event.preventDefault(); // 기본 동작을 방지
});

dropArea.addEventListener('drop', (event) => {
    event.preventDefault(); // 기본 동작을 방지

    const dataTransfer = event.dataTransfer;
    const itemList = dataTransfer.items;

    for (let i = 0; i < itemList.length; i++) {
        const item = itemList[i];
        console.log(`항목 ${i}: ${item.getAsFile().name}`);
    }
});

// 항목 추가 예제
dataTransfer.items.add(new File(["내용"], "example.txt"));
```

## 설명
- **일반적인 함정**: `DataTransferItemList`는 드래그 앤 드롭이 발생할 때만 유효합니다. 따라서 이벤트 리스너 내에서만 접근할 수 있습니다.
- **지원되는 브라우저**: 대부분의 현대 브라우저는 `DataTransferItemList`를 지원하지만, 구형 브라우저에서는 호환성 문제가 있을 수 있습니다.
- **데이터 유형**: `DataTransferItem` 객체는 파일, HTML, 텍스트 등 다양한 데이터 유형을 지원합니다. 각 항목의 데이터 유형을 확인하려면 `kind` 속성을 사용할 수 있습니다.

## 한 문장 요약
`DataTransferItemList`는 드래그 앤 드롭 인터페이스에서 데이터 항목을 관리하는 객체로, 사용자가 전송하려는 데이터의 목록을 조작할 수 있게 해줍니다.