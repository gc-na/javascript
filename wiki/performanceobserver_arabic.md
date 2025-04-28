<!--
Meta Description: # PerformanceObserver في JavaScript: تحسين أداء التطبيقات ## ملخص PerformanceObserver هو واجهة في JavaScript تُستخدم لمراقبة وتحليل أداء تطبيقات الويب...
Meta Keywords: performanceobserver, entry, javascript, observer, الأحداث
-->

# PerformanceObserver في JavaScript: تحسين أداء التطبيقات

## ملخص
PerformanceObserver هو واجهة في JavaScript تُستخدم لمراقبة وتحليل أداء تطبيقات الويب من خلال تتبع الأحداث المتعلقة بالأداء. تساعد هذه الواجهة المطورين على جمع بيانات الأداء في الوقت الحقيقي وتحليلها لتحسين تجربة المستخدم.

## الوثائق
### الغرض
تُستخدم PerformanceObserver لمراقبة الأحداث المرتبطة بالأداء، مثل زمن تحميل الموارد، وزمن تنفيذ العمليات، وغيرها. يتيح لك ذلك فهم كيفية استجابة تطبيقك وتحسين أدائه.

### الاستخدام
لإنشاء PerformanceObserver، يجب عليك اتباع الخطوات التالية:

1. **إنشاء مثيل من PerformanceObserver**:
   يمكنك إنشاء مثيل من PerformanceObserver من خلال تمرير دالة رد نداء (callback) التي سيتم استدعاؤها عند حدوث الأحداث.

   ```javascript
   const observer = new PerformanceObserver((list) => {
       for (const entry of list.getEntries()) {
           console.log(entry);
       }
   });
   ```

2. **بدء المراقبة**:
   يجب عليك تحديد نوع الأحداث التي ترغب في مراقبتها باستخدام `observe`، مثل "resource" أو "mark" أو "measure".

   ```javascript
   observer.observe({ entryTypes: ['resource'] });
   ```

3. **إيقاف المراقبة**:
   يمكنك إيقاف المراقبة في أي وقت باستخدام `disconnect`.

   ```javascript
   observer.disconnect();
   ```

## الأمثلة
### مثال أساسي لمراقبة الموارد
```javascript
const observer = new PerformanceObserver((list) => {
    list.getEntries().forEach((entry) => {
        console.log(`Resource: ${entry.name}, Duration: ${entry.duration}`);
    });
});

observer.observe({ entryTypes: ['resource'] });

// تحميل مورد للتجربة
const img = new Image();
img.src = 'https://example.com/image.jpg';
```

### مثال على مراقبة العلامات والقياسات
```javascript
const observer = new PerformanceObserver((list) => {
    list.getEntries().forEach((entry) => {
        console.log(`Mark: ${entry.name}, Start Time: ${entry.startTime}, Duration: ${entry.duration}`);
    });
});

observer.observe({ entryTypes: ['mark', 'measure'] });

// إضافة علامة
performance.mark('start');
// عملية تستغرق بعض الوقت
setTimeout(() => {
    performance.mark('end');
    performance.measure('My Measure', 'start', 'end');
}, 1000);
```

## الشرح
### المخاطر الشائعة والملاحظات
- **الأداء**: يجب أن تكون حذرًا عند استخدام PerformanceObserver في التطبيقات ذات الأداء الحساس، حيث إن تسجيل الكثير من البيانات قد يؤثر سلبًا على الأداء.
- **التحجيم**: عند مراقبة عدد كبير من الأحداث، قد يصبح من الصعب تحليل البيانات. من المستحسن تحديد نوع الأحداث التي تحتاج إلى مراقبتها فقط.
- **التوافق**: تأكد من أن بيئة التشغيل تدعم PerformanceObserver، حيث قد تختلف درجات الدعم بين المتصفحات.

## ملخص بجملة واحدة
PerformanceObserver هو أداة قوية في JavaScript لمراقبة وتحليل أداء تطبيقات الويب، مما يساعد المطورين على تحسين تجربة المستخدم.