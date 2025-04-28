<!--
Meta Description: # GravitySensor: 자바스크립트에서 중력 센서 활용하기 ## 개요 GravitySensor는 웹 애플리케이션에서 장치의 중력 센서를 활용하여 기기의 기울기 및 방향을 측정할 수 있도록 하는 JavaScript API입니다. 이 기능은 특히 모바일 디바이스에서...
Meta Keywords: sensor, gravitysensor, javascript, 장치의, 합니다
-->

# GravitySensor: 자바스크립트에서 중력 센서 활용하기

## 개요
GravitySensor는 웹 애플리케이션에서 장치의 중력 센서를 활용하여 기기의 기울기 및 방향을 측정할 수 있도록 하는 JavaScript API입니다. 이 기능은 특히 모바일 디바이스에서 유용하게 사용되며, 다양한 사용자 경험을 향상시키는 데 도움을 줍니다.

## 문서
### 목적
GravitySensor API는 물리적 환경을 감지하고, 장치의 기울기 및 방향 정보를 실시간으로 제공합니다. 이를 통해 게임, 증강 현실, 사용자 인터페이스 등 다양한 분야에서 활용할 수 있습니다.

### 사용법
GravitySensor API를 사용하기 위해서는 다음 단계를 따라야 합니다:

1. **GravitySensor 객체 생성**
   ```javascript
   const sensor = new GravitySensor();
   ```

2. **데이터 수신을 위한 이벤트 리스너 등록**
   ```javascript
   sensor.addEventListener('reading', () => {
       console.log(`X: ${sensor.x}, Y: ${sensor.y}, Z: ${sensor.z}`);
   });
   ```

3. **센서 시작**
   ```javascript
   sensor.start();
   ```

4. **센서 중지**
   ```javascript
   sensor.stop();
   ```

### 세부정보
- **속성**
  - `x`: 장치의 X축 중력 값.
  - `y`: 장치의 Y축 중력 값.
  - `z`: 장치의 Z축 중력 값.

- **이벤트**
  - `reading`: 센서 데이터가 업데이트될 때 발생하는 이벤트.

- **예외 처리**
  - `NotSupportedError`: GravitySensor가 지원되지 않는 경우 발생합니다.
  - `SecurityError`: 보안 상의 이유로 센서를 사용할 수 없는 경우 발생합니다.

## 예제
### 기본 사용 예제
```javascript
if ('GravitySensor' in window) {
    const sensor = new GravitySensor();

    sensor.addEventListener('reading', () => {
        console.log(`X: ${sensor.x}, Y: ${sensor.y}, Z: ${sensor.z}`);
    });

    sensor.start();
} else {
    console.warn("GravitySensor가 지원되지 않습니다.");
}
```

## 설명
- **일반적인 오류 및 주의사항**
  - GravitySensor API는 모든 브라우저에서 지원되지 않습니다. 따라서 사용하기 전에 `if ('GravitySensor' in window)`를 통해 지원 여부를 확인해야 합니다.
  - 모바일 디바이스에서만 유용하며, 데스크탑 환경에서는 사용이 제한적일 수 있습니다.
  - 사용자가 브라우저에서 위치 정보 또는 센서 접근 권한을 허용해야 합니다.

- **추가 노트**
  - GravitySensor는 실시간 데이터를 제공하므로, 성능에 영향을 미칠 수 있습니다. 필요하지 않을 때는 `sensor.stop()`을 호출하여 센서를 중지하는 것이 좋습니다.
  - 개발 중에 디바이스에서 센서 정보를 확인할 수 없을 경우, 다른 디바이스에서 테스트해 보아야 합니다.

## 한 줄 요약
GravitySensor는 JavaScript를 사용하여 사용자의 장치 기울기와 방향을 감지할 수 있는 강력한 API입니다.