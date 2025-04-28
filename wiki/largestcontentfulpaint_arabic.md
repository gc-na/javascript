<!--
Meta Description: # أكبر محتوى مرئي (Largest Contentful Paint) في JavaScript ## ملخص أكبر محتوى مرئي (LCP) هو مقياس أداء مهم في تجربة المستخدم، حيث يقيس الوقت الذي يستغ...
Meta Keywords: lcp, تحميل, أكبر, مرئي, الصفحة
-->

# أكبر محتوى مرئي (Largest Contentful Paint) في JavaScript

## ملخص
أكبر محتوى مرئي (LCP) هو مقياس أداء مهم في تجربة المستخدم، حيث يقيس الوقت الذي يستغرقه تحميل أكبر عنصر مرئي في الصفحة. في JavaScript، يمكن قياس LCP باستخدام واجهة Performance API.

## الوثائق
### الغرض
يهدف LCP إلى قياس سرعة تحميل المحتوى المرئي الرئيسي، مما يعكس تجربة المستخدم الفعلية. يعتبر LCP جزءًا من مجموعة مقاييس تسمى "مقاييس تجربة المستخدم الأساسية" (Core Web Vitals).

### الاستخدام
يمكن قياس LCP باستخدام واجهة Performance API المتاحة في المتصفحات الحديثة. يتم ذلك عن طريق الاستماع للأحداث التي تشير إلى تحميل العناصر المرئية.

### التفاصيل
1. **التوافر**: LCP متاح في معظم المتصفحات الحديثة.
2. **الإعداد**: يجب إعداد مراقب للتحقق من LCP عند تحميل الصفحة.
3. **التحليل**: يمكن استخدام القيمة الناتجة لتحسين أداء الصفحة.

### الكود:
```javascript
let lcp;

const observer = new PerformanceObserver((entryList) => {
    const entries = entryList.getEntries();
    lcp = entries[entries.length - 1]; // الحصول على أكبر محتوى مرئي
});

observer.observe({ type: 'largest-contentful-paint', buffered: true });

// بعد انتهاء التحميل، يمكنك استخدام قيمة LCP
window.addEventListener('load', () => {
    console.log('أكبر محتوى مرئي تم تحميله في: ', lcp.startTime);
});
```

## الأمثلة
### مثال بسيط
في المثال التالي، نقوم بقياس LCP عند تحميل الصفحة:
```javascript
const lcpObserver = new PerformanceObserver((entries) => {
    entries.getEntries().forEach((entry) => {
        console.log('LCP:', entry.startTime);
    });
});

lcpObserver.observe({ type: 'largest-contentful-paint', buffered: true });
```

## الشرح
### الأخطاء الشائعة
- **عدم الانتباه لأوقات التحميل**: قد يتأخر LCP بسبب تحميل العناصر الثقيلة أو الصور غير المحسنة.
- **تجاهل تحسين الأداء**: عدم استخدام تقنيات مثل التحميل الكسول (lazy loading) قد يؤثر سلبًا على LCP.

### ملاحظات إضافية
- **النطاق الزمني**: تأكد من قياس LCP في الوقت المناسب، مثل بعد تحميل الصفحة مباشرة.
- **التوافق مع المتصفحات**: تحقق من دعم المتصفح للـ Performance API لضمان دقة القياسات.

## ملخص من سطر واحد
أكبر محتوى مرئي (LCP) هو مقياس أساسي لسرعة تحميل أكبر عنصر مرئي في الصفحة باستخدام JavaScript.