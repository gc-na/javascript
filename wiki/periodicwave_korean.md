<!--
Meta Description: # PeriodicWave: 자바스크립트에서의 주기파 생성 ## 개요 `PeriodicWave`는 Web Audio API의 구성 요소로, 주기적인 파형을 생성하는 데 사용됩니다. 이 객체는 오디오 신호에서 다양한 주기적인 파형을 정의하고 생성하는 데 유용합니다. ##...
Meta Keywords: periodicwave, audiocontext, const, 파형을, real
-->

# PeriodicWave: 자바스크립트에서의 주기파 생성

## 개요
`PeriodicWave`는 Web Audio API의 구성 요소로, 주기적인 파형을 생성하는 데 사용됩니다. 이 객체는 오디오 신호에서 다양한 주기적인 파형을 정의하고 생성하는 데 유용합니다.

## 문서화
### 목적
`PeriodicWave`는 사인파, 사각파, 삼각파 등과 같은 주기적인 파형을 정의하여 오디오 컨텍스트 내에서 사용할 수 있게 해줍니다. 오디오 신호를 합성하거나 효과를 적용할 때 유용하게 사용됩니다.

### 사용법
`PeriodicWave` 객체를 생성하려면 `AudioContext`와 함께 사용해야 합니다. 다음은 `PeriodicWave`를 생성하는 기본적인 방법입니다.

```javascript
const audioContext = new AudioContext();
const real = new Float32Array([0, 1, 0]); // 실수 성분
const imag = new Float32Array([0, 0, 1]); // 허수 성분
const periodicWave = audioContext.createPeriodicWave(real, imag);
```

- **real**: 파형의 실수 성분을 정의하는 Float32Array.
- **imag**: 파형의 허수 성분을 정의하는 Float32Array.

이후, 생성된 `periodicWave`는 `OscillatorNode`와 함께 사용하여 오디오를 재생할 수 있습니다.

### 세부사항
`PeriodicWave`는 다음과 같은 속성과 메소드를 제공합니다:

- **real**: 주기파의 실수 성분을 반환합니다.
- **imag**: 주기파의 허수 성분을 반환합니다.
- **length**: 주기파의 길이를 반환합니다.

이 객체는 FFT(고속 푸리에 변환)를 기반으로 다양한 주파수 성분을 포함할 수 있으며, 사용자가 원하는 형태로 파형을 조정할 수 있습니다.

## 예제
### 기본 사용 예제
다음은 `PeriodicWave`를 사용하여 간단한 사인파를 생성하는 예제입니다.

```javascript
const audioContext = new AudioContext();
const real = new Float32Array([0, 1]); // 사인파의 실수 성분
const imag = new Float32Array([0, 0]); // 사인파의 허수 성분

const periodicWave = audioContext.createPeriodicWave(real, imag);
const oscillator = audioContext.createOscillator();
oscillator.setPeriodicWave(periodicWave);
oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // 440Hz
oscillator.connect(audioContext.destination);
oscillator.start();
```

## 설명
`PeriodicWave`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **값의 범위**: `real`과 `imag` 배열의 값은 특정 범위 내에 있어야 하며, 너무 큰 값은 오디오 왜곡을 초래할 수 있습니다.
2. **메모리 사용**: 복잡한 파형을 생성할 때 메모리 사용량이 증가할 수 있습니다. 필요한 경우에만 복잡한 파형을 생성하는 것이 좋습니다.
3. **오디오 컨텍스트**: `PeriodicWave`는 반드시 활성화된 `AudioContext` 내에서 생성되어야 하며, 그렇지 않으면 오류가 발생할 수 있습니다.

## 한 줄 요약
`PeriodicWave`는 Web Audio API에서 주기적인 오디오 파형을 생성하고 조작하는 데 사용되는 객체입니다.