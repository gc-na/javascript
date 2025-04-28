<!--
Meta Description: # JavaScript의 Intl: 국제화 및 지역화 기능 ## 개요 `Intl` 객체는 JavaScript에서 국제화 및 지역화를 위한 기능을 제공하는 내장 객체입니다. 이 객체를 사용하면 날짜, 시간, 숫자 및 통화를 다양한 언어 및 지역에 맞게 형식화할 수 있습니...
Meta Keywords: intl, numberformat, const, new, 객체는
-->

# JavaScript의 Intl: 국제화 및 지역화 기능

## 개요
`Intl` 객체는 JavaScript에서 국제화 및 지역화를 위한 기능을 제공하는 내장 객체입니다. 이 객체를 사용하면 날짜, 시간, 숫자 및 통화를 다양한 언어 및 지역에 맞게 형식화할 수 있습니다.

## 문서화

### 목적
`Intl` 객체는 다양한 로케일에 따라 문자열을 형식화하고 언어별로 설정할 수 있는 기능을 제공합니다. 이를 통해 개발자는 사용자에게 더 친숙하고 이해하기 쉬운 방식으로 데이터를 표시할 수 있습니다.

### 사용법
`Intl` 객체는 여러 개의 하위 객체와 메서드를 포함하고 있으며, 주요 하위 객체는 다음과 같습니다:

1. **Intl.NumberFormat**: 숫자를 특정 로케일에 맞게 형식화합니다.
2. **Intl.DateTimeFormat**: 날짜와 시간을 특정 로케일에 맞게 형식화합니다.
3. **Intl.Collator**: 문자열 비교 및 정렬을 특정 로케일에 맞게 처리합니다.
4. **Intl.PluralRules**: 복수형 규칙을 처리합니다.
5. **Intl.RelativeTimeFormat**: 상대 시간(예: "1시간 전")을 형식화합니다.

### 세부 사항
각 하위 객체는 생성자 함수로 사용되며, 로케일 및 옵션을 인수로 받아 다양한 형식화 기능을 제공합니다.

- **Intl.NumberFormat**
  ```javascript
  const numberFormat = new Intl.NumberFormat('ko-KR', { style: 'currency', currency: 'KRW' });
  console.log(numberFormat.format(1234567.89)); // "₩1,234,567.89"
  ```

- **Intl.DateTimeFormat**
  ```javascript
  const dateFormat = new Intl.DateTimeFormat('ko-KR', { year: 'numeric', month: 'long', day: 'numeric' });
  console.log(dateFormat.format(new Date())); // "2023년 10월 1일"
  ```

- **Intl.Collator**
  ```javascript
  const collator = new Intl.Collator('ko-KR');
  const result = collator.compare('가', '나');
  console.log(result); // -1 (가가 나보다 앞선다는 의미)
  ```

## 예시
아래는 `Intl` 객체를 사용하는 기본적인 예시입니다.

```javascript
// 숫자 형식화 예
const numberFormat = new Intl.NumberFormat('en-US');
console.log(numberFormat.format(1234567.89)); // "1,234,567.89"

// 날짜 형식화 예
const dateFormat = new Intl.DateTimeFormat('fr-FR');
console.log(dateFormat.format(new Date())); // "01/10/2023"

// 문자열 정렬 예
const items = ['사과', '배', '귤'];
const sortedItems = items.sort(collator.compare);
console.log(sortedItems); // ['귤', '배', '사과']
```

## 설명
`Intl` 객체를 사용할 때 주의해야 할 점은 로케일 및 옵션의 조합에 따라 형식화 결과가 달라질 수 있다는 것입니다. 또한, 일부 로케일에서는 특정 옵션이 지원되지 않을 수 있으므로, 항상 해당 로케일의 사양을 확인하는 것이 좋습니다.

- **일관성**: 여러 로케일에 대해 동일한 숫자 또는 날짜 형식을 사용하려면 올바른 로케일을 선택해야 합니다.
- **호환성**: 구형 브라우저에서는 `Intl` 객체의 일부 기능이 지원되지 않을 수 있으므로, 최신 환경에서의 사용을 권장합니다.

## 한 줄 요약
`Intl` 객체는 JavaScript에서 국제화 및 지역화를 위한 데이터를 형식화하는 데 유용한 기능을 제공합니다.