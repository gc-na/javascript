<!--
Meta Description: # أداء توقيت الأداء (PerformanceTiming) في JavaScript ## ملخص PerformanceTiming هو واجهة في JavaScript تقدم معلومات تفصيلية حول توقيت تحميل الصفحة، مم...
Meta Keywords: الوقت, الذي, فيه, تحميل, بدأ
-->

# أداء توقيت الأداء (PerformanceTiming) في JavaScript

## ملخص
PerformanceTiming هو واجهة في JavaScript تقدم معلومات تفصيلية حول توقيت تحميل الصفحة، مما يساعد المطورين في تحسين أداء تطبيقاتهم.

## الوثائق
تعتبر واجهة PerformanceTiming جزءًا من واجهة Performance في HTML5، وتوفر مجموعة من الخصائص التي تُظهر مختلف مراحل تحميل الصفحة. الغرض من PerformanceTiming هو تمكين المطورين من قياس وتحليل الأداء لتطبيقاتهم، مما يساعد في تحسين تجربة المستخدم.

### الخصائص الرئيسية
- `navigationStart`: الوقت الذي بدأت فيه عملية التنقل.
- `unloadEventStart`: الوقت الذي بدأ فيه حدث التفريغ (unload).
- `unloadEventEnd`: الوقت الذي انتهى فيه حدث التفريغ.
- `redirectStart`: الوقت الذي بدأ فيه إعادة التوجيه (redirect).
- `redirectEnd`: الوقت الذي انتهى فيه إعادة التوجيه.
- `fetchStart`: الوقت الذي بدأ فيه تحميل المورد.
- `domainLookupStart`: الوقت الذي بدأ فيه البحث عن اسم النطاق.
- `domainLookupEnd`: الوقت الذي انتهى فيه البحث عن اسم النطاق.
- `connectStart`: الوقت الذي بدأ فيه الاتصال بالخادم.
- `connectEnd`: الوقت الذي انتهى فيه الاتصال بالخادم.
- `secureConnectionStart`: الوقت الذي بدأ فيه الاتصال الآمن.
- `requestStart`: الوقت الذي بدأ فيه طلب المورد.
- `responseStart`: الوقت الذي بدأ فيه استلام الرد.
- `responseEnd`: الوقت الذي انتهى فيه استلام الرد.
- `domLoading`: الوقت الذي بدأ فيه تحميل DOM.
- `domInteractive`: الوقت الذي أصبح فيه DOM تفاعليًا.
- `domContentLoadedEventStart`: الوقت الذي بدأ فيه حدث تحميل محتوى DOM.
- `domContentLoadedEventEnd`: الوقت الذي انتهى فيه حدث تحميل محتوى DOM.
- `domComplete`: الوقت الذي انتهى فيه تحميل DOM بالكامل.
- `loadEventStart`: الوقت الذي بدأ فيه حدث التحميل.
- `loadEventEnd`: الوقت الذي انتهى فيه حدث التحميل.

### الاستخدام
يمكنك الوصول إلى كائن PerformanceTiming من خلال `performance.timing`، ومن ثم يمكنك استخدام الخصائص المختلفة لقياس الزمن بين الأحداث المختلفة.

## أمثلة
### مثال أساسي
```javascript
// الحصول على توقيت الأداء
var timing = performance.timing;

// حساب زمن تحميل الصفحة
var loadTime = timing.loadEventEnd - timing.navigationStart;

console.log("زمن تحميل الصفحة: " + loadTime + " ميلي ثانية");
```

### مثال متقدم
```javascript
// الحصول على تفاصيل زمن تحميل الصفحة
var timing = performance.timing;

console.log("زمن البحث عن النطاق: " + (timing.domainLookupEnd - timing.domainLookupStart) + " ميلي ثانية");
console.log("زمن تحميل المحتوى: " + (timing.responseEnd - timing.requestStart) + " ميلي ثانية");
```

## الشرح
قد يواجه المطورون بعض التحديات عند استخدام PerformanceTiming، مثل:
- **تأخر البيانات**: يعتمد الأداء على ظروف الشبكة، لذا قد تختلف النتائج من مستخدم لآخر.
- **الاختلاف بين المتصفحات**: قد تختلف كيفية تنفيذ PerformanceTiming بين المتصفحات، مما يتطلب اختبارًا شاملاً.
- **توقيتات غير متوقعة**: في بعض الحالات، قد تشير القيم إلى أوقات غير متوقعة بسبب أحداث خارجية مثل التأخير في الشبكة.

## ملخص جملة واحدة
تساعد واجهة PerformanceTiming في قياس وتحليل أوقات تحميل الصفحة في JavaScript، مما يساهم في تحسين أداء التطبيقات.