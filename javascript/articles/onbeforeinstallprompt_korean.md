<!--
Meta Description: # onbeforeinstallprompt: JavaScript에서 PWA 설치 프롬프트 제어하기 ## 개요 `onbeforeinstallprompt`는 Progressive Web Apps (PWA)에서 사용되는 이벤트로, 사용자가 앱을 설치할 수 있는 프롬프트를 표...
Meta Keywords: onbeforeinstallprompt, 사용자가, 프롬프트를, installpromptevent, pwa
-->

# onbeforeinstallprompt: JavaScript에서 PWA 설치 프롬프트 제어하기

## 개요
`onbeforeinstallprompt`는 Progressive Web Apps (PWA)에서 사용되는 이벤트로, 사용자가 앱을 설치할 수 있는 프롬프트를 표시하기 전에 발생합니다. 이 이벤트를 활용하면 개발자가 사용자 경험을 개선하고 앱 설치를 최적화할 수 있습니다.

## 문서화
### 목적
`onbeforeinstallprompt` 이벤트는 브라우저가 PWA 설치 프롬프트를 표시하기 전에 발생합니다. 이를 통해 개발자는 사용자가 설치 프롬프트를 수동으로 트리거할 수 있는 시점을 제어할 수 있습니다. 이 기능은 특히 사용자가 앱을 설치하기에 적합한 시점에 맞추어 사용자 경험을 향상시키는 데 유용합니다.

### 사용법
`onbeforeinstallprompt` 이벤트는 `window` 객체에서 발생합니다. 이벤트 리스너를 등록하여 이 이벤트를 감지하고, 기본 프롬프트가 표시되는 것을 방지한 후, 적절한 시점에 사용자에게 설치를 유도할 수 있습니다.

#### 기본 사용법
```javascript
let installPromptEvent;

window.addEventListener('beforeinstallprompt', (event) => {
    // 기본 프롬프트 표시를 방지합니다.
    event.preventDefault();
    // 이벤트를 저장합니다.
    installPromptEvent = event;
    
    // 사용자에게 설치 버튼을 표시합니다.
    showInstallButton();
});

function showInstallButton() {
    const installButton = document.getElementById('install-button');
    installButton.style.display = 'block';

    installButton.addEventListener('click', () => {
        // 저장된 이벤트로 설치 프롬프트를 표시합니다.
        installPromptEvent.prompt();
        installPromptEvent.userChoice.then((choiceResult) => {
            if (choiceResult.outcome === 'accepted') {
                console.log('사용자가 설치를 수락했습니다.');
            } else {
                console.log('사용자가 설치를 거부했습니다.');
            }
            installPromptEvent = null; // 이벤트 리셋
        });
    });
}
```

## 설명
### 일반적인 문제 및 주의사항
- **브라우저 호환성**: `onbeforeinstallprompt` 이벤트는 모든 브라우저에서 지원되지 않습니다. Chrome, Edge, Opera와 같은 Chromium 기반 브라우저에서 주로 사용됩니다. Safari와 Firefox는 아직 이 이벤트를 지원하지 않으므로, 해당 브라우저에서는 대체 사용자 경험을 제공해야 합니다.
  
- **조건부 표시**: 사용자가 앱을 설치할 수 있는 조건이 충족되어야만 이 이벤트가 발생합니다. HTTPS를 사용하고, 서비스 워커가 등록되어 있어야 합니다.

- **이벤트 사용 후 초기화**: 이벤트가 발생한 후에는 `installPromptEvent`를 초기화하여 메모리 누수를 방지하고, 이후 사용자에게 설치 프롬프트를 다시 표시할 수 있도록 해야 합니다.

## 한 줄 요약
`onbeforeinstallprompt`는 PWA 설치 프롬프트를 사용자에게 표시하기 전, 개발자가 이를 제어할 수 있는 이벤트입니다.