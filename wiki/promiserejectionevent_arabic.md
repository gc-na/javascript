<!--
Meta Description: # PromiseRejectionEvent في JavaScript: كل ما تحتاج معرفته ## ملخص تعتبر `PromiseRejectionEvent` إحدى الأحداث المهمة في JavaScript التي تُستخدم لمعالجة...
Meta Keywords: promiserejectionevent, javascript, promise, event, الرفض
-->

# PromiseRejectionEvent في JavaScript: كل ما تحتاج معرفته

## ملخص
تعتبر `PromiseRejectionEvent` إحدى الأحداث المهمة في JavaScript التي تُستخدم لمعالجة الرفض غير المعالج للوعود (Promises). تُتيح هذه الميزة للمطورين تتبع الأخطاء التي قد تحدث بسبب الوعود غير الموفرة.

## الوثائق
`PromiseRejectionEvent` هو حدث يُطلق عندما يتم رفض وعد (Promise) ولكن لم يتم التعامل مع هذا الرفض بواسطة دالة `catch` أو معالج الرفض. يتم استخدام هذا الحدث بشكل رئيسي مع الـ `window` كجزء من واجهة برمجة التطبيقات الخاصة بالأحداث في المتصفح.

### الغرض
الغرض من `PromiseRejectionEvent` هو توفير وسيلة للمطورين لمراقبة الوعود غير المعالجة والتعامل مع الأخطاء بشكل أكثر فعالية.

### الاستخدام
يمكنك الاستماع إلى حدث `unhandledrejection` الذي يمثل `PromiseRejectionEvent` كما يلي:

```javascript
window.addEventListener('unhandledrejection', (event) => {
    console.log('Unhandled promise rejection:', event.reason);
});
```

### التفاصيل
- **الخاصية `reason`**: تُستخدم للوصول إلى سبب الرفض.
- **الهدف**: مساعدة المطورين في تحديد ومعالجة الأخطاء مبكرًا قبل أن تتسبب في مشكلات أكبر.

## الأمثلة

### مثال 1: التعامل مع رفض وعد غير معالج
```javascript
window.addEventListener('unhandledrejection', (event) => {
    console.log('Unhandled promise rejection:', event.reason);
});

// وعد مرفوض بدون معالجة
Promise.reject(new Error('Something went wrong'));
```

### مثال 2: استخدام `PromiseRejectionEvent` مع `try...catch`
```javascript
window.addEventListener('unhandledrejection', (event) => {
    console.log('Unhandled promise rejection:', event.reason);
});

const failingPromise = new Promise((resolve, reject) => {
    reject('Error occurred!');
});

// محاولة معالجة الرفض
failingPromise.catch((error) => {
    console.log('Caught error:', error);
});
```

## الشرح
- **نقاط يجب الانتباه لها**: من المهم دائمًا التعامل مع الوعود (Promises) بشكل صحيح باستخدام `.catch()` لتجنب إطلاق `PromiseRejectionEvent`. إذا لم يتم ذلك، فقد يؤدي إلى مشاكل في الأداء أو صعوبة في تتبع الأخطاء.
- **الإصدار**: تم تضمين `PromiseRejectionEvent` في ECMAScript 2015 (ES6) ويمكن استخدامه في معظم المتصفحات الحديثة.

## ملخص جملة واحدة
`PromiseRejectionEvent` هو حدث في JavaScript يساعد المطورين على مراقبة الوعود غير المعالجة وتحسين إدارة الأخطاء.