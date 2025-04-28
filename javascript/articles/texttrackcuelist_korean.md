<!--
Meta Description: # TextTrackCueList: 자바스크립트에서의 텍스트 트랙 큐 리스트 ## 개요 `TextTrackCueList`는 HTML5 비디오 및 오디오 요소에서 사용되는 텍스트 트랙의 큐를 관리하는 객체입니다. 이 객체는 자막, 설명, 챕터 등과 같은 텍스트 트랙의 큐...
Meta Keywords: 텍스트, cues, texttrackcuelist, video, 트랙의
-->

# TextTrackCueList: 자바스크립트에서의 텍스트 트랙 큐 리스트

## 개요
`TextTrackCueList`는 HTML5 비디오 및 오디오 요소에서 사용되는 텍스트 트랙의 큐를 관리하는 객체입니다. 이 객체는 자막, 설명, 챕터 등과 같은 텍스트 트랙의 큐를 배열처럼 다룰 수 있게 해줍니다.

## 문서화
`TextTrackCueList`는 `TextTrack`의 `cues` 프로퍼티를 통해 접근할 수 있으며, 여러 개의 `TextTrackCue` 객체를 포함하는 리스트입니다. 이 리스트는 비디오의 특정 시간에 표시할 텍스트 정보를 제공합니다.

### 목적
- 텍스트 트랙의 큐를 관리하고, 각 큐의 정보에 접근할 수 있도록 합니다.
  
### 사용법
`TextTrackCueList`는 다음과 같은 특성을 가집니다:
- `length`: 큐의 개수를 반환합니다.
- `item(index)`: 주어진 인덱스에 해당하는 `TextTrackCue` 객체를 반환합니다.

### 상세 내용
`TextTrackCueList`는 일반적으로 다음과 같이 사용됩니다:
1. HTML 비디오 요소에서 텍스트 트랙을 생성합니다.
2. `TextTrack` 객체를 통해 `cues` 프로퍼티에 접근하여 `TextTrackCueList`를 얻습니다.

```javascript
const video = document.querySelector('video');
const textTracks = video.textTracks;

if (textTracks.length > 0) {
    const cues = textTracks[0].cues; // 첫 번째 텍스트 트랙의 큐 리스트
    console.log(cues.length); // 큐의 개수 출력
}
```

## 예제
```javascript
// HTML 비디오 요소에 텍스트 트랙 추가
const video = document.createElement('video');
const track = document.createElement('track');
track.kind = 'subtitles';
track.src = 'subtitles.vtt';
video.appendChild(track);

// 비디오 요소에서 텍스트 트랙의 큐 접근
video.addEventListener('loadedmetadata', () => {
    const cues = video.textTracks[0].cues;

    for (let i = 0; i < cues.length; i++) {
        console.log(cues.item(i).text); // 각 큐의 텍스트 출력
    }
});
```

## 설명
`TextTrackCueList`를 사용할 때 주의해야 할 점은 다음과 같습니다:
- `TextTrack` 객체가 로드되지 않은 상태에서 `cues` 프로퍼티에 접근하면 빈 리스트가 반환될 수 있습니다. 따라서, 메타데이터가 로드된 후에 접근해야 합니다.
- `TextTrackCue`의 속성을 정확히 이해하고 사용해야 합니다. 각 큐는 시작 시간과 종료 시간을 가지며, 이 범위 내에서만 표시됩니다.

## 한 줄 요약
`TextTrackCueList`는 자바스크립트에서 텍스트 트랙의 큐를 관리하고 접근할 수 있게 해주는 객체입니다.