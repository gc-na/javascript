<!--
Meta Description: # حدث RTCDTMFToneChangeEvent في جافا سكريبت: دليل شامل ## ملخص حدث RTCDTMFToneChangeEvent هو جزء من واجهة برمجة التطبيقات WebRTC في جافا سكريبت، ويستخ...
Meta Keywords: dtmf, rtcdtmftonechangeevent, حدث, webrtc, إرسال
-->

# حدث RTCDTMFToneChangeEvent في جافا سكريبت: دليل شامل

## ملخص
حدث RTCDTMFToneChangeEvent هو جزء من واجهة برمجة التطبيقات WebRTC في جافا سكريبت، ويستخدم للإبلاغ عن تغييرات نغمات DTMF (Dual-Tone Multi-Frequency) في اتصالات الصوت.

## الوثائق
### الغرض
يهدف حدث RTCDTMFToneChangeEvent إلى توفير معلومات حول النغمات التي تم إرسالها أو تلقيها عبر قناة WebRTC. يساعد هذا الحدث المطورين على التعامل مع تفاعلات DTMF مثل إدخال الأرقام أثناء المكالمات الهاتفية.

### الاستخدام
يمكن استخدام RTCDTMFToneChangeEvent في سياقات مختلفة حيث يتم استخدام WebRTC لإجراء مكالمات صوتية. يتضمن ذلك تطبيقات الاتصال المباشر وتطبيقات مؤتمرات الفيديو.

### التفاصيل
يتم إنشاء حدث RTCDTMFToneChangeEvent عندما يتم إرسال نغمة DTMF. يتضمن الحدث خاصية `tone` التي تحتوي على النغمة التي تم إرسالها. يمكن للمطورين الاشتراك في هذا الحدث للاستجابة لتغييرات النغمة.

## الأمثلة
### مثال أساسي
```javascript
// إنشاء كائن RTCPeerConnection
const peerConnection = new RTCPeerConnection();

// الاستماع لحدث RTCDTMFToneChangeEvent
peerConnection.addEventListener('dtmfToneChange', (event) => {
    console.log('تم إرسال نغمة DTMF:', event.tone);
});

// إرسال نغمة DTMF
const sender = peerConnection.getSenders()[0];
sender.sendDtmf('5');
```

### مثال آخر
```javascript
// إعداد حدث DTMF
const dtmfSender = peerConnection.createDTMFSender(senderTrack);

// الاستماع للحدث
dtmfSender.addEventListener('dtmfToneChange', (event) => {
    alert(`تم إرسال النغمة: ${event.tone}`);
});

// إرسال نغمة DTMF
dtmfSender.insertDTMF('1', 100, 100);
```

## الشرح
### المشكلات الشائعة
- **فشل الإرسال**: تأكد من أن قناة WebRTC مفتوحة وتعمل بشكل صحيح قبل إرسال نغمات DTMF.
- **التعامل مع الأحداث**: تأكد من وجود مستمعين للأحداث بشكل صحيح لتجنب فقدان إشعارات النغمة.
- **التوافق**: تأكد من أن المتصفح أو البيئة المدعومة تدعم واجهة WebRTC وRTCDTMFToneChangeEvent.

### ملاحظات إضافية
- تأكد من استدعاء `sendDtmf` أو `insertDTMF` في السياق الصحيح، حيث يجب أن يكون لديك اتصال نشط.
- يمكن أن تكون هناك قيود على عدد النغمات التي يمكن إرسالها في فترة زمنية محددة، لذا يجب الانتباه لذلك عند تصميم التطبيق.

## ملخص جملة واحدة
حدث RTCDTMFToneChangeEvent في جافا سكريبت يُستخدم للإبلاغ عن تغييرات نغمات DTMF في اتصالات WebRTC.