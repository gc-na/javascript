<!--
Meta Description: # JavaScript에서 이미지 다루기: 이미지 처리 및 조작 가이드 ## 개요 JavaScript는 웹 애플리케이션에서 이미지를 동적으로 생성, 조작 및 표시하는 강력한 기능을 제공합니다. HTML `<img>` 요소와 함께 사용할 수 있는 다양한 JavaScrip...
Meta Keywords: img, 이미지, 이미지를, javascript, document
-->

# JavaScript에서 이미지 다루기: 이미지 처리 및 조작 가이드

## 개요
JavaScript는 웹 애플리케이션에서 이미지를 동적으로 생성, 조작 및 표시하는 강력한 기능을 제공합니다. HTML `<img>` 요소와 함께 사용할 수 있는 다양한 JavaScript 메서드를 통해 개발자는 이미지의 로딩, 스타일링 및 이벤트 처리 등을 쉽게 구현할 수 있습니다.

## 문서화
JavaScript에서 이미지를 다루는 것은 웹 개발의 중요한 부분입니다. 이미지는 사용자 인터페이스를 풍부하게 만들고, 시각적 요소를 추가하는 데 필수적입니다. JavaScript를 사용하여 이미지의 소스를 변경하거나, 이미지를 로드하고, 사용자와 상호 작용하는 기능을 추가할 수 있습니다. 여기서는 JavaScript를 통해 이미지를 어떻게 처리하는지에 대한 기본적인 방법을 설명합니다.

### 목적
- 웹 페이지에서 이미지를 동적으로 표시하고 조작하기 위해.
- 사용자 상호 작용에 따라 이미지 변경 및 애니메이션 효과를 추가하기 위해.

### 사용법
1. **이미지 생성**: JavaScript를 사용하여 새로운 이미지 요소를 생성할 수 있습니다.
    ```javascript
    const img = document.createElement('img');
    img.src = 'image.jpg';
    document.body.appendChild(img);
    ```

2. **이미지 소스 변경**: 기존의 이미지를 새 이미지로 변경할 수 있습니다.
    ```javascript
    const img = document.querySelector('img');
    img.src = 'new-image.jpg';
    ```

3. **이벤트 리스너 추가**: 이미지에 클릭 이벤트를 추가하여 사용자와의 상호 작용을 처리할 수 있습니다.
    ```javascript
    img.addEventListener('click', () => {
        alert('이미지가 클릭되었습니다!');
    });
    ```

## 예제
### 기본 이미지 생성 예제
```javascript
const img = document.createElement('img');
img.src = 'https://example.com/image.jpg';
img.alt = '예시 이미지';
document.body.appendChild(img);
```

### 클릭 이벤트 예제
```javascript
const img = document.querySelector('img');
img.addEventListener('click', () => {
    alert('이미지가 클릭되었습니다!');
});
```

### 이미지 소스 변경 예제
```javascript
const img = document.querySelector('img');
img.src = 'https://example.com/new-image.jpg';
```

## 설명
JavaScript에서 이미지를 다룰 때 몇 가지 주의할 점이 있습니다:

- **이미지 로딩 시간**: 큰 이미지 파일은 로딩 시간이 길어질 수 있으므로, 최적화된 이미지를 사용하는 것이 좋습니다.
- **alt 속성**: 접근성을 위해 이미지에 항상 `alt` 속성을 추가해야 합니다.
- **CORS 문제**: 다른 도메인에서 이미지를 로드할 때 CORS(Cross-Origin Resource Sharing) 정책을 준수해야 합니다.

## 한 줄 요약
JavaScript는 웹 애플리케이션에서 이미지를 동적으로 생성하고 조작할 수 있는 강력한 도구를 제공합니다.