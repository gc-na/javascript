<!--
Meta Description: # MediaCapabilities: JavaScript에서 미디어 성능을 평가하는 방법 ## 개요 `MediaCapabilities`는 웹 브라우저에서 비디오 및 오디오 콘텐츠의 성능을 평가하고 지원 여부를 확인하는 JavaScript API입니다. 이 API는 다양...
Meta Keywords: mediacapabilities, error, console, 미디어, 비디오
-->

# MediaCapabilities: JavaScript에서 미디어 성능을 평가하는 방법

## 개요
`MediaCapabilities`는 웹 브라우저에서 비디오 및 오디오 콘텐츠의 성능을 평가하고 지원 여부를 확인하는 JavaScript API입니다. 이 API는 다양한 미디어 코덱과 해상도에 대해 하드웨어 가속 지원을 확인할 수 있는 방법을 제공합니다.

## 문서화
### 목적
`MediaCapabilities` API는 개발자가 사용자가 사용하는 장치의 미디어 재생 성능을 이해하고, 최적의 사용자 경험을 제공하기 위해 필요한 정보를 제공합니다. 이를 통해 개발자는 콘텐츠의 품질을 조정하거나, 특정 포맷을 지원하지 않는 경우 대체 콘텐츠를 제공할 수 있습니다.

### 사용법
`MediaCapabilities` API는 `MediaCapabilities.decodingInfo()` 메서드를 사용하여 특정 미디어 포맷의 디코딩 성능을 확인합니다. 이 메서드는 비디오 또는 오디오의 코덱, 해상도, 프레임 속도 등의 정보를 포함하는 객체를 인자로 받습니다.

#### 기본 구문
```javascript
navigator.mediaCapabilities.decodingInfo({
    type: 'media_type', // 'video' 또는 'audio'
    codec: 'codec_string', // 예: 'avc1.42E01E'
    width: width_value, // 해상도 너비
    height: height_value, // 해상도 높이
    framerate: framerate_value, // 프레임 속도
    bitrate: bitrate_value // 비트레이트
}).then(function(result) {
    console.log(result);
}).catch(function(error) {
    console.error(error);
});
```

### 세부 사항
- **type**: 미디어의 유형을 지정합니다. 'video' 또는 'audio' 중 하나입니다.
- **codec**: 사용하려는 미디어 코덱을 문자열로 정의합니다.
- **width**: 비디오의 해상도 너비를 픽셀 단위로 설정합니다.
- **height**: 비디오의 해상도 높이를 픽셀 단위로 설정합니다.
- **framerate**: 비디오의 프레임 속도를 정의합니다.
- **bitrate**: 비디오 또는 오디오의 비트레이트를 설정합니다.

이 메서드는 Promise를 반환하며, 성공적으로 호출되면 `MediaCapabilitiesDecodingInfo` 객체를 반환합니다. 이 객체는 `powerEfficient`, `smooth`, `supported` 등의 속성을 포함합니다.

## 예제
### 비디오 디코딩 정보 확인
```javascript
navigator.mediaCapabilities.decodingInfo({
    type: 'video',
    codec: 'avc1.42E01E',
    width: 1920,
    height: 1080,
    framerate: 30,
    bitrate: 5000000
}).then(function(result) {
    if (result.supported) {
        console.log('비디오 재생이 지원됩니다.');
    } else {
        console.log('비디오 재생이 지원되지 않습니다.');
    }
}).catch(function(error) {
    console.error('오류 발생:', error);
});
```

### 오디오 디코딩 정보 확인
```javascript
navigator.mediaCapabilities.decodingInfo({
    type: 'audio',
    codec: 'mp4a.40.2',
    bitrate: 128000
}).then(function(result) {
    if (result.supported) {
        console.log('오디오 재생이 지원됩니다.');
    } else {
        console.log('오디오 재생이 지원되지 않습니다.');
    }
}).catch(function(error) {
    console.error('오류 발생:', error);
});
```

## 설명
- **지원되지 않는 코덱**: 사용자가 요청한 코덱이 장치에서 지원되지 않는 경우, `supported` 속성은 `false`로 반환됩니다.
- **비트레이트와 해상도**: 비트레이트나 해상도가 장치의 한계를 초과하면 성능 저하가 발생할 수 있습니다. 따라서 적절한 값을 설정하는 것이 중요합니다.
- **Promise 처리**: `decodingInfo()`는 Promise를 반환하므로, 비동기 처리를 위해 `then()` 및 `catch()` 메서드를 사용해야 합니다.

## 한 줄 요약
`MediaCapabilities`는 JavaScript에서 미디어 콘텐츠의 디코딩 성능을 평가하고, 최적의 재생 환경을 제공하는 API입니다.