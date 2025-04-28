<!--
Meta Description: # PushSubscription: JavaScript에서의 푸시 알림 구독 관리 ## 개요 PushSubscription은 웹 푸시 API의 핵심 구성 요소로, 사용자가 푸시 알림을 수신할 수 있도록 브라우저에서 관리하는 구독 객체입니다. 이 객체는 웹 애플리케이션이...
Meta Keywords: 알림을, service, 사용자가, function, error
-->

# PushSubscription: JavaScript에서의 푸시 알림 구독 관리

## 개요
PushSubscription은 웹 푸시 API의 핵심 구성 요소로, 사용자가 푸시 알림을 수신할 수 있도록 브라우저에서 관리하는 구독 객체입니다. 이 객체는 웹 애플리케이션이 서버에서 푸시 메시지를 전송할 수 있도록 필요한 정보를 제공합니다.

## 문서화
PushSubscription은 웹 푸시 알림을 구현하기 위해 필수적인 객체입니다. 이를 통해 개발자는 사용자의 브라우저에 푸시 알림을 전송할 수 있는 기능을 활성화합니다. 일반적으로 이 객체는 Service Worker와 함께 사용되며, 사용자가 애플리케이션에 대한 알림을 구독할 때 생성됩니다.

### 목적
PushSubscription의 주 목적은 사용자가 푸시 알림을 받을 수 있도록 하고, 이를 통해 실시간 정보를 사용자에게 제공하는 것입니다.

### 사용법
PushSubscription 객체는 일반적으로 다음과 같은 방법으로 생성됩니다:

1. **Service Worker 등록**: 먼저 Service Worker를 등록해야 합니다.
2. **푸시 알림 권한 요청**: 사용자의 권한을 요청합니다.
3. **구독 생성**: 사용자가 권한을 부여하면, `PushManager.subscribe()` 메소드를 호출하여 구독을 생성합니다.

### 세부 사항
- **구독 정보**: PushSubscription 객체는 사용자의 푸시 알림 구독에 대한 정보를 포함합니다. 여기에는 endpoint, keys, expirationTime 등이 포함됩니다.
- **endpoint**: 푸시 메시지를 전송하기 위한 URL입니다.
- **keys**: 암호화에 사용되는 공개키 및 비공개키를 포함합니다.

## 예제
기본적인 PushSubscription 사용 예제는 다음과 같습니다:

```javascript
// Service Worker 등록
if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('/sw.js').then(function(registration) {
        console.log('Service Worker 등록 성공:', registration);
        
        // 푸시 알림 권한 요청
        Notification.requestPermission().then(function(permission) {
            if (permission === 'granted') {
                // 푸시 구독 생성
                registration.pushManager.subscribe({
                    userVisibleOnly: true,
                    applicationServerKey: urlB64ToUint8Array('<YOUR_PUBLIC_VAPID_KEY>')
                }).then(function(subscription) {
                    console.log('푸시 구독 성공:', subscription);
                }).catch(function(error) {
                    console.error('푸시 구독 실패:', error);
                });
            }
        });
    }).catch(function(error) {
        console.error('Service Worker 등록 실패:', error);
    });
}

// Base64 URL을 Uint8 Array로 변환하는 함수
function urlB64ToUint8Array(base64String) {
    const padding = '='.repeat((4 - base64String.length % 4) % 4);
    const base64 = (base64String + padding)
        .replace(/-/g, '+')
        .replace(/_/g, '/');
    
    const rawData = window.atob(base64);
    return new Uint8Array([...rawData].map(char => char.charCodeAt(0)));
}
```

## 설명
PushSubscription을 사용할 때 주의해야 할 사항은 다음과 같습니다:
- **권한 요청**: 사용자가 푸시 알림을 수신하기 위해서는 반드시 권한을 요청해야 하며, 사용자가 이를 거부할 경우 알림을 받을 수 없습니다.
- **브라우저 지원**: 모든 브라우저가 Push API를 지원하는 것은 아니므로, 사용하고자 하는 브라우저의 호환성을 확인해야 합니다.
- **Service Worker**: PushSubscription은 반드시 Service Worker와 함께 작동해야 하며, 이를 통해 백그라운드에서 푸시 메시지를 수신할 수 있습니다.

## 한 줄 요약
PushSubscription은 웹 푸시 알림을 수신하기 위한 구독 정보를 관리하는 JavaScript 객체입니다.