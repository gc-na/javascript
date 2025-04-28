<!--
Meta Description: # PerformanceServerTiming في جافا سكريبت: تحسين الأداء وقياس السرعة ## ملخص PerformanceServerTiming هو واجهة برمجة تطبيقات (API) في جافا سكريبت تساعد ...
Meta Keywords: performanceservertiming, الخادم, timing, على, الاستجابة
-->

# PerformanceServerTiming في جافا سكريبت: تحسين الأداء وقياس السرعة

## ملخص
PerformanceServerTiming هو واجهة برمجة تطبيقات (API) في جافا سكريبت تساعد المطورين على قياس وتحليل زمن الاستجابة للطلبات المرسلة إلى الخادم. تُستخدم هذه الأداة لتحسين الأداء العام للتطبيقات من خلال تقديم معلومات دقيقة حول زمن الاستجابة.

## الوثائق
### الغرض
تتيح واجهة PerformanceServerTiming للمطورين تتبع زمن الاستجابة للطلبات التي يتم إرسالها إلى الخوادم. يساعد ذلك في تحديد نقاط الضعف في الأداء وتحسين تجربة المستخدم.

### الاستخدام
يمكن استخدام PerformanceServerTiming عن طريق إضافة معلومات توقيت الخادم في رأس الاستجابة HTTP. يتم ذلك باستخدام الكائن `PerformanceServerTiming` الذي يحتوي على مجموعة من الخصائص.

### التفاصيل
- **واجهة برمجة التطبيقات**: يمكن الوصول إلى PerformanceServerTiming من خلال الكائن `performance` في جافا سكريبت.
- **الخصائص**:
  - `name`: اسم المقياس.
  - `duration`: زمن القياس بالمللي ثانية.
  - `description`: وصف إضافي (اختياري) لتوفير مزيد من المعلومات حول المقياس.

### كيفية التفعيل
لإضافة معلومات PerformanceServerTiming، يجب أن يحتوي رأس الاستجابة HTTP على المعلومات المطلوبة. على سبيل المثال:
```
Server-Timing: app;dur=50, db;dur=30
```

## الأمثلة
### مثال أساسي
```javascript
// قراءة توقيتات الخادم
const serverTimings = performance.getEntriesByType("navigation")[0].serverTiming;

serverTimings.forEach(timing => {
    console.log(`Server: ${timing.name}, Duration: ${timing.duration}ms`);
});
```

### مثال متقدم
```javascript
// إضافة توقيتات الخادم في الاستجابة
fetch('/api/data')
    .then(response => {
        const serverTimings = response.headers.get('Server-Timing');
        console.log('Server Timings:', serverTimings);
    });
```

## الشرح
### العقبات الشائعة
- **عدم وجود بيانات**: في بعض الأحيان، قد لا تكون معلومات Server Timing متاحة إذا لم يتم تكوين الخادم بشكل صحيح.
- **التعارض مع أدوات التتبع الأخرى**: في حال استخدام أدوات تتبع الأداء الأخرى، قد يحدث تداخل في البيانات.

### ملاحظات إضافية
- تأكد من أن الخادم يدعم رأس `Server-Timing`.
- قد تختلف دقة القياس بناءً على كيفية إعداد الخادم وبيانات الشبكة.

## ملخص بعبارة واحدة
PerformanceServerTiming هو أداة قوية في جافا سكريبت لتحليل أداء الطلبات إلى الخادم، مما يساعد على تحسين سرعة التطبيق وتجربة المستخدم.