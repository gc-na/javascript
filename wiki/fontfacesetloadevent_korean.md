<!--
Meta Description: # FontFaceSetLoadEvent: 자바스크립트에서 글꼴 로딩 이벤트 처리하기 ## 개요 `FontFaceSetLoadEvent`는 자바스크립트에서 글꼴 로딩 상태를 감지하는 데 사용되는 이벤트입니다. 이 이벤트는 웹 페이지에서 사용자 정의 글꼴이 로드될 때 발...
Meta Keywords: fontfacesetloadevent, 글꼴이, fontfaceset, ready, 로드된
-->

# FontFaceSetLoadEvent: 자바스크립트에서 글꼴 로딩 이벤트 처리하기

## 개요
`FontFaceSetLoadEvent`는 자바스크립트에서 글꼴 로딩 상태를 감지하는 데 사용되는 이벤트입니다. 이 이벤트는 웹 페이지에서 사용자 정의 글꼴이 로드될 때 발생하며, 글꼴 로딩 완료 후 실행할 작업을 정의하는 데 유용합니다.

## 문서화

### 목적
`FontFaceSetLoadEvent`는 `FontFaceSet` 객체와 관련된 이벤트로, 웹 페이지에서 글꼴을 비동기적으로 로드할 때 발생합니다. 이 이벤트를 통해 개발자는 글꼴 로딩이 완료된 시점을 알 수 있으며, 그에 따른 추가 작업을 수행할 수 있습니다.

### 사용법
`FontFaceSetLoadEvent`는 `FontFaceSet`의 `ready` 프로미스를 통해 사용할 수 있습니다. `ready`는 페이지에 로드된 모든 글꼴의 로딩이 완료될 때까지 기다렸다가 결과를 제공합니다.

### 세부 사항
- **이벤트 종류**: `FontFaceSetLoadEvent`
- **속성**: 
  - `fontfaces` : 로드된 글꼴의 배열
- **메서드**: 
  - `FontFaceSet.load()`: 특정 글꼴을 로드하는 메서드입니다.

## 예제

```javascript
// 글꼴 로딩 이벤트 처리하기
document.fonts.ready.then(function(fonts) {
    console.log('모든 글꼴이 로드되었습니다:', fonts);
}).catch(function(error) {
    console.error('글꼴 로딩 중 오류 발생:', error);
});
```

이 예제에서는 `document.fonts.ready`를 사용하여 모든 글꼴이 로드될 때까지 기다린 후, 성공적으로 로드된 글꼴 정보를 로그에 출력합니다.

## 설명
- **일반적인 오류**: `FontFaceSetLoadEvent`는 모든 글꼴이 로드된 후에만 발생하므로, 이를 잘못 이해하고 즉시 작업을 수행하려 하면 오류가 발생할 수 있습니다.
- **비동기 처리**: `FontFaceSet`는 비동기적으로 작동하므로, 글꼴 로딩이 완료될 때까지 기다리는 것이 중요합니다. 이를 위해 `.then()`과 `.catch()`를 사용하여 성공 및 오류 처리를 구현합니다.

## 한 줄 요약
`FontFaceSetLoadEvent`는 자바스크립트에서 사용자 정의 글꼴의 로딩 완료 여부를 확인하고 처리하는 데 사용되는 이벤트입니다.