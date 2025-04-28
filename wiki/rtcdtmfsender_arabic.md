<!--
Meta Description: # RTCDTMFSender في JavaScript: كيفية استخدامه لإرسال نغمات DTMF في WebRTC ## ملخص RTCDTMFSender هو واجهة برمجة تطبيقات (API) في WebRTC تُستخدم لإرسال ...
Meta Keywords: نغمات, dtmf, rtcdtmfsender, إرسال, لإرسال
-->

# RTCDTMFSender في JavaScript: كيفية استخدامه لإرسال نغمات DTMF في WebRTC

## ملخص
RTCDTMFSender هو واجهة برمجة تطبيقات (API) في WebRTC تُستخدم لإرسال نغمات DTMF (Dual-Tone Multi-Frequency) عبر اتصال الصوت. يتيح للمطورين القدرة على إرسال نغمات مثل تلك المستخدمة في لوحات المفاتيح الهاتفية.

## الوثائق
### الغرض
يهدف RTCDTMFSender إلى تمكين نقل نغمات DTMF بشكل موثوق أثناء مكالمات الصوت أو الفيديو في تطبيقات WebRTC. يعتبر إرسال نغمات DTMF ضروريًا في العديد من التطبيقات مثل أنظمة الرد الآلي والاتصالات الصوتية.

### الاستخدام
لإنشاء مثيل من RTCDTMFSender، يجب أن يكون لديك كائن `RTCPeerConnection` مرتبط بالاتصال الصوتي. يمكنك بعد ذلك استخدام هذه الواجهة لإرسال نغمات DTMF.

#### إنشاء RTCDTMFSender
```javascript
const pc = new RTCPeerConnection();
const dtmfSender = pc.createDTMFSender(track);
```
### التفاصيل
- **الخصائص**:
  - `track`: يجب أن يكون كائن `MediaStreamTrack` يمثل تدفق الصوت الذي تريد إرسال نغمات DTMF عبره.
  
- **الطرق**:
  - `insertDTMF(tones, duration, interToneGap)`: تُستخدم لإرسال نغمات DTMF. 
    - `tones`: سلسلة من النغمات (مثل "123#").
    - `duration`: مدة كل نغمة بالمللي ثانية (افتراضي 100 مللي ثانية).
    - `interToneGap`: الفاصل الزمني بين النغمات بالمللي ثانية (افتراضي 70 مللي ثانية).

## أمثلة
### مثال بسيط لإرسال نغمات DTMF
```javascript
const pc = new RTCPeerConnection();
const audioTrack = ...; // كائن MediaStreamTrack
const dtmfSender = pc.createDTMFSender(audioTrack);

// إرسال نغمات DTMF
dtmfSender.insertDTMF("123#");
```

### استخدام مع خيارات مخصصة
```javascript
dtmfSender.insertDTMF("456", 150, 100);
```

## الشرح
### الأخطاء الشائعة
- **فشل في إرسال النغمات**: تأكد من أن `RTCPeerConnection` في حالة الاتصال وأن `MediaStreamTrack` صالح.
- **إعدادات غير صحيحة**: تأكد من ضبط `duration` و `interToneGap` بشكل مناسب لتجنب مشاكل في الإرسال.

### ملاحظات إضافية
- RTCDTMFSender مدعوم في معظم المتصفحات الحديثة، ولكن يُفضل التحقق من التوافق قبل استخدامه في تطبيقاتك.
- تأكد من اختبار الإرسال في بيئات مختلفة لضمان موثوقية الاتصال.

## ملخص بجملة واحدة
RTCDTMFSender هو واجهة في WebRTC تمكن المطورين من إرسال نغمات DTMF عبر اتصالات الصوت بسهولة وموثوقية.