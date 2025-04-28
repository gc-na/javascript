<!--
Meta Description: # HTMLTableRowElement: JavaScript에서 HTML 테이블 행을 다루는 방법 ## 개요 `HTMLTableRowElement`는 JavaScript에서 HTML 테이블의 행을 나타내는 객체로, `<tr>` 요소에 대한 프로퍼티와 메서드를 제공합니다...
Meta Keywords: var, document, htmltablerowelement, 있습니다, 테이블
-->

# HTMLTableRowElement: JavaScript에서 HTML 테이블 행을 다루는 방법

## 개요
`HTMLTableRowElement`는 JavaScript에서 HTML 테이블의 행을 나타내는 객체로, `<tr>` 요소에 대한 프로퍼티와 메서드를 제공합니다. 이 객체를 사용하면 테이블 행을 생성, 수정 및 조작할 수 있습니다.

## 문서화
`HTMLTableRowElement`는 DOM (Document Object Model)의 일부로, HTML 테이블의 각 행을 표현합니다. 이 객체는 다음과 같은 목적으로 사용됩니다:

- **행 추가**: 새로운 테이블 행을 생성하고 기존 테이블에 추가할 수 있습니다.
- **행 수정**: 기존 테이블 행의 내용을 업데이트하거나 스타일을 변경할 수 있습니다.
- **행 삭제**: 특정 조건에 따라 테이블 행을 삭제할 수 있습니다.

### 사용법
`HTMLTableRowElement`는 일반적으로 JavaScript의 `document.createElement()` 메서드를 사용하여 생성할 수 있습니다. 다음은 기본적인 사용법입니다.

```javascript
// 새로운 tr 요소 생성
var row = document.createElement('tr');

// td 요소 생성 및 추가
var cell1 = document.createElement('td');
cell1.textContent = '첫 번째 셀';
row.appendChild(cell1);

var cell2 = document.createElement('td');
cell2.textContent = '두 번째 셀';
row.appendChild(cell2);

// tbody에 행 추가
var tbody = document.querySelector('tbody');
tbody.appendChild(row);
```

## 예제
### 예제 1: 기본 테이블 행 추가
```javascript
// 테이블에 새로운 행 추가하기
var table = document.getElementById('myTable');
var newRow = table.insertRow();

var cell1 = newRow.insertCell(0);
cell1.textContent = '새로운 셀 1';

var cell2 = newRow.insertCell(1);
cell2.textContent = '새로운 셀 2';
```

### 예제 2: 행 삭제하기
```javascript
// 특정 인덱스의 행 삭제하기
var table = document.getElementById('myTable');
var rowIndex = 1; // 삭제할 행의 인덱스
table.deleteRow(rowIndex);
```

## 설명
- **DOM 조작**: `HTMLTableRowElement`를 사용할 때, DOM의 구조를 이해해야 합니다. 잘못된 부모 요소에 행을 추가하면 원하는 결과를 얻지 못할 수 있습니다.
- **인덱스 관리**: 행 삭제 시, 인덱스를 잘 관리해야 합니다. 삭제 후에는 남은 행의 인덱스가 변경됩니다.
- **속성 접근**: `HTMLTableRowElement`는 `rowIndex`, `cells`, `style` 등 다양한 속성을 제공합니다. 이를 통해 CSS 스타일링이나 다른 DOM 조작을 쉽게 할 수 있습니다.

## 요약
`HTMLTableRowElement`는 JavaScript에서 HTML 테이블의 행을 생성, 수정 및 관리하는 데 유용한 객체입니다.