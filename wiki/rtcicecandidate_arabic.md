<!--
Meta Description: # RTCIceCandidate في JavaScript: فهم واستخدام مرشحات ICE ## ملخص RTCIceCandidate هو كائن في واجهة WebRTC يُستخدم لتمثيل مرشحات الاتصال في بروتوكول ICE...
Meta Keywords: rtcicecandidate, الاتصال, candidate, كائن, المرشحات
-->

# RTCIceCandidate في JavaScript: فهم واستخدام مرشحات ICE

## ملخص
RTCIceCandidate هو كائن في واجهة WebRTC يُستخدم لتمثيل مرشحات الاتصال في بروتوكول ICE (Interactive Connectivity Establishment)، مما يسهل إنشاء اتصالات صوتية ومرئية مباشرة بين المتصفحات.

## الوثائق
يُستخدم كائن RTCIceCandidate في تطبيقات WebRTC لتحديد المرشحات التي يمكن استخدامها في عملية التفاوض على اتصال. تم تصميمه لتوفير تفاصيل حول المرشحات المتاحة، مثل عنوان IP ونوع الاتصال.

### الغرض
يساعد RTCIceCandidate في تسهيل إنشاء الاتصالات من خلال توفير معلومات حول المرشحات، مما يمكّن المتصفحات من تحديد أفضل مسار لتبادل البيانات.

### الاستخدام
لإنشاء كائن RTCIceCandidate، يجب استخدام بناء الجملة التالي:
```javascript
const candidate = new RTCIceCandidate({
  candidate: 'candidate:0 1 UDP 2122260223 192.168.1.1 12345 typ host',
  sdpMid: 'audio',
  sdpMLineIndex: 0,
});
```

### التفاصيل
- **property candidate**: يمثل سلسلة نصية تحتوي على معلومات المرشح، بما في ذلك نوعه وعنوان IP.
- **property sdpMid**: تشير إلى معرف المقطع (media stream) الذي ينتمي إليه المرشح.
- **property sdpMLineIndex**: يشير إلى رقم السطر في كود SDP الذي يتضمن المرشح.

## الأمثلة
### مثال بسيط لإنشاء مرشح ICE
```javascript
const iceCandidate = new RTCIceCandidate({
  candidate: 'candidate:1 1 udp 2122260223 203.0.113.1 54321 typ srflx raddr 192.168.1.1 rport 1234',
  sdpMid: 'video',
  sdpMLineIndex: 1,
});

console.log(iceCandidate);
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود معلومات كافية**: تأكد من أن سلسلة المرشح تحتوي على جميع التفاصيل المطلوبة.
- **تعارضات مع SDPs**: تأكد من أن `sdpMid` و `sdpMLineIndex` تتطابق مع تدفقات الوسائط الموجودة.

### ملاحظات إضافية
- يمكن استخدام RTCIceCandidate مع واجهات أخرى مثل RTCPeerConnection لتسهيل عمليات الاتصال.
- تأكد من معالجة المرشحات بشكل صحيح لتجنب مشكلات الاتصال.

## ملخص بجملة واحدة
RTCIceCandidate هو كائن مهم في WebRTC يُستخدم لتسهيل عمليات الاتصال المباشر من خلال توفير معلومات دقيقة حول مرشحات الاتصال.