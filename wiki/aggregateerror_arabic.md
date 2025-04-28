<!--
Meta Description: # AggregateError في JavaScript: فهم شامل ## الملخص AggregateError هو نوع من الأخطاء في JavaScript يُستخدم لتجميع عدة أخطاء في كائن واحد، مما يسهل التع...
Meta Keywords: aggregateerror, error, promise, الأخطاء, خطأ
-->

# AggregateError في JavaScript: فهم شامل

## الملخص
AggregateError هو نوع من الأخطاء في JavaScript يُستخدم لتجميع عدة أخطاء في كائن واحد، مما يسهل التعامل معها في العمليات غير المتزامنة.

## الوثائق
### الغرض
AggregateError هو كائن يُستخدم لتجميع مجموعة من الأخطاء التي قد تحدث أثناء تنفيذ العمليات غير المتزامنة، مثل Promise.all. يُعتبر هذا النوع من الأخطاء مفيدًا عندما تحتاج إلى معالجة عدة أخطاء بشكل متزامن.

### الاستخدام
يمكن استخدام AggregateError عندما ترغب في التقاط عدة أخطاء من مجموعة من العمليات غير المتزامنة بدلاً من التقاط خطأ واحد فقط. يُمكنك استخدامه مع الدوال التي تُعيد وعودًا (Promises) مثل `Promise.all` و`Promise.any`.

### التفاصيل
- **الخصائص**:
  - `name`: اسم الخطأ، والذي سيكون "AggregateError".
  - `errors`: مصفوفة تحتوي على الأخطاء الفردية التي تم تجميعها.
  
- **الإنشاء**:
  يتم إنشاء AggregateError باستخدام الكلمة المفتاحية `new`، مع تمرير مصفوفة من الأخطاء التي تريد تجميعها.

```javascript
const error1 = new Error("خطأ 1");
const error2 = new Error("خطأ 2");
const aggregateError = new AggregateError([error1, error2], "تم تجميع الأخطاء");
```

## الأمثلة
### مثال 1: استخدام AggregateError مع Promise.all
```javascript
const promise1 = Promise.resolve(1);
const promise2 = Promise.reject(new Error("خطأ في الوعد الثاني"));
const promise3 = Promise.reject(new Error("خطأ في الوعد الثالث"));

Promise.all([promise1, promise2, promise3])
  .then(results => {
    console.log(results);
  })
  .catch(error => {
    if (error instanceof AggregateError) {
      console.log("تم تجميع الأخطاء:", error.errors);
    } else {
      console.log("خطأ منفرد:", error);
    }
  });
```

### مثال 2: استخدام AggregateError مع Promise.any
```javascript
const promiseA = Promise.reject(new Error("خطأ A"));
const promiseB = Promise.reject(new Error("خطأ B"));
const promiseC = Promise.resolve("نجاح C");

Promise.any([promiseA, promiseB, promiseC])
  .then(result => {
    console.log(result); // "نجاح C"
  })
  .catch(error => {
    if (error instanceof AggregateError) {
      console.log("تم تجميع الأخطاء:", error.errors);
    } else {
      console.log("خطأ منفرد:", error);
    }
  });
```

## الشرح
### الأخطاء الشائعة
- **عدم معالجة الأخطاء بشكل صحيح**: قد يعتقد المطورون أنه يمكنهم استخدام AggregateError كأي خطأ آخر، لكن يجب التأكد من أن الكود يتعامل مع مصفوفة الأخطاء بشكل صحيح.
- **إغفال الرسالة**: عند إنشاء AggregateError، من المهم تمرير رسالة توضيحية لتسهيل فهم الأخطاء المجمعة.

### ملاحظات إضافية
AggregateError هي خاصية متاحة في بيئات JavaScript الحديثة (ES2021 وما بعدها)، لذا تأكد من أن بيئتك تدعمها.

## ملخص من سطر واحد
AggregateError في JavaScript يُستخدم لتجميع عدة أخطاء في كائن واحد، مما يسهل إدارتها في العمليات غير المتزامنة.