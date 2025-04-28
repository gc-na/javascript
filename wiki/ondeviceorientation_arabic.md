<!--
Meta Description: # ondeviceorientation في JavaScript: كيفية استخدامه وفهمه ## ملخص تعتبر خاصية `ondeviceorientation` في JavaScript وسيلة لاستقبال بيانات اتجاه الجهاز، ...
Meta Keywords: event, ondeviceorientation, حول, alpha, beta
-->

# ondeviceorientation في JavaScript: كيفية استخدامه وفهمه

## ملخص
تعتبر خاصية `ondeviceorientation` في JavaScript وسيلة لاستقبال بيانات اتجاه الجهاز، مما يسمح للمطورين بإنشاء تجارب تفاعلية بناءً على موضع الجهاز في الفضاء.

## التوثيق
تُستخدم خاصية `ondeviceorientation` للتعامل مع أحداث التوجيه للجهاز، والتي تُعطى من خلال مستشعرات الجيروسكوب والمستشعرات الأخرى. يمكن استخدام هذه الخاصية لتطوير تطبيقات تفاعلية مثل الألعاب أو التطبيقات التي تعتمد على الواقع المعزز.

### الغرض
يهدف استخدام `ondeviceorientation` إلى تقديم معلومات حول الاتجاهات الثلاثة للجهاز:
- **الزاوية حول المحور X** (الميل الأمامي والخلفي)
- **الزاوية حول المحور Y** (اللف الجانبي)
- **الزاوية حول المحور Z** (الدوران)

### الاستخدام
لتنفيذ `ondeviceorientation`، يمكن استخدام الكود التالي:

```javascript
window.ondeviceorientation = function(event) {
    const alpha = event.alpha; // الزاوية حول المحور Z
    const beta = event.beta;   // الزاوية حول المحور X
    const gamma = event.gamma; // الزاوية حول المحور Y

    console.log(`Alpha: ${alpha}, Beta: ${beta}, Gamma: ${gamma}`);
};
```

## الأمثلة
### مثال 1: تسجيل الاتجاهات
```javascript
window.ondeviceorientation = function(event) {
    console.log(`Alpha: ${event.alpha}, Beta: ${event.beta}, Gamma: ${event.gamma}`);
};
```

### مثال 2: استخدام القيم لتدوير عنصر
```javascript
const box = document.getElementById('box');

window.ondeviceorientation = function(event) {
    box.style.transform = `rotateZ(${event.alpha}deg) rotateX(${event.beta}deg) rotateY(${event.gamma}deg)`;
};
```

## الشرح
### المشاكل الشائعة
1. **عدم استجابة الأحداث**: قد لا تعمل خاصية `ondeviceorientation` على بعض الأجهزة أو المتصفحات القديمة. تأكد من استخدام متصفح حديث يدعم هذه الخاصية.
2. **إذن الوصول**: في بعض المتصفحات، قد تحتاج إلى طلب إذن المستخدم لاستخدام مستشعرات الجهاز. استخدم `DeviceOrientationEvent.requestPermission()` على الأجهزة المحمولة.
3. **الدقة**: قد تختلف دقة البيانات المستلمة بناءً على نوع الجهاز والمستشعرات المتاحة.

## ملخص في جملة واحدة
تتيح خاصية `ondeviceorientation` في JavaScript للمطورين الوصول إلى بيانات اتجاه الجهاز، مما يسهل تطوير تجارب تفاعلية فريدة.