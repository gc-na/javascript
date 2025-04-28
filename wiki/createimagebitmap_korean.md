<!--
Meta Description: # createImageBitmap: JavaScript에서 이미지 비트맵 생성하기 ## 개요 `createImageBitmap`은 JavaScript에서 이미지 데이터, HTML 요소, 또는 비트맵을 비동기적으로 처리하여 이미지 비트맵 객체를 생성하는 기능입니다. 이...
Meta Keywords: createimagebitmap, 이미지, imgelement, const, 비트맵
-->

# createImageBitmap: JavaScript에서 이미지 비트맵 생성하기

## 개요
`createImageBitmap`은 JavaScript에서 이미지 데이터, HTML 요소, 또는 비트맵을 비동기적으로 처리하여 이미지 비트맵 객체를 생성하는 기능입니다. 이 기능은 웹 애플리케이션에서 이미지 로딩 성능을 향상시키기 위해 사용됩니다.

## 문서화
### 목적
`createImageBitmap` 함수는 다양한 소스(이미지, 캔버스, 비디오 등)로부터 이미지 비트맵 객체를 생성하여, 그래픽 작업이나 애니메이션에서 더 나은 성능을 제공하는 것을 목적으로 합니다.

### 사용법
`createImageBitmap`은 다음과 같이 사용됩니다:

```javascript
createImageBitmap(imageSource, options)
```

- `imageSource`: 이미지 비트맵을 생성할 소스입니다. 소스는 `HTMLImageElement`, `HTMLCanvasElement`, `HTMLVideoElement`, `ImageBitmap`, 또는 `Blob` 객체가 될 수 있습니다.
- `options`: 선택적 매개변수로, 비트맵의 크기와 비율을 정의하는 객체입니다. 이 객체는 `resizeWidth`, `resizeHeight`, `cropping`, `imageOrientation` 등의 속성을 가질 수 있습니다.

### 반환값
이 함수는 `Promise` 객체를 반환하며, 이 `Promise`가 해결되면 `ImageBitmap` 객체가 반환됩니다.

## 예제
### 기본 사용 예제
아래는 `createImageBitmap`을 사용하여 이미지 비트맵을 생성하는 간단한 예제입니다.

```javascript
const imgElement = document.createElement('img');
imgElement.src = 'example.jpg';

imgElement.onload = () => {
    createImageBitmap(imgElement).then((bitmap) => {
        const canvas = document.getElementById('myCanvas');
        const ctx = canvas.getContext('2d');
        ctx.drawImage(bitmap, 0, 0);
    });
};
```

### 비트맵 크기 조정
비트맵의 크기를 조정할 수 있는 예제입니다.

```javascript
const imgElement = document.createElement('img');
imgElement.src = 'example.jpg';

imgElement.onload = () => {
    const options = {
        resizeWidth: 100,
        resizeHeight: 100,
    };
    createImageBitmap(imgElement, options).then((bitmap) => {
        const canvas = document.getElementById('myCanvas');
        const ctx = canvas.getContext('2d');
        ctx.drawImage(bitmap, 0, 0);
    });
};
```

## 설명
### 일반적인 주의사항
- **비동기 처리**: `createImageBitmap`은 비동기적으로 동작하므로, 이미지가 준비되지 않은 상태에서 접근하면 오류가 발생할 수 있습니다. 따라서 이미지가 로드된 후에 이 함수를 호출해야 합니다.
- **지원 브라우저**: 모든 브라우저가 이 기능을 지원하는 것은 아닙니다. 따라서 사용 전 브라우저 호환성을 확인하는 것이 좋습니다.
- **메모리 관리**: 비트맵 객체는 메모리를 사용할 수 있으므로, 더 이상 필요하지 않을 경우 적절히 해제해야 합니다.

## 한 줄 요약
`createImageBitmap`은 다양한 소스에서 비동기적으로 이미지 비트맵을 생성하여 웹 애플리케이션의 성능을 향상시키는 JavaScript 기능입니다.