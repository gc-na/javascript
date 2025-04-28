<!--
Meta Description: # USBIsochronousInTransferResult: JavaScript에서의 USB 이소크로너스 전송 결과 ## 개요 USBIsochronousInTransferResult는 JavaScript에서 USB 장치와의 이소크로너스 전송을 처리하기 위한 결과 객체입...
Meta Keywords: usb, result, 데이터, 이소크로너스, status
-->

# USBIsochronousInTransferResult: JavaScript에서의 USB 이소크로너스 전송 결과

## 개요
USBIsochronousInTransferResult는 JavaScript에서 USB 장치와의 이소크로너스 전송을 처리하기 위한 결과 객체입니다. 이 객체는 USB 장치로부터 데이터를 일정한 속도로 수신할 때의 결과를 나타냅니다.

## 문서화
### 목적
USBIsochronousInTransferResult는 USB 이소크로너스 전송의 결과를 캡슐화하여, 개발자가 데이터 전송의 성공 여부 및 수신된 데이터의 상태를 쉽게 확인할 수 있도록 돕습니다.

### 사용법
USBIsochronousInTransferResult 객체는 일반적으로 `USBInTransfer` 메서드와 함께 사용됩니다. 이 메서드는 USB 장치로부터 이소크로너스 방식으로 데이터를 수신할 때 호출됩니다.

```javascript
async function transferData(device) {
    const result = await device.transferIn(endpointNumber, length);
    // USBIsochronousInTransferResult 객체 사용
    if (result.status === 'ok') {
        console.log('데이터 수신 성공:', result.data);
    } else {
        console.error('데이터 수신 실패:', result.status);
    }
}
```

### 세부사항
- **속성**
  - `data`: 수신된 데이터의 바이트 배열.
  - `status`: 전송의 성공 여부를 나타내는 문자열 ('ok' 또는 'error').

- **메서드**
  - USBIsochronousInTransferResult는 주로 USBInTransfer 메서드의 반환값으로 사용되며, 이 메서드는 Promise를 반환합니다.

## 예제
### 기본 사용 예제
```javascript
const usbDevice = await navigator.usb.requestDevice({ filters: [{ vendorId: 0x1234 }] });
await usbDevice.open();
const result = await usbDevice.transferIn(1, 64);

if (result.status === 'ok') {
    console.log('데이터:', new Uint8Array(result.data.buffer));
} else {
    console.error('오류:', result.status);
}
```

## 설명
이소크로너스 전송 방식은 실시간 데이터 전송에 적합하지만, 전송 속도가 일정해야 하므로 몇 가지 주의사항이 있습니다. 
- **전송 속도**: USB 장치의 대역폭에 따라 전송 속도가 제한될 수 있습니다.
- **에러 처리**: 전송 도중 발생할 수 있는 오류에 대한 처리를 반드시 구현해야 합니다. 데이터 전송이 실패할 경우, 적절한 에러 메시지를 로그에 출력하는 것이 좋습니다.

## 한 줄 요약
USBIsochronousInTransferResult는 USB 이소크로너스 전송의 결과를 나타내는 객체로, 데이터 수신의 성공 여부 및 수신된 데이터를 제공합니다.