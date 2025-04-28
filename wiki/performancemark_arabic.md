<!--
Meta Description: # PerformanceMark في JavaScript: تحسين أداء التطبيقات ## ملخص **PerformanceMark** هي واجهة برمجية في JavaScript تُستخدم لتسجيل نقاط الأداء في التطبيقا...
Meta Keywords: performance, javascript, mark, performancemark, إنشاء
-->

# PerformanceMark في JavaScript: تحسين أداء التطبيقات

## ملخص
**PerformanceMark** هي واجهة برمجية في JavaScript تُستخدم لتسجيل نقاط الأداء في التطبيقات، مما يسمح للمطورين بتتبع وتحليل أداء التطبيقات وتحسينها بشكل فعال.

## الوثائق
### الغرض
تتيح **PerformanceMark** للمطورين القدرة على إنشاء نقاط مرجعية في كود JavaScript لتحديد فترات زمنية معينة، مما يساعد في قياس الأداء وتحديد bottlenecks.

### الاستخدام
يمكنك استخدام **PerformanceMark** من خلال استدعاء الدالة `performance.mark()`، حيث تأخذ هذه الدالة اسمًا كنقطة مرجعية. بعد إنشاء النقاط، يمكنك استردادها باستخدام `performance.getEntriesByType('mark')`.

#### التركيب
```javascript
performance.mark(name);
```

- **name**: اسم النقطة المرجعية (سلسلة نصية).

### التفاصيل
- يمكن استخدام النقاط المرجعية لتحديد وقت بدء أو انتهاء عملية معينة.
- يمكن أن يؤدي الاستخدام الجيد لـ **PerformanceMark** إلى تحسين أداء التطبيق وجعله أكثر كفاءة.
- النقاط المرجعية لا تؤثر على الأداء بحد ذاتها، بل توفر وسيلة للقياس والتحليل.

## الأمثلة
### مثال 1: إنشاء نقطة مرجعية
```javascript
// إنشاء نقطة مرجعية عند بدء تحميل البيانات
performance.mark('startLoadData');

// محاكاة تحميل البيانات
setTimeout(() => {
    // إنشاء نقطة مرجعية عند انتهاء تحميل البيانات
    performance.mark('endLoadData');

    // حساب الوقت المستغرق
    performance.measure('loadDataDuration', 'startLoadData', 'endLoadData');
    
    // عرض النتائج
    const measures = performance.getEntriesByType('measure');
    console.log(measures);
}, 1000);
```

### مثال 2: استخدام النقاط المرجعية لقياس الأداء
```javascript
performance.mark('taskStart');

// تنفيذ مهمة معينة
doSomeTask();

performance.mark('taskEnd');

// قياس الوقت المستغرق
performance.measure('taskDuration', 'taskStart', 'taskEnd');
const duration = performance.getEntriesByName('taskDuration')[0];
console.log(`مدة المهمة: ${duration.duration} ميلي ثانية`);
```

## التفسير
### الأخطاء الشائعة والملاحظات
- تأكد من استخدام أسماء فريدة للنقاط المرجعية لتجنب التداخل.
- يجب أن تكون النقاط المرجعية واضحة ومحددة لتحقيق أقصى استفادة من القياس.
- تجنب إنشاء العديد من النقاط في فترة قصيرة، حيث قد يؤدي ذلك إلى تشويش البيانات.

## ملخص جملة واحدة
**PerformanceMark** في JavaScript هي أداة قوية لتسجيل نقاط الأداء وتحليلها بهدف تحسين كفاءة التطبيقات.