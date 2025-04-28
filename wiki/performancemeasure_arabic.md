<!--
Meta Description: # قياس الأداء (PerformanceMeasure) في JavaScript: تحسين الأداء في تطبيقات الويب ## ملخص تُستخدم دالة قياس الأداء (PerformanceMeasure) في JavaScript لق...
Meta Keywords: performance, mark, الأداء, javascript, قياس
-->

# قياس الأداء (PerformanceMeasure) في JavaScript: تحسين الأداء في تطبيقات الويب

## ملخص
تُستخدم دالة قياس الأداء (PerformanceMeasure) في JavaScript لقياس الأداء الزمني لعمليات معينة داخل تطبيقات الويب، مما يساعد المطورين على تحسين سرعة التطبيق وتجربة المستخدم.

## الوثائق
### الغرض
دالة PerformanceMeasure جزء من واجهة Performance API في JavaScript، والتي تقدم أدوات لقياس أداء التطبيقات. يمكن استخدامها لتسجيل وقت تنفيذ العمليات، مما يمكّن المطورين من تحليل الأداء بشكل أعمق.

### الاستخدام
يمكن استخدام PerformanceMeasure عن طريق استدعاء دالة `performance.measure()`، والتي تتطلب اسمًا للقياس ووقت البداية والنهاية. يتم تسجيل هذه القياسات في متصفح المستخدم، ويمكن الوصول إليها لاحقًا.

### التفاصيل
- **التركيب**:
  ```javascript
  performance.measure(name, startMark, endMark);
  ```
  - `name`: اسم القياس.
  - `startMark`: (اختياري) علامة البدء (start mark) التي تم تسجيلها باستخدام `performance.mark()`.
  - `endMark`: (اختياري) علامة الانتهاء (end mark) التي تم تسجيلها باستخدام `performance.mark()`.

- **المتطلبات**: يجب أن تكون قد قمت بتسجيل علامات البدء والانتهاء باستخدام `performance.mark()` قبل استخدام `performance.measure()`.

## أمثلة
### مثال 1: قياس زمن تنفيذ عملية
```javascript
performance.mark('start');
// تنفيذ عملية معينة
setTimeout(() => {
  performance.mark('end');
  performance.measure('myOperation', 'start', 'end');
  
  const measures = performance.getEntriesByName('myOperation');
  console.log(measures);
}, 1000);
```

### مثال 2: قياس زمن تحميل صفحة
```javascript
performance.mark('pageStart');
// تحميل الصفحة أو تنفيذ عملية
performance.mark('pageEnd');
performance.measure('pageLoad', 'pageStart', 'pageEnd');

const loadMeasures = performance.getEntriesByName('pageLoad');
console.log(loadMeasures);
```

## الشرح
### الأخطاء الشائعة
- **عدم تسجيل العلامات**: تأكد من أنك قد قمت بتسجيل علامات البدء والانتهاء قبل قياس الأداء. إذا لم تقم بذلك، فإن القياس لن يكون دقيقًا.
- **عدم استرجاع القياسات**: يجب استخدام `performance.getEntriesByName()` لاسترجاع القياسات بعد تسجيلها.

### ملاحظات إضافية
- يمكن أن تؤثر عمليات القياس على الأداء، لذا يُفضل استخدامها في بيئات التطوير أو الاختبار.
- تأكد من أن اسم القياس فريد لتجنب التعارض مع قياسات أخرى.

## ملخص بجملة واحدة
دالة PerformanceMeasure في JavaScript تُستخدم لقياس زمن تنفيذ العمليات وتحسين أداء تطبيقات الويب.