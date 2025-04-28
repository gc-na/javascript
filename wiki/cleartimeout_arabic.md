<!--
Meta Description: # clearTimeout في JavaScript: كيفية استخدامه وإدارته ## ملخص `clearTimeout` هو دالة في JavaScript تُستخدم لإلغاء مؤقت (timeout) تم تعيينه مسبقًا باستخ...
Meta Keywords: cleartimeout, settimeout, إلغاء, المؤقت, javascript
-->

# clearTimeout في JavaScript: كيفية استخدامه وإدارته

## ملخص
`clearTimeout` هو دالة في JavaScript تُستخدم لإلغاء مؤقت (timeout) تم تعيينه مسبقًا باستخدام `setTimeout`. تتيح هذه الدالة للمطورين التحكم في العمليات التي تعتمد على التأخير، مما يساعد على تحسين أداء التطبيقات.

## الوثائق
### الغرض
تُستخدم دالة `clearTimeout` لإلغاء مؤقت تم تحديده بواسطة `setTimeout`. يُعتبر هذا مفيدًا عندما تحتاج إلى إلغاء تنفيذ دالة معينة كانت ستُنفذ بعد فترة زمنية محددة.

### الاستخدام
تأخذ `clearTimeout` معلمة واحدة، وهي معرف المؤقت (timeout ID) الذي تم إرجاعه بواسطة `setTimeout`. إذا تم تمرير معرف غير صحيح أو معرف لم يتم تعيينه، فلا يحدث أي تأثير.

### التركيب
```javascript
clearTimeout(timeoutID);
```
- `timeoutID`: هو المعرف الذي تم إرجاعه من دالة `setTimeout`.

## الأمثلة
### المثال 1: إلغاء مؤقت بسيط
```javascript
let timeoutID = setTimeout(() => {
    console.log("هذا النص لن يظهر، لأنه تم إلغاء المؤقت.");
}, 2000);

// إلغاء المؤقت بعد 1 ثانية
setTimeout(() => {
    clearTimeout(timeoutID);
    console.log("تم إلغاء المؤقت.");
}, 1000);
```

### المثال 2: استخدام clearTimeout في دالة
```javascript
function startTimer() {
    let timeoutID = setTimeout(() => {
        console.log("المؤقت انتهى.");
    }, 3000);

    // إلغاء المؤقت بعد 1.5 ثانية
    setTimeout(() => {
        clearTimeout(timeoutID);
        console.log("تم إلغاء المؤقت.");
    }, 1500);
}

startTimer();
```

## الشرح
### الأخطاء الشائعة
1. **عدم تخزين معرف المؤقت**: من الأخطاء الشائعة عدم تخزين القيمة المعادة من `setTimeout`، مما يجعل من المستحيل إلغاء المؤقت لاحقًا.
2. **إلغاء مؤقت لم يتم تعيينه**: إذا حاولت استخدام `clearTimeout` مع معرف غير صحيح، فلن يحدث أي تأثير، مما قد يؤدي إلى الالتباس.
3. **الاستدعاء المتعدد**: استدعاء `clearTimeout` بشكل متكرر بنفس المعرف لن يؤثر على الأداء، حيث يتم إلغاء المؤقت مرة واحدة فقط.

## ملخص بعبارة واحدة
`clearTimeout` هي دالة في JavaScript تُستخدم لإلغاء مؤقت محدد بواسطة `setTimeout`، مما يتيح التحكم في تنفيذ الدوال المتأخرة.