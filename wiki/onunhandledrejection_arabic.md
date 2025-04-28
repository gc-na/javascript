<!--
Meta Description: # التعامل مع onUnhandledRejection في JavaScript: كيفية التعامل مع الأخطاء غير المعالجة ## الملخص تعتبر `onunhandledrejection` حدثًا مهمًا في JavaScrip...
Meta Keywords: onunhandledrejection, الأخطاء, event, المعالجة, التعامل
-->

# التعامل مع onUnhandledRejection في JavaScript: كيفية التعامل مع الأخطاء غير المعالجة

## الملخص
تعتبر `onunhandledrejection` حدثًا مهمًا في JavaScript يُستخدم للتعامل مع الوعود (Promises) التي تم رفضها دون معالجة. يوفر هذا الحدث وسيلة لرصد الأخطاء غير المعالجة في التطبيقات، مما يساعد المطورين على تحسين موثوقية التطبيق وتجربة المستخدم.

## الوثائق
### الغرض
يهدف حدث `onunhandledrejection` إلى توفير وسيلة لرصد الأخطاء التي تحدث عند رفض الوعود دون وجود مستمع (handler) لهذا الرفض. عندما يتم رفض وعد ولم يتم التعامل معه، يتم تفعيل هذا الحدث.

### الاستخدام
يمكنك استخدام `onunhandledrejection` لتسجيل الأخطاء أو عرض رسائل توضيحية للمستخدم. يتم تعيين مستمع لهذا الحدث على مستوى `window`، مما يعني أنه سيشمل جميع الوعود في التطبيق.

### التفاصيل
- **صيغة الحدث**: `window.onunhandledrejection = function(event) { ... }`
- **الخاصية `event.reason`**: تحتوي على سبب الرفض.

## الأمثلة
### مثال 1: تسجيل الأخطاء غير المعالجة
```javascript
window.onunhandledrejection = function(event) {
    console.error('Unhandled rejection:', event.reason);
};

new Promise((resolve, reject) => {
    reject(new Error('Something went wrong!'));
});
```

### مثال 2: عرض رسالة للمستخدم
```javascript
window.onunhandledrejection = function(event) {
    alert('حدث خطأ: ' + event.reason.message);
};

new Promise((resolve, reject) => {
    reject(new Error('خطأ في الطلب!'));
});
```

## الشرح
### الأخطاء الشائعة
- **عدم تسجيل المستمع**: إذا لم تقم بتسجيل `onunhandledrejection`، فلن يتمكن المتصفح من التعامل مع الوعود المرفوضة، مما قد يؤدي إلى فقدان معلومات مهمة عن الأخطاء.
- **عدم الانتباه للسبب**: يجب دائمًا فحص `event.reason` لفهم سبب الخطأ وتقديم المعالجة المناسبة.

### ملاحظات إضافية
- يجب أن تكون حذرًا عند استخدام `onunhandledrejection`، حيث يمكن أن يؤثر على أداء التطبيق إذا كان هناك الكثير من الأخطاء غير المعالجة.
- يفضل استخدام `try...catch` مع `async/await` للتقليل من الأخطاء غير المعالجة.

## ملخص جملة واحدة
يتيح `onunhandledrejection` في JavaScript للمطورين التعامل مع الأخطاء في الوعود المرفوضة دون معالجة، مما يعزز الثقة والاستقرار في التطبيقات.