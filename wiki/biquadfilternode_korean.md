<!--
Meta Description: # BiquadFilterNode: 자바스크립트에서의 오디오 필터링 ## 개요 BiquadFilterNode는 Web Audio API의 일부분으로, 간단한 필터링 작업을 수행하기 위해 사용되는 노드입니다. 이 노드는 주로 오디오 신호의 주파수를 조정하여 특정 주파수를...
Meta Keywords: biquadfilter, audiocontext, oscillator, 오디오, const
-->

# BiquadFilterNode: 자바스크립트에서의 오디오 필터링 

## 개요
BiquadFilterNode는 Web Audio API의 일부분으로, 간단한 필터링 작업을 수행하기 위해 사용되는 노드입니다. 이 노드는 주로 오디오 신호의 주파수를 조정하여 특정 주파수를 강조하거나 감소시키기 위해 사용됩니다.

## 문서화
BiquadFilterNode는 다양한 유형의 필터(저역 통과, 고역 통과, 대역 통과, 대역 저지 등)를 지원하며, 오디오 처리에서 널리 사용됩니다. 이 노드는 AudioContext의 createBiquadFilter 메서드를 통해 생성되며, 필터의 유형, 주파수, 품질 팩터(Q) 및 이득을 설정할 수 있습니다.

### 사용법
1. **생성**: BiquadFilterNode는 AudioContext의 createBiquadFilter 메서드를 통해 생성합니다.
   ```javascript
   const audioContext = new AudioContext();
   const biquadFilter = audioContext.createBiquadFilter();
   ```
   
2. **필터 설정**: 필터의 유형과 매개변수를 설정합니다.
   ```javascript
   biquadFilter.type = 'lowpass'; // 필터 유형 설정 (예: lowpass, highpass 등)
   biquadFilter.frequency.setValueAtTime(440, audioContext.currentTime); // 주파수 설정
   biquadFilter.Q.setValueAtTime(1, audioContext.currentTime); // 품질 팩터 설정
   biquadFilter.gain.setValueAtTime(0, audioContext.currentTime); // 이득 설정
   ```

3. **노드 연결**: 필터 노드를 오디오 소스와 연결합니다.
   ```javascript
   const oscillator = audioContext.createOscillator();
   oscillator.connect(biquadFilter);
   biquadFilter.connect(audioContext.destination);
   oscillator.start();
   ```

## 예제
### 기본 사용 예제
```javascript
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const biquadFilter = audioCtx.createBiquadFilter();
const oscillator = audioCtx.createOscillator();

biquadFilter.type = 'lowpass';
biquadFilter.frequency.setValueAtTime(1000, audioCtx.currentTime);
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, audioCtx.currentTime);

oscillator.connect(biquadFilter);
biquadFilter.connect(audioCtx.destination);
oscillator.start();
```

## 설명
BiquadFilterNode를 사용할 때 주의해야 할 점은 설정한 주파수와 Q 값이 오디오 신호에 미치는 영향을 이해하는 것입니다. 잘못된 설정은 원치 않는 결과를 초래할 수 있습니다. 또한, 필터의 효과는 신호의 입력에 따라 달라질 수 있으므로, 다양한 주파수와 이득 값으로 실험하는 것이 좋습니다.

## 한줄 요약
BiquadFilterNode는 Web Audio API에서 오디오 신호의 특정 주파수를 필터링하기 위해 사용되는 유용한 노드입니다.