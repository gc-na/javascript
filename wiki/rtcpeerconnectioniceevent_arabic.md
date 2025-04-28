<!--
Meta Description: # RTCPeerConnectionIceEvent في JavaScript: كل ما تحتاج معرفته ## ملخص يعتبر RTCPeerConnectionIceEvent من العناصر الأساسية في واجهة برمجة تطبيقات WebRT...
Meta Keywords: event, ice, candidate, rtcpeerconnectioniceevent, javascript
-->

# RTCPeerConnectionIceEvent في JavaScript: كل ما تحتاج معرفته

## ملخص
يعتبر RTCPeerConnectionIceEvent من العناصر الأساسية في واجهة برمجة تطبيقات WebRTC (الاتصالات في الوقت الحقيقي على الويب) في JavaScript. يُستخدم هذا الحدث للإبلاغ عن تغييرات في حالة اتصال ICE (Interactive Connectivity Establishment) للاتصالات من نظير إلى نظير.

## الوثائق
### الغرض
يهدف RTCPeerConnectionIceEvent إلى توفير معلومات حول حالة ICE للاتصال، مثل تفاصيل المرشحات المستخدمة وتغييرات الحالة. يسمح للمطورين بمتابعة التغييرات في حالة الاتصال وتحسين تجربة المستخدم في تطبيقات الاتصالات.

### الاستخدام
يتم إنشاء RTCPeerConnectionIceEvent عند حدوث تغييرات في حالة ICE. يمكن للمطورين الاستماع لهذا الحدث عبر إضافة معالج أحداث إلى كائن RTCPeerConnection. على سبيل المثال:

```javascript
const peerConnection = new RTCPeerConnection();

peerConnection.addEventListener('icecandidate', (event) => {
    if (event.candidate) {
        console.log('تم العثور على مرشح جديد: ', event.candidate);
    } else {
        console.log('تم الانتهاء من إضافة المرشحات.');
    }
});
```

### التفاصيل
RTCPeerConnectionIceEvent يتضمن الخصائص التالية:
- **candidate**: يمثل كائن مرشح ICE الذي تم إنشاؤه.
- **type**: نوع الحدث (عادةً "icecandidate").

## أمثلة
### مثال 1: الاستماع إلى مرشحات ICE
```javascript
const peerConnection = new RTCPeerConnection();

peerConnection.addEventListener('icecandidate', (event) => {
    if (event.candidate) {
        console.log('مرشح جديد:', event.candidate);
    }
});
```

### مثال 2: التعامل مع نهاية المرشحات
```javascript
peerConnection.addEventListener('icecandidate', (event) => {
    if (!event.candidate) {
        console.log('لا توجد مرشحات أخرى.');
    }
});
```

## التوضيح
### الأخطاء الشائعة
- **عدم التحقق من وجود مرشح**: يجب دائمًا التحقق مما إذا كان `event.candidate` موجودًا قبل استخدامه، حيث قد يكون الحدث بدون مرشح.
- **عدم إدارة الأحداث بشكل صحيح**: عدم إزالة معالجات الأحداث بعد استخدامها يمكن أن يؤدي إلى تسرب الذاكرة.

### ملاحظات إضافية
تأكد من أن الاتصال قد تم إنشاؤه بشكل صحيح قبل التعامل مع أحداث ICE، حيث أن الاستخدام في وقت مبكر قد يؤدي إلى أخطاء. يُفضل اختبار التطبيق في بيئات مختلفة لضمان توافق الاتصال.

## ملخص بجملة واحدة
RTCPeerConnectionIceEvent هو حدث في JavaScript يُستخدم لمتابعة التغييرات في حالة اتصال ICE في تطبيقات WebRTC.