<!--
Meta Description: # واجهة ScreenOrientation في JavaScript: التحكم في اتجاه الشاشة ## الملخص واجهة ScreenOrientation في JavaScript تتيح للمطورين إدارة اتجاه الشاشة في ال...
Meta Keywords: الاتجاه, واجهة, screenorientation, اتجاه, الشاشة
-->

# واجهة ScreenOrientation في JavaScript: التحكم في اتجاه الشاشة

## الملخص
واجهة ScreenOrientation في JavaScript تتيح للمطورين إدارة اتجاه الشاشة في المتصفحات، مما يسهل تحسين تجربة المستخدم على الأجهزة المحمولة.

## الوثائق
### الغرض
تُستخدم واجهة ScreenOrientation لتمكين التحكم في اتجاه شاشة الجهاز، سواء كان ذلك في الوضع العمودي أو الأفقي. تساعد هذه الواجهة في تحسين تجربة المستخدم من خلال ضمان توافق تطبيقات الويب مع اتجاه الجهاز.

### الاستخدام
يمكن الوصول إلى واجهة ScreenOrientation من خلال `window.screen.orientation`. توفر هذه الواجهة مجموعة من الخصائص والطرق التي تسمح للمطورين بتحديد الاتجاه المطلوب ومعرفة الاتجاه الحالي.

### الخصائص
- `type`: تُرجع نوع الاتجاه الحالي (مثل "portrait" أو "landscape").
- `angle`: تُرجع الزاوية الحالية للشاشة.
- `lock()`: تُستخدم لقفل الاتجاه في وضع معين.
- `unlock()`: تُستخدم لفك قفل الاتجاه.

### طرق الاستخدام
للاستفادة من واجهة ScreenOrientation، يجب أولاً التحقق من دعم المتصفح لهذه الواجهة. يمكن استخدام الشيفرة التالية:

```javascript
if (screen.orientation) {
    console.log("واجهة ScreenOrientation مدعومة!");
} else {
    console.log("واجهة ScreenOrientation غير مدعومة.");
}
```

## أمثلة
### قفل اتجاه الشاشة
لإجبار الشاشة على الاتجاه الأفقي، يمكن استخدام الشيفرة التالية:

```javascript
if (screen.orientation) {
    screen.orientation.lock('landscape')
        .then(() => {
            console.log("تم قفل الاتجاه إلى الأفقي.");
        })
        .catch(err => {
            console.error("فشل قفل الاتجاه: ", err);
        });
}
```

### الحصول على الاتجاه الحالي
للحصول على الاتجاه الحالي للشاشة، يمكن استخدام الشيفرة التالية:

```javascript
if (screen.orientation) {
    console.log("الاتجاه الحالي هو: " + screen.orientation.type);
}
```

## الشرح
### الأخطاء الشائعة
1. **عدم دعم المتصفح**: قد لا تدعم بعض المتصفحات القديمة واجهة ScreenOrientation، لذا يجب دائمًا التحقق من الدعم قبل استخدام الواجهة.
2. **قيود القفل**: قد لا يتمكن بعض المستخدمين من قفل اتجاه الشاشة بسبب إعدادات نظام التشغيل أو قيود في المتصفح.
3. **التعامل مع الأحداث**: يجب الانتباه إلى الأحداث مثل `change` التي يمكن أن تؤثر على استجابة التطبيق لاتجاه الشاشة.

## ملخص بعبارة واحدة
واجهة ScreenOrientation في JavaScript توفر وسيلة فعالة للتحكم في اتجاه الشاشة وتحسين تجربة المستخدم على الأجهزة المحمولة.