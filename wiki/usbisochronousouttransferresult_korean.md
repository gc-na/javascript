<!--
Meta Description: # USBIsochronousOutTransferResult: 자바스크립트에서 USB 이소크로너스 전송 결과 ## 개요 USBIsochronousOutTransferResult는 자바스크립트에서 USB 이소크로너스 전송의 결과를 나타내는 객체입니다. 이 객체는 USB ...
Meta Keywords: usb, 이소크로너스, 전송의, 데이터, usbisochronousouttransferresult는
-->

# USBIsochronousOutTransferResult: 자바스크립트에서 USB 이소크로너스 전송 결과

## 개요
USBIsochronousOutTransferResult는 자바스크립트에서 USB 이소크로너스 전송의 결과를 나타내는 객체입니다. 이 객체는 USB 장치와의 이소크로너스 전송에서 발생하는 데이터 전송의 성공 여부와 전송된 데이터의 양을 관리합니다.

## 문서화
USBIsochronousOutTransferResult는 WebUSB API의 일부로, USB 장치와의 이소크로너스 전송을 위해 사용됩니다. 이 객체는 주로 USB 비디오 카메라, 오디오 장치 등에서 실시간 데이터 전송을 수행하는 데 필요합니다.

### 목적
이 객체의 목적은 USB 이소크로너스 전송의 결과를 확인하고, 전송된 데이터의 상태를 관리하는 것입니다.

### 사용법
USBIsochronousOutTransferResult는 다음과 같은 속성을 가지고 있습니다:
- **status**: 전송의 성공 여부를 나타내는 문자열. 주로 "ok" 또는 "error" 값을 가집니다.
- **bytesWritten**: 전송된 바이트 수를 나타내는 정수 값.

### 예제
```javascript
async function sendIsochronousData(device, data) {
    const transferResult = await device.transferOut(1, data);
    
    // USBIsochronousOutTransferResult 객체를 사용하여 전송 결과 확인
    if (transferResult.status === "ok") {
        console.log(`${transferResult.bytesWritten} 바이트가 성공적으로 전송되었습니다.`);
    } else {
        console.error("전송 실패:", transferResult.status);
    }
}
```

## 설명
이 객체를 사용할 때 주의해야 할 점은 다음과 같습니다:
1. **상태 확인**: 전송 후 status가 "ok"인지 확인하여 전송의 성공 여부를 판단해야 합니다.
2. **비동기 처리**: USB 장치와의 데이터 전송은 비동기적으로 처리되므로, await 키워드를 사용해야 합니다.
3. **전송 크기**: 이소크로너스 전송은 일정한 시간 간격으로 데이터를 전송해야 하므로, 데이터 크기와 전송 주기를 적절히 설정해야 합니다.

## 한 줄 요약
USBIsochronousOutTransferResult는 USB 이소크로너스 전송의 결과를 관리하는 객체로, 전송 성공 여부와 전송된 데이터 양을 확인하는 데 사용됩니다.