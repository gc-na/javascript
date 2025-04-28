<!--
Meta Description: # PerformanceNavigationTiming في جافا سكريبت: تحسين أداء التطبيقات ## ملخص تعتبر واجهة `PerformanceNavigationTiming` جزءًا من واجهة `Performance` في ج...
Meta Keywords: navigationtiming, performancenavigationtiming, تحميل, console, performance
-->

# PerformanceNavigationTiming في جافا سكريبت: تحسين أداء التطبيقات

## ملخص
تعتبر واجهة `PerformanceNavigationTiming` جزءًا من واجهة `Performance` في جافا سكريبت، وتوفر معلومات تفصيلية حول كيفية تحميل المستندات في المتصفح. تساعد هذه الواجهة المطورين في قياس أداء تحميل الصفحات وتحسين تجربة المستخدم.

## الوثائق
### الغرض
تستخدم `PerformanceNavigationTiming` لجمع معلومات حول زمن التحميل والتفاعلية في صفحات الويب. يمكن أن تساعد هذه المعلومات في تحديد نقاط الضعف وتحسين الأداء العام للتطبيقات.

### الاستخدام
يمكن الوصول إلى `PerformanceNavigationTiming` من خلال خاصية `performance.getEntriesByType('navigation')`. توفر هذه الطريقة مجموعة من الكائنات التي تحتوي على تفاصيل حول كل عملية تحميل.

### التفاصيل
- **الخصائص**: تحتوي `PerformanceNavigationTiming` على عدة خصائص مهمة، منها:
  - `startTime`: وقت بدء التحميل.
  - `responseEnd`: الوقت الذي تم فيه استلام استجابة الشبكة.
  - `domContentLoadedEventEnd`: الوقت الذي انتهى فيه حدث تحميل محتوى DOM.
  - `loadEventEnd`: الوقت الذي انتهى فيه حدث التحميل الكامل للصفحة.

### كيفية الاستخدام
```javascript
const [navigationTiming] = performance.getEntriesByType('navigation');

console.log('Start Time:', navigationTiming.startTime);
console.log('Response End:', navigationTiming.responseEnd);
console.log('DOM Content Loaded Event End:', navigationTiming.domContentLoadedEventEnd);
console.log('Load Event End:', navigationTiming.loadEventEnd);
```

## الأمثلة
### مثال بسيط
```javascript
window.onload = function() {
    const [navigationTiming] = performance.getEntriesByType('navigation');
    
    console.log('Total Time:', navigationTiming.loadEventEnd - navigationTiming.startTime);
};
```

### مثال متقدم
```javascript
window.addEventListener('load', () => {
    const [navigationTiming] = performance.getEntriesByType('navigation');
    
    const metrics = {
        redirectTime: navigationTiming.redirectEnd - navigationTiming.redirectStart,
        appCacheTime: navigationTiming.domainLookupStart - navigationTiming.fetchStart,
        serverConnectionTime: navigationTiming.connectEnd - navigationTiming.connectStart,
        responseTime: navigationTiming.responseEnd - navigationTiming.responseStart,
        domContentLoadedTime: navigationTiming.domContentLoadedEventEnd - navigationTiming.fetchStart,
        pageLoadTime: navigationTiming.loadEventEnd - navigationTiming.fetchStart
    };
    
    console.table(metrics);
});
```

## الشرح
### الأخطاء الشائعة
- **عدم الانتظار للتحميل الكامل**: تأكد من استخدام `window.onload` أو أحداث أخرى لضمان جمع البيانات بعد تحميل الصفحة بالكامل.
- **نقص في البيانات**: قد لا يتوفر `PerformanceNavigationTiming` في بعض المتصفحات القديمة، تحقق من توافق المتصفح قبل الاعتماد عليها.

### ملاحظات إضافية
- يمكن استخدام `PerformanceNavigationTiming` لتحليل الأداء في أدوات مثل Google Lighthouse.
- تأكد من أن بيانات الأداء يتم جمعها في بيئة إنتاجية للحصول على قياسات دقيقة.

## ملخص
تعتبر `PerformanceNavigationTiming` أداة قيمة لتحليل أداء تحميل الصفحات في جافا سكريبت، مما يساعد المطورين على تحسين تجربة المستخدم بشكل فعال.