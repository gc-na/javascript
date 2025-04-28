<!--
Meta Description: # TimeRanges: 자바스크립트에서의 시간 범위 객체 ## 개요 `TimeRanges`는 HTMLMediaElement 인터페이스의 속성으로, 미디어 요소에서 재생 가능한 시간 범위를 정의합니다. 이 객체는 비디오 및 오디오에서 부분 재생을 관리할 때 유용합니다....
Meta Keywords: timeranges, video, 객체는, 미디어, 가능한
-->

# TimeRanges: 자바스크립트에서의 시간 범위 객체

## 개요
`TimeRanges`는 HTMLMediaElement 인터페이스의 속성으로, 미디어 요소에서 재생 가능한 시간 범위를 정의합니다. 이 객체는 비디오 및 오디오에서 부분 재생을 관리할 때 유용합니다.

## 문서화
`TimeRanges` 객체는 여러 개의 시간 범위를 나타내며, 각 범위는 시작 시간과 끝 시간으로 구성됩니다. 이 객체는 주로 `<video>` 및 `<audio>` 요소와 함께 사용되며, 특정 구간에서의 재생 가능 여부를 확인하는 데에 사용됩니다.

### 목적
`TimeRanges`의 주요 목적은 미디어의 재생 가능한 특정 구간을 확인하고, 이러한 구간을 기반으로 사용자 인터페이스를 최적화하는 것입니다.

### 사용법
`TimeRanges` 객체는 기본적으로 다음과 같은 속성과 메서드를 가집니다:
- `length`: 정의된 시간 범위의 수를 반환합니다.
- `start(index)`: 지정된 인덱스의 시작 시간을 반환합니다.
- `end(index)`: 지정된 인덱스의 끝 시간을 반환합니다.

### 예제
```javascript
// 비디오 요소 가져오기
const video = document.querySelector('video');

// 메타데이터가 로드된 후 TimeRanges 객체 접근
video.addEventListener('loadedmetadata', () => {
    const timeRanges = video.seekable; // 또는 video.buffered

    for (let i = 0; i < timeRanges.length; i++) {
        console.log(`범위 ${i + 1}: 시작 - ${timeRanges.start(i)}, 끝 - ${timeRanges.end(i)}`);
    }
});
```

## 설명
`TimeRanges` 객체를 사용할 때 주의해야 할 몇 가지 점이 있습니다:

1. **비어 있는 TimeRanges**: 경우에 따라 `TimeRanges` 객체가 비어 있을 수 있습니다. 이는 미디어가 아직 로드되지 않았거나, 메타데이터를 불러오지 않은 경우에 발생할 수 있습니다. 이럴 때는 `length` 속성을 확인하여 유효성을 체크해야 합니다.

2. **인덱스 접근**: `start()` 및 `end()` 메서드는 유효한 인덱스에만 접근해야 합니다. 유효하지 않은 인덱스에 접근하면 `IndexSizeError`가 발생합니다.

3. **상황에 따른 사용**: 일반적으로 `buffered`, `seekable`, `played` 속성과 함께 사용되며, 각각의 속성은 다른 미디어 상태를 나타냅니다. 이들 각 속성의 사용 목적과 기능을 이해하는 것이 중요합니다.

## 한 줄 요약
`TimeRanges`는 HTMLMediaElement의 속성으로, 미디어 재생 가능한 시간 범위를 정의하고 관리하는 데 사용됩니다.