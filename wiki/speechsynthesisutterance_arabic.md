<!--
Meta Description: # SpeechSynthesisUtterance في JavaScript: دليلك الشامل ## الملخص تُستخدم فئة `SpeechSynthesisUtterance` في JavaScript لإنشاء نصوص صوتية يمكن للمتصفح ق...
Meta Keywords: utterance, speechsynthesisutterance, speechsynthesis, javascript, تعيين
-->

# SpeechSynthesisUtterance في JavaScript: دليلك الشامل

## الملخص
تُستخدم فئة `SpeechSynthesisUtterance` في JavaScript لإنشاء نصوص صوتية يمكن للمتصفح قراءتها بصوت عالٍ، مما يتيح إمكانية الوصول وتجربة مستخدم أكثر تفاعلية.

## الوثائق
### الغرض
`SpeechSynthesisUtterance` هو كائن يُستخدم لتحديد النص الذي سيتم تحويله إلى كلام باستخدام واجهة برمجة التطبيقات (API) الخاصة بالتوليد الصوتي (Speech Synthesis API). يتيح للمطورين إمكانية إضافة التعليقات الصوتية إلى تطبيقاتهم على الويب، مما يُحسن من تجربة المستخدم.

### الاستخدام
للبدء في استخدام `SpeechSynthesisUtterance`، يجب أولاً إنشاء كائن من الفئة، ثم تعيين النص الخاص بالمحتوى الذي ترغب في تحويله إلى صوت. بعد ذلك، يمكنك استخدام واجهة `speechSynthesis` لتشغيل الصوت. إليك كيفية القيام بذلك:

```javascript
// إنشاء كائن جديد من SpeechSynthesisUtterance
let utterance = new SpeechSynthesisUtterance("مرحبًا بك في عالم البرمجة!");

// تعيين الخصائص
utterance.lang = 'ar-SA'; // تعيين اللغة
utterance.pitch = 1; // تعيين النغمة
utterance.rate = 1; // تعيين سرعة الكلام

// تشغيل الصوت
window.speechSynthesis.speak(utterance);
```

## الأمثلة
### مثال بسيط
```javascript
const utterance = new SpeechSynthesisUtterance("هذا نص تجريبي.");
window.speechSynthesis.speak(utterance);
```

### مثال مع خصائص إضافية
```javascript
const utterance = new SpeechSynthesisUtterance("هذا نص تجريبي مع خصائص مخصصة.");
utterance.pitch = 1.5; // نغمة أعلى
utterance.rate = 0.9; // سرعة أبطأ
utterance.volume = 0.8; // حجم الصوت
window.speechSynthesis.speak(utterance);
```

## الشرح
### النقاط الشائعة
- **التوافق:** تأكد من أن متصفحك يدعم واجهة برمجة التطبيقات للتوليد الصوتي. معظم المتصفحات الحديثة تدعمها، لكن الأداء قد يختلف.
- **اللغات والأصوات:** يمكنك تعيين لغات مختلفة وأصوات مختلفة باستخدام خاصية `voice` المتاحة في كائن `SpeechSynthesis`. يمكنك الحصول على قائمة الأصوات المتاحة باستخدام `speechSynthesis.getVoices()`.
- **إيقاف الصوت:** يمكنك إيقاف الصوت الجاري باستخدام `window.speechSynthesis.cancel()`.

### ملاحظات إضافية
- قد تتطلب بعض المتصفحات إذنًا للوصول إلى الصوت، لذا احرص على اختبار تطبيقك على بيئات مختلفة.
- تأكد من إدارة الموارد بشكل صحيح عن طريق إلغاء أي كائنات `SpeechSynthesisUtterance` غير المستخدمة لتفادي تسرب الذاكرة.

## ملخص جملة واحدة
`SpeechSynthesisUtterance` هو كائن في JavaScript يتيح للمطورين تحويل النصوص إلى كلام باستخدام واجهة برمجة التطبيقات للتوليد الصوتي.