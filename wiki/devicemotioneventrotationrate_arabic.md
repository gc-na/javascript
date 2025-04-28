<!--
Meta Description: # جهاز حركة الحدث: معدل الدوران (DeviceMotionEventRotationRate) في JavaScript ## ملخص يُعتبر `DeviceMotionEventRotationRate` واجهة في JavaScript تُستخ...
Meta Keywords: rotationrate, معدل, حول, الدوران, console
-->

# جهاز حركة الحدث: معدل الدوران (DeviceMotionEventRotationRate) في JavaScript

## ملخص
يُعتبر `DeviceMotionEventRotationRate` واجهة في JavaScript تُستخدم للوصول إلى معلومات حول معدل دوران الجهاز، مما يتيح للمطورين إنشاء تطبيقات تستجيب لحركة الجهاز.

## الوثائق
### الغرض
`DeviceMotionEventRotationRate` هي كائن يحتوي على معلومات عن معدل دوران الجهاز حول محاور X و Y و Z. تُستخدم هذه البيانات في تطبيقات مثل الألعاب، والواقع المعزز، وتطبيقات تتطلب تفاعلاً مع الحركة.

### الاستخدام
عند استخدام `DeviceMotionEvent`، يمكنك الاستماع إلى الأحداث المرتبطة بحركة الجهاز والحصول على معلومات حول معدل الدوران من خلال خاصية `rotationRate`.

### التفاصيل
- **المسار**: `DeviceMotionEvent.rotationRate`
- **القيم**:
  - `alpha`: معدل الدوران حول المحور Z (بالدرجات في الثانية).
  - `beta`: معدل الدوران حول المحور X (بالدرجات في الثانية).
  - `gamma`: معدل الدوران حول المحور Y (بالدرجات في الثانية).

يتم إرجاع القيم ككائن يحتوي على الخصائص الثلاثة المذكورة.

## أمثلة
### مثال أساسي
```javascript
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', function(event) {
        let rotationRate = event.rotationRate;
        console.log('Mعدل الدوران حول المحور X: ' + rotationRate.alpha);
        console.log('معدل الدوران حول المحور Y: ' + rotationRate.beta);
        console.log('معدل الدوران حول المحور Z: ' + rotationRate.gamma);
    });
} else {
    console.log('جهازك لا يدعم أحداث الحركة.');
}
```

### مثال مع التحقق من القيم
```javascript
if (window.DeviceMotionEvent) {
    window.addEventListener('devicemotion', function(event) {
        let rotationRate = event.rotationRate;
        // تحقق من وجود القيم
        if (rotationRate.alpha !== null && rotationRate.beta !== null && rotationRate.gamma !== null) {
            console.log('البيانات متاحة:');
            console.log(rotationRate);
        } else {
            console.log('لا توجد بيانات متاحة حول معدل الدوران.');
        }
    });
}
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم الأحداث**: ليس كل الأجهزة تدعم `DeviceMotionEvent`. تأكد من التحقق من دعم المتصفح قبل محاولة استخدام هذه الميزة.
- **القيم الخالية**: في بعض الأحيان، قد لا تتوفر القيم (تكون null) بسبب قيود على المستشعرات أو إعدادات الخصوصية.
- **الأمان والخصوصية**: بعض المتصفحات قد تتطلب إذنًا للوصول إلى بيانات الحركة، لذا تأكد من التعامل مع الأذونات بشكل صحيح.

### ملاحظات إضافية
- تأكد من استخدام `devicemotion` في بيئة آمنة (مثل HTTPS) حيث أن بعض المتصفحات تمنع الوصول إلى معلومات الحركة في السياقات غير الآمنة.

## ملخص من جملة واحدة
`DeviceMotionEventRotationRate` في JavaScript يتيح الوصول إلى معلومات معدل دوران الجهاز، مما يمكن المطورين من إنشاء تطبيقات تفاعلية تعتمد على حركة الجهاز.