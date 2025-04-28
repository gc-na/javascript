<!--
Meta Description: # CSPViolationReportBody: JavaScript의 콘텐츠 보안 정책 위반 보고서 본문 ## 개요 CSPViolationReportBody는 JavaScript에서 콘텐츠 보안 정책(CSP) 위반 보고서를 처리하는 데 사용되는 객체입니다. CSP는 웹 ...
Meta Keywords: csp, cspviolationreportbody는, report, uri, 보고서를
-->

# CSPViolationReportBody: JavaScript의 콘텐츠 보안 정책 위반 보고서 본문

## 개요
CSPViolationReportBody는 JavaScript에서 콘텐츠 보안 정책(CSP) 위반 보고서를 처리하는 데 사용되는 객체입니다. CSP는 웹 애플리케이션의 보안을 강화하기 위해 특정 리소스의 로딩이나 실행을 제한하는 정책으로, CSPViolationReportBody는 이러한 위반 사항에 대한 정보를 제공합니다.

## 문서화
### 목적
CSPViolationReportBody는 CSP 위반이 발생했을 때 브라우저가 보내는 보고서의 본문을 정의합니다. 이 객체는 웹 개발자가 CSP 설정을 점검하고 보안 취약점을 찾아내는 데 유용합니다.

### 사용법
CSPViolationReportBody는 일반적으로 `report-uri` 또는 `report-to` 지시어를 사용하여 지정한 URL로 전송됩니다. 해당 URL에서 수신된 보고서는 JSON 형식으로 제공되며, 다양한 속성을 포함합니다.

### 세부 사항
- **이벤트**: CSPViolationReportBody는 CSP 위반이 발생했을 때 자동으로 생성됩니다.
- **속성**: 주요 속성으로는 `document-uri`, `referrer`, `violated-directive`, `effective-directive`, `original-policy`, `blocked-uri` 등이 있습니다.

## 예제
```javascript
// CSPViolationReportBody의 예시
const report = {
  "document-uri": "https://example.com",
  "referrer": "https://referrer.com",
  "violated-directive": "script-src 'self'",
  "effective-directive": "script-src",
  "original-policy": "default-src 'self'; script-src 'self'",
  "blocked-uri": "https://malicious.com/script.js"
};

// 보고서를 서버에 전송
fetch('https://your-report-endpoint.com/report', {
  method: 'POST',
  body: JSON.stringify(report),
  headers: {
    'Content-Type': 'application/json'
  }
});
```

## 설명
CSPViolationReportBody를 사용할 때 주의해야 할 점은 다음과 같습니다:
- **위반 사항의 정확성**: 보고된 위반 사항이 실제로 의도된 것인지 확인해야 합니다. 잘못된 CSP 설정이 원인일 수 있습니다.
- **보고서 수신 처리**: 서버에서 CSP 위반 보고서를 제대로 수신하고 처리하는 로직을 구현해야 합니다.
- **보안 고려사항**: CSP 위반 보고서는 민감한 정보를 포함할 수 있으므로, 적절한 보안 조치를 취해야 합니다.

## 한 줄 요약
CSPViolationReportBody는 JavaScript에서 CSP 위반 보고서를 정의하고 처리하는 데 사용되는 객체입니다.