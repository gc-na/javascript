<!--
Meta Description: # مستشعر التسارع في JavaScript: استخداماته وتطبيقاته ## ملخص مستشعر التسارع (Accelerometer) في JavaScript يُتيح للمطورين الوصول إلى بيانات تسارع الجها...
Meta Keywords: التسارع, مستشعر, javascript, على, acceleration
-->

# مستشعر التسارع في JavaScript: استخداماته وتطبيقاته

## ملخص
مستشعر التسارع (Accelerometer) في JavaScript يُتيح للمطورين الوصول إلى بيانات تسارع الجهاز، مما يمكّنهم من تطوير تطبيقات تفاعلية تعتمد على حركة الجهاز.

## الوثائق
### الغرض
مستشعر التسارع يستخدم لقياس التسارع في ثلاثة محاور: X، Y، وZ. يمكن استخدام هذه البيانات في تطبيقات مثل الألعاب، والتطبيقات الرياضية، وتطبيقات الواقع المعزز.

### الاستخدام
يتم الوصول إلى مستشعر التسارع من خلال واجهة `DeviceMotionEvent` في JavaScript. يمكن للمطورين استخدام هذه الواجهة للحصول على معلومات حول تسارع الجهاز.

### التفاصيل
لتتمكن من استخدام مستشعر التسارع، يجب أولاً التأكد من أن المتصفح يدعم واجهة `DeviceMotionEvent`. بعد ذلك، يمكن استخدام الكود التالي للاستماع إلى أحداث الحركة:

```javascript
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', function(event) {
        const acceleration = event.acceleration;
        console.log(`تسارع X: ${acceleration.x}`);
        console.log(`تسارع Y: ${acceleration.y}`);
        console.log(`تسارع Z: ${acceleration.z}`);
    });
} else {
    console.log('مستشعر التسارع غير مدعوم في هذا المتصفح.');
}
```

## أمثلة
### مثال أساسي
إليك مثالاً بسيطاً يوضح كيفية استخدام مستشعر التسارع:

```javascript
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', (event) => {
        const { x, y, z } = event.acceleration;
        document.getElementById('output').innerText = `تسارع: X=${x}, Y=${y}, Z=${z}`;
    });
} else {
    alert('مستشعر التسارع غير مدعوم.');
}
```

### مثال على الرسم البياني
يمكنك استخدام البيانات لإنشاء رسم بياني:

```javascript
const data = [];
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', (event) => {
        data.push(event.acceleration);
        // كود لإنشاء رسم بياني باستخدام مكتبة مثل Chart.js
    });
}
```

## الشرح
### الأخطاء الشائعة
- قد تواجه مشكلات في الوصول إلى بيانات مستشعر التسارع على بعض الأجهزة أو المتصفحات التي لا تدعم `DeviceMotionEvent`.
- يجب التأكد من أن لديك الأذونات اللازمة للوصول إلى بيانات الحركة، خاصة على الأجهزة المحمولة.

### ملاحظات إضافية
- قد تختلف دقة بيانات التسارع بناءً على الجهاز المستخدم.
- تأكد من اختبار التطبيق على مجموعة متنوعة من الأجهزة لضمان عمله بشكل صحيح.

## ملخص بنص واحد
مستشعر التسارع في JavaScript يسمح للمطورين بالوصول إلى بيانات الحركة الثلاثية الأبعاد للجهاز لتطوير تطبيقات تفاعلية ومبتكرة.