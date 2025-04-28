<!--
Meta Description: # JavaScript의 Serial API: 직렬 통신의 이해와 활용 ## 개요 JavaScript의 Serial API는 브라우저와 하드웨어 간의 직렬 통신을 가능하게 하는 기능입니다. 이 API는 웹 애플리케이션이 USB 장치와 같은 하드웨어와 직접 연결하여 데이...
Meta Keywords: port, serial, api는, const, await
-->

# JavaScript의 Serial API: 직렬 통신의 이해와 활용

## 개요
JavaScript의 Serial API는 브라우저와 하드웨어 간의 직렬 통신을 가능하게 하는 기능입니다. 이 API는 웹 애플리케이션이 USB 장치와 같은 하드웨어와 직접 연결하여 데이터를 송수신할 수 있도록 지원합니다.

## 문서화

### 목적
Serial API는 웹 애플리케이션이 다양한 직렬 장치와 통신할 수 있도록 설계되었습니다. 이를 통해 개발자는 IoT 기기, 센서, 또는 다른 USB 기반 장치와의 상호작용을 쉽게 구현할 수 있습니다.

### 사용법
Serial API를 사용하기 위해서는 먼저 사용자의 허가를 받아야 합니다. 기본적인 사용 단계는 다음과 같습니다:

1. **장치 요청**: `navigator.serial.requestPort()`를 호출하여 사용자가 연결할 장치를 선택하도록 요청합니다.
2. **포트 열기**: 선택된 포트를 열기 위해 `port.open()` 메서드를 사용합니다.
3. **데이터 송수신**: `port.readable` 및 `port.writable` 스트림을 사용하여 데이터를 읽고 쓸 수 있습니다.
4. **포트 닫기**: 작업이 끝나면 `port.close()`를 호출하여 포트를 닫습니다.

### 세부 사항
- **브라우저 지원**: Serial API는 현재 Chrome 및 Edge와 같은 Chromium 기반 브라우저에서 지원됩니다.
- **보안**: 이 API는 HTTPS에 의해 보호되는 환경에서만 작동합니다.
- **데이터 형식**: 데이터 송수신 시 Uint8Array 형식이 사용됩니다.

## 예제

### 기본 사용 예제
```javascript
async function connectToSerial() {
    const port = await navigator.serial.requestPort();
    await port.open({ baudRate: 9600 });

    const writer = port.writable.getWriter();
    const data = new Uint8Array([0x01, 0x02, 0x03]);
    await writer.write(data);
    writer.releaseLock();

    const reader = port.readable.getReader();
    const { value } = await reader.read();
    console.log(value);
    reader.releaseLock();

    await port.close();
}
```

## 설명
- **권한 요청**: 사용자가 장치를 선택할 수 있는 팝업 창이 나타나며, 이 단계에서 사용자가 장치를 승인해야 합니다.
- **데이터 형식에 유의**: 송수신하는 데이터는 반드시 Uint8Array 형식이어야 하며, 다른 형식은 오류를 발생시킬 수 있습니다.
- **스트림 관리**: 포트를 열고 닫을 때는 항상 스트림을 적절히 관리해야 하며, 리소스 누수를 방지해야 합니다.

## 한 줄 요약
JavaScript의 Serial API는 브라우저에서 하드웨어와의 직렬 통신을 가능하게 하여, IoT 기기와의 상호작용을 쉽게 만들어주는 기능입니다.