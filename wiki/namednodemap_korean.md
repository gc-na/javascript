<!--
Meta Description: # NamedNodeMap: JavaScript에서의 사용법과 이해 ## 개요 NamedNodeMap은 JavaScript에서 DOM(문서 객체 모델)에서 속성 노드의 집합을 나타내는 특수한 객체입니다. HTML 및 XML 문서에서 요소의 속성을 다루는 데 유용합니다....
Meta Keywords: 속성을, attributes, namednodemap은, 속성의, html
-->

# NamedNodeMap: JavaScript에서의 사용법과 이해

## 개요
NamedNodeMap은 JavaScript에서 DOM(문서 객체 모델)에서 속성 노드의 집합을 나타내는 특수한 객체입니다. HTML 및 XML 문서에서 요소의 속성을 다루는 데 유용합니다.

## 문서화
NamedNodeMap은 주로 `attributes` 속성을 통해 요소의 속성을 접근할 때 사용됩니다. 이 객체는 속성 노드의 리스트를 제공하며, 각 노드는 이름과 값을 가집니다. NamedNodeMap은 배열과 유사하지만, 배열이 아닌 특수한 형태의 객체입니다.

### 목적
- DOM 요소의 속성을 쉽게 관리하고 접근할 수 있도록 돕습니다.
- 속성의 이름과 값을 쌍으로 다룰 수 있습니다.

### 사용법
NamedNodeMap 객체는 `Element` 인터페이스의 `attributes` 프로퍼티를 통해 접근할 수 있습니다.

```javascript
const element = document.getElementById("example");
const attributes = element.attributes;
```

### 세부사항
- NamedNodeMap은 `length` 프로퍼티를 가지고 있으며, 이는 속성의 개수를 나타냅니다.
- 속성 노드는 `item(index)` 메서드를 사용하여 접근할 수 있습니다.
- 속성 노드를 직접 삭제하거나 수정할 수는 없지만, `setAttribute` 및 `removeAttribute` 메서드를 통해 요소의 속성을 조작할 수 있습니다.
  
## 예제
### 기본 사용 예
```html
<!DOCTYPE html>
<html>
<head>
    <title>NamedNodeMap 예제</title>
</head>
<body>
    <div id="example" class="container" data-role="example"></div>
    <script>
        const element = document.getElementById("example");
        const attributes = element.attributes;

        console.log("속성의 개수:", attributes.length); // 속성의 개수 출력

        for (let i = 0; i < attributes.length; i++) {
            const attr = attributes.item(i);
            console.log(attr.name, ":", attr.value); // 각 속성의 이름과 값 출력
        }
    </script>
</body>
</html>
```

## 설명
NamedNodeMap을 사용할 때 주의해야 할 몇 가지 사항은 다음과 같습니다:
- NamedNodeMap은 속성의 순서를 보장하지 않습니다. 따라서, 속성을 반복할 때 그 순서가 항상 동일하지 않을 수 있습니다.
- NamedNodeMap은 `delete` 연산자를 사용하여 속성을 직접 삭제할 수 없습니다. 대신 `removeAttribute` 메서드를 사용해야 합니다.
- 속성을 추가하거나 수정할 때는 반드시 `setAttribute` 메서드를 사용해야 합니다.

## 한 줄 요약
NamedNodeMap은 JavaScript에서 DOM 요소의 속성을 관리하고 접근하기 위한 객체입니다.