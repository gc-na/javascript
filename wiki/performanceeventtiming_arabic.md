<!--
Meta Description: # PerformanceEventTiming في جافا سكريبت: تحسين أداء التطبيقات على الويب ## ملخص PerformanceEventTiming هو واجهة في جافا سكريبت تتيح للمطورين قياس وتحل...
Meta Keywords: على, الأحداث, performanceeventtiming, أداء, الحدث
-->

# PerformanceEventTiming في جافا سكريبت: تحسين أداء التطبيقات على الويب

## ملخص
PerformanceEventTiming هو واجهة في جافا سكريبت تتيح للمطورين قياس وتحليل أداء الأحداث في تطبيقات الويب، مما يساعد في تحسين تجربة المستخدم.

## الوثائق
### الغرض
PerformanceEventTiming هو جزء من واجهة Performance API التي تقدم معلومات دقيقة عن توقيت الأحداث، مثل وقت التحميل والوقت المستغرق في التعامل مع الأحداث. يهدف هذا إلى تمكين المطورين من تحليل الأداء وتحسينه.

### الاستخدام
يمكن الوصول إلى PerformanceEventTiming من خلال كائن performance، والذي يحتوي على مجموعة من خصائص التوقيت المهمة. يتم استخدامه عادةً لتحديد مدى فعالية الأحداث، مثل النقرات أو التفاعلات الأخرى.

### التفاصيل
- **الخصائص**:
  - `name`: اسم الحدث.
  - `entryType`: نوع الإدخال، والذي يكون دائمًا "event".
  - `startTime`: الوقت الذي بدأ فيه الحدث.
  - `duration`: المدة التي استغرقها الحدث.
  
- **كيفية الحصول على PerformanceEventTiming**:
  لالتقاط توقيت حدث معين، يمكن استخدام `PerformanceObserver` لمراقبة الأحداث.

## أمثلة
### مثال أساسي على كيفية استخدام PerformanceEventTiming
```javascript
// إنشاء PerformanceObserver لمراقبة الأحداث
const observer = new PerformanceObserver((list) => {
    list.getEntries().forEach((entry) => {
        console.log(`حدث: ${entry.name}`);
        console.log(`وقت البدء: ${entry.startTime}`);
        console.log(`مدة الحدث: ${entry.duration}`);
    });
});

// بدء المراقبة على الأحداث
observer.observe({ entryTypes: ['event'] });

// تسجيل حدث
const button = document.getElementById("myButton");
button.addEventListener("click", () => {
    console.log("تم النقر على الزر");
});
```

## الشرح
### الفخاخ الشائعة
1. **عدم تفعيل المراقبة**: يجب التأكد من تفعيل `PerformanceObserver` قبل تسجيل الأحداث، وإلا فلن يتم التقاط المعلومات.
2. **تجاهل البيانات**: يجب معالجة البيانات التي تم جمعها بشكل صحيح، حيث يمكن أن تكون هناك أحداث متعددة تحتاج إلى تحليل.
3. **الأداء**: قد تؤثر المراقبة على أداء التطبيق إذا تم استخدامها بشكل مفرط، لذا يفضل استخدامها بحذر.

## ملخص في جملة واحدة
PerformanceEventTiming هو واجهة في جافا سكريبت تساعد المطورين على قياس وتحليل أداء أحداث الويب لتحسين تجربة المستخدم.