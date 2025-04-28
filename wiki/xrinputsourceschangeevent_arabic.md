<!--
Meta Description: # XRInputSourcesChangeEvent في JavaScript: حدث التغيير في مصادر الإدخال للواقع المعزز ## ملخص يعد `XRInputSourcesChangeEvent` حدثًا مهمًا في واجهة برم...
Meta Keywords: الإدخال, مصادر, الحدث, xrinputsourceschangeevent, javascript
-->

# XRInputSourcesChangeEvent في JavaScript: حدث التغيير في مصادر الإدخال للواقع المعزز

## ملخص
يعد `XRInputSourcesChangeEvent` حدثًا مهمًا في واجهة برمجة التطبيقات للواقع الممتد (XR) في JavaScript. يُستخدم هذا الحدث لإعلام المطورين بأي تغييرات تطرأ على مصادر الإدخال، مثل وحدات التحكم أو أجهزة الاستشعار المستخدمة في تجارب الواقع الافتراضي (VR) والواقع المعزز (AR).

## الوثائق
### الغرض
يهدف `XRInputSourcesChangeEvent` إلى تزويد المطورين بمعلومات حول الإضافات أو الحذف أو التغييرات في مصادر الإدخال المستخدمة في تطبيقات XR الخاصة بهم. يمكن استخدام هذا الحدث لتحديث الحالة أو واجهة المستخدم عند حدوث تغييرات في الأجهزة.

### الاستخدام
يتم إصدار هذا الحدث من قبل كائن `XRSession`، ويتم الاستماع إليه باستخدام `addEventListener`، مما يسمح للتطبيقات بالتفاعل مع إدخالات المستخدم بشكل ديناميكي.

### التفاصيل
- **الخصائص**:
  - `added`: قائمة بمصادر الإدخال الجديدة.
  - `removed`: قائمة بمصادر الإدخال التي تمت إزالتها.
  
- **الأسلوب**:
  ```javascript
  xrSession.addEventListener('inputsourceschange', function(event) {
      // التعامل مع الحدث هنا
  });
  ```

## الأمثلة
### مثال بسيط على استخدام `XRInputSourcesChangeEvent`
```javascript
// بدء جلسة XR
const xrSession = navigator.xr.requestSession('immersive-vr').then(onSessionStarted);

function onSessionStarted(session) {
    session.addEventListener('inputsourceschange', onInputSourcesChange);
}

function onInputSourcesChange(event) {
    const added = event.added;
    const removed = event.removed;

    // معالجة مصادر الإدخال الجديدة
    added.forEach(source => {
        console.log('تم إضافة مصدر إدخال:', source);
    });

    // معالجة مصادر الإدخال التي تمت إزالتها
    removed.forEach(source => {
        console.log('تمت إزالة مصدر إدخال:', source);
    });
}
```

## الشرح
### الأخطاء الشائعة
- **عدم تسجيل الحدث**: تأكد من أنك قد قمت بتسجيل الحدث بعد بدء جلسة XR. إذا حاولت التسجيل قبل ذلك، فلن يتم استدعاء المعالج.
- **عدم التحقق من الحالة**: تأكد من التحقق من حالة `added` و `removed` بشكل صحيح لتفادي الأخطاء في معالجة الإدخال.

### ملاحظات إضافية
- قد تختلف مصادر الإدخال المتاحة بناءً على الأجهزة المستخدمة، لذا احرص على اختبار تطبيقاتك على مجموعة متنوعة من الأجهزة.
- تأكد من أن لديك الأذونات الصحيحة لاستخدام ميزات XR في متصفحك.

## ملخص بعبارة واحدة
`XRInputSourcesChangeEvent` هو حدث في JavaScript يُستخدم لمتابعة التغييرات في مصادر الإدخال المستخدمة في تطبيقات الواقع الافتراضي والواقع المعزز.