<!--
Meta Description: # NetworkInformation: 자바스크립트를 통한 네트워크 상태 정보 조회 ## 개요 `NetworkInformation` 인터페이스는 웹 애플리케이션이 네트워크 연결 상태에 대한 정보를 제공받고, 이를 통해 사용자의 경험을 향상시키도록 돕습니다. 이 기능은 ...
Meta Keywords: connection, 네트워크, networkinformation, 사용자의, console
-->

# NetworkInformation: 자바스크립트를 통한 네트워크 상태 정보 조회

## 개요
`NetworkInformation` 인터페이스는 웹 애플리케이션이 네트워크 연결 상태에 대한 정보를 제공받고, 이를 통해 사용자의 경험을 향상시키도록 돕습니다. 이 기능은 사용자의 인터넷 연결 상태를 실시간으로 확인하고, 네트워크 변경 시 알림을 받을 수 있게 해줍니다.

## 문서화
`NetworkInformation` API는 웹 브라우저에서 네트워크 연결에 대한 정보를 제공합니다. 이를 통해 개발자는 사용자의 네트워크 상태를 모니터링하고, 연결 유형(예: Wi-Fi, 4G 등) 및 속도와 같은 추가 정보를 활용할 수 있습니다. 

### 목적
- 사용자의 네트워크 상태를 파악하여 최적의 사용자 경험을 제공.
- 네트워크 변경 시 실시간으로 반응하여 애플리케이션의 동작을 조정.

### 사용법
`NetworkInformation` API는 `navigator.connection` 속성을 통해 접근할 수 있습니다. 이 속성은 `NetworkInformation` 객체를 반환하며, 네트워크 상태에 대한 여러 속성과 메서드를 제공합니다.

### 주요 속성 및 메서드
- `type`: 연결 유형을 나타내는 문자열 (예: "wifi", "cellular")
- `effectiveType`: 사용자의 네트워크 속도를 나타내는 문자열 (예: "2g", "3g", "4g", "5g")
- `downlink`: 다운링크 속도를 나타내는 숫자 (Mbps 단위)
- `rtt`: 왕복 시간(Round Trip Time) (밀리초 단위)
- `saveData`: 사용자가 데이터 절약 모드를 활성화했는지 여부를 나타내는 불리언 값.

## 예제
```javascript
if ('connection' in navigator) {
    const connection = navigator.connection;
    console.log('Connection Type: ', connection.type);
    console.log('Effective Type: ', connection.effectiveType);
    console.log('Downlink Speed: ', connection.downlink, 'Mbps');
    console.log('RTT: ', connection.rtt, 'ms');
    console.log('Save Data Mode: ', connection.saveData);
    
    // 네트워크 상태 변화 리스너
    connection.addEventListener('change', () => {
        console.log('Network connection type has changed to: ', connection.type);
    });
} else {
    console.log('NetworkInformation API is not supported in this browser.');
}
```

## 설명
`NetworkInformation` API를 사용할 때 주의해야 할 점은 다음과 같습니다:
- 모든 웹 브라우저가 이 API를 지원하는 것은 아닙니다. Chrome과 일부 모바일 브라우저에서 주로 지원됩니다. 사용자가 사용하는 브라우저가 이 API를 지원하는지 확인해야 합니다.
- 네트워크 상태가 자주 변할 수 있기 때문에, 이 API를 사용할 때는 적절한 이벤트 리스너를 설정하여 상태 변화를 감지해야 합니다.
- 사용자의 개인 정보 보호를 위해, 이 API는 사용자가 데이터 절약 모드를 활성화했는지 여부만을 알려주며, 구체적인 사용량 정보를 제공하지 않습니다.

## 한 줄 요약
`NetworkInformation` API는 자바스크립트를 통해 사용자의 네트워크 연결 상태를 실시간으로 조회하고, 이를 기반으로 최적의 사용자 경험을 제공할 수 있도록 돕는 인터페이스입니다.