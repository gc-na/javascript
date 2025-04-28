<!--
Meta Description: # PerformanceScriptTiming في JavaScript: تحسين الأداء وتحليل التوقيت ## الملخص PerformanceScriptTiming هو واجهة في JavaScript تستخدم لجمع معلومات دقيق...
Meta Keywords: script, تحميل, performance, performancescripttiming, javascript
-->

# PerformanceScriptTiming في JavaScript: تحسين الأداء وتحليل التوقيت

## الملخص
PerformanceScriptTiming هو واجهة في JavaScript تستخدم لجمع معلومات دقيقة حول أداء تحميل النصوص البرمجية (JavaScript) في صفحات الويب. تساعد هذه المعلومات المطورين على تحسين أداء تطبيقاتهم وتحليل نقاط الضعف في التحميل.

## الوثائق
### الغرض
تستخدم PerformanceScriptTiming لقياس الوقت الذي يستغرقه تحميل نصوص JavaScript المختلفة في صفحة الويب. من خلال جمع معلومات حول وقت البدء والانتهاء، يمكن للمطورين فهم تأثير هذه النصوص على أداء الصفحة.

### الاستخدام
يمكن الوصول إلى PerformanceScriptTiming من خلال واجهة Performance API. يتضمن هذا الهيكل معلومات مثل:
- `startTime`: الوقت الذي بدأ فيه تحميل النص البرمجي.
- `duration`: الوقت الذي استغرقه تحميل النص البرمجي.
- `scriptSrc`: مصدر النص البرمجي.

### التفاصيل
لكي تستخدم PerformanceScriptTiming، يجب أن تكون النصوص البرمجية قد تم تحميلها باستخدام خاصية `performance.mark()` و `performance.measure()` لتحديد الأنشطة. من المهم أن تكون هذه المعلومات متاحة فقط بعد تحميل النصوص البرمجية.

## الأمثلة
### مثال أساسي
```javascript
// تحديد علامة لبدء التحميل
performance.mark('start-loading-script');

// تحميل النص البرمجي
const script = document.createElement('script');
script.src = 'script.js';
document.head.appendChild(script);

// تحديد علامة لإنهاء التحميل
script.onload = function() {
    performance.mark('end-loading-script');
    performance.measure('script-loading', 'start-loading-script', 'end-loading-script');

    const measurements = performance.getEntriesByName('script-loading');
    measurements.forEach(measurement => {
        console.log(`Script loaded from ${measurement.scriptSrc} in ${measurement.duration} milliseconds.`);
    });
};
```

## الشرح
### الأخطاء الشائعة والملاحظات
- **عدم تسجيل العلامات بشكل صحيح**: تأكد من أنك تسجل العلامات قبل وبعد تحميل النص البرمجي مباشرة.
- **عدم وجود قياسات**: إذا لم تقم بتسجيل القياسات بشكل صحيح، فلن تحصل على أي معلومات حول الأداء.
- **استخدام في المتصفحات القديمة**: تأكد من أن المتصفح يدعم Performance API، فقد تكون هناك قيود في المتصفحات القديمة.

## ملخص جملة واحدة
PerformanceScriptTiming هو أداة قوية لتحليل وتحسين أداء تحميل النصوص البرمجية في JavaScript.