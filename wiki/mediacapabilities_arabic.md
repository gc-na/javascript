<!--
Meta Description: # MediaCapabilities في JavaScript: فهم وتحليل قدرات الوسائط ## ملخص تُعتبر MediaCapabilities واجهة برمجة تطبيقات (API) في JavaScript تُستخدم لتحديد قد...
Meta Keywords: mediacapabilities, الوسائط, مثل, javascript, على
-->

# MediaCapabilities في JavaScript: فهم وتحليل قدرات الوسائط

## ملخص
تُعتبر MediaCapabilities واجهة برمجة تطبيقات (API) في JavaScript تُستخدم لتحديد قدرات تشغيل الوسائط مثل الفيديو والصوت في المتصفح. تساعد هذه الواجهة المطورين على معرفة ما إذا كان الجهاز يدعم تنسيق وسائط معين ومدى كفاءته في تشغيله.

## الوثائق
### الغرض
تُستخدم واجهة MediaCapabilities لتقديم معلومات حول دعم الوسائط، مما يمكّن المطورين من تحسين تجربة المستخدم من خلال اختيار تنسيقات الوسائط الأكثر توافقًا مع الأجهزة المختلفة.

### الاستخدام
يمكن استخدام MediaCapabilities من خلال استدعاء الدالة `MediaCapabilities.decodingInfo()`. هذه الدالة تأخذ كائنًا كوسيط يحتوي على معلومات حول نوع الوسائط، بما في ذلك التنسيق، ودرجة الدقة، ومعدل البت.

#### التركيب
```javascript
navigator.mediaCapabilities.decodingInfo(constraints).then(function(result) {
    // التعامل مع النتيجة
}).catch(function(error) {
    // معالجة الخطأ
});
```

### التفاصيل
- **المحددات**: يجب أن يتضمن الكائن الذي يتم تمريره إلى `decodingInfo` المعلومات التالية:
  - `type`: نوع الوسائط (مثل "video/mp4" أو "audio/webm").
  - `video`: كائن يتضمن معلومات الفيديو (مثل `width`, `height`, `framerate`, `duration`, و`bitrate`).
  - `audio`: كائن يتضمن معلومات الصوت (مثل `channels`, `bitrate`, و`sampleRate`).

- **النتائج**: تعيد الدالة كائنًا يحتوي على خصائص مثل:
  - `supported`: تشير إلى ما إذا كان التنسيق مدعومًا.
  - `smooth`: تشير إلى ما إذا كان تشغيل الوسائط سيكون سلسًا.
  - `powerEfficient`: تشير إلى كفاءة الطاقة خلال التشغيل.

## أمثلة
### مثال بسيط للتحقق من دعم فيديو MP4
```javascript
const constraints = {
    type: 'video/mp4',
    video: {
        width: 1280,
        height: 720,
        bitrate: 1000000,
        framerate: 30
    }
};

navigator.mediaCapabilities.decodingInfo(constraints).then(function(result) {
    if (result.supported) {
        console.log("التنسيق مدعوم.");
    } else {
        console.log("التنسيق غير مدعوم.");
    }
}).catch(function(error) {
    console.error("حدث خطأ: ", error);
});
```

## الشرح
- **التعامل مع النتائج**: يجب على المطورين دائمًا التحقق من النتائج قبل اتخاذ أي إجراء، مثل تشغيل الفيديو أو الصوت، لضمان تجربة مستخدم سلسة.
- **الدعم المتنوع**: ليس جميع المتصفحات تدعم واجهة MediaCapabilities، لذا يجب اختبار الكود في بيئات مختلفة.
- **الأداء**: قد تتأثر نتائج `decodingInfo` بعوامل مثل قوة المعالجة والذاكرة المتاحة.

## ملخص من جملة واحدة
تعتبر واجهة MediaCapabilities في JavaScript أداة فعالة لتحديد قدرات تشغيل الوسائط على الأجهزة المختلفة، مما يحسن من تجربة المستخدم.