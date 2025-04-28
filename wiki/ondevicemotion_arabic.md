<!--
Meta Description: # ondevicemotion في JavaScript: كيفية استخدامه لتتبع حركة الجهاز ## ملخص تعتبر خاصية `ondevicemotion` في JavaScript وسيلة فعالة لتتبع حركة الجهاز باست...
Meta Keywords: الجهاز, event, acceleration, ondevicemotion, javascript
-->

# ondevicemotion في JavaScript: كيفية استخدامه لتتبع حركة الجهاز

## ملخص
تعتبر خاصية `ondevicemotion` في JavaScript وسيلة فعالة لتتبع حركة الجهاز باستخدام مستشعرات التسارع. تستخدم هذه الخاصية في تطبيقات الويب لتحسين تجربة المستخدم من خلال التفاعل مع حركة الجهاز.

## الوثائق
### الغرض
تُستخدم `ondevicemotion` للكشف عن التغيرات في حركة الجهاز، مثل التسارع في المحاور الثلاثة (X، Y، Z) وكذلك الدوران. يمكن استخدام هذه المعلومات في تطوير الألعاب، التطبيقات التفاعلية، وغيرها من التطبيقات التي تتطلب استجابة لحركة الجهاز.

### الاستخدام
يمكن استخدام `ondevicemotion` بطرق عدة. يجب أولاً التحقق من دعم المتصفح لهذه الخاصية. بعد ذلك، يمكن إعداد مستمع للأحداث ليتعامل مع بيانات الحركة.

### التفاصيل
عند التفعيل، يقوم المتصفح بإرسال بيانات عن الحركة إلى المستمع المحدد. تتضمن هذه البيانات كلاً من `acceleration` و `accelerationIncludingGravity` و `rotationRate`.

### التركيب
```javascript
window.addEventListener('devicemotion', function(event) {
    // معالجة البيانات هنا
    let acceleration = event.acceleration;
    let rotationRate = event.rotationRate;

    console.log('تسارع المحاور: ', acceleration);
    console.log('معدل الدوران: ', rotationRate);
});
```

## الأمثلة
### مثال بسيط
```javascript
window.addEventListener('devicemotion', function(event) {
    let x = event.acceleration.x;
    let y = event.acceleration.y;
    let z = event.acceleration.z;

    console.log(`تسارع X: ${x}, Y: ${y}, Z: ${z}`);
});
```

### مثال لتطبيق عملي
```javascript
window.addEventListener('devicemotion', function(event) {
    let { x, y, z } = event.acceleration;

    if (x > 10) {
        console.log("الجهاز يتحرك بسرعة في الاتجاه X");
    } else if (y > 10) {
        console.log("الجهاز يتحرك بسرعة في الاتجاه Y");
    }
});
```

## الشرح
### المشاكل الشائعة
- **الدعم غير المتساوي:** ليست جميع المتصفحات تدعم `ondevicemotion`. تأكد من اختبار الكود في بيئات متعددة.
- **إعدادات الخصوصية:** قد يتطلب بعض المتصفحات إذن الوصول إلى مستشعرات الجهاز.
- **التعامل مع البيانات:** تأكد من معالجة البيانات بشكل صحيح لتجنب التداخل أو السلوك غير المتوقع.

### ملاحظات إضافية
يمكن أن تؤدي استخدام `ondevicemotion` في التطبيقات ذات الأداء العالي إلى استهلاك موارد البطارية. لذا، يُفضل استخدام هذه الخاصية بحذر.

## ملخص بجملة واحدة
`ondevicemotion` هي خاصية في JavaScript تسمح بتتبع حركة الجهاز باستخدام مستشعرات التسارع، مما يوفر تجربة تفاعلية محسنة في التطبيقات.