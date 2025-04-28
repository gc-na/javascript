<!--
Meta Description: # مستشعر الاتجاه النسبي (RelativeOrientationSensor) في JavaScript ## ملخص مستشعر الاتجاه النسبي هو واجهة برمجة التطبيقات (API) في JavaScript تتيح للمط...
Meta Keywords: sensor, relativeorientationsensor, الاتجاه, النسبي, مستشعر
-->

# مستشعر الاتجاه النسبي (RelativeOrientationSensor) في JavaScript

## ملخص
مستشعر الاتجاه النسبي هو واجهة برمجة التطبيقات (API) في JavaScript تتيح للمطورين الوصول إلى بيانات الاتجاه النسبي للجهاز، مما يساعد في تطوير تطبيقات تعتمد على الحركة والاتجاه.

## الوثائق
### الغرض
مستشعر الاتجاه النسبي يوفر معلومات حول اتجاه الجهاز بالنسبة إلى الأرض. يستخدم هذا المستشعر في مجموعة من التطبيقات مثل الألعاب، الواقع المعزز، وتطبيقات الملاحة.

### الاستخدام
يتم استخدام مستشعر الاتجاه النسبي عن طريق إنشاء مثيل جديد لـ `RelativeOrientationSensor`. يتطلب هذا المستشعر إذن المستخدم للوصول إلى بيانات الاستشعار.

### التفاصيل
```javascript
if ('RelativeOrientationSensor' in window) {
    const sensor = new RelativeOrientationSensor({
        frequency: 60 // عدد الإطارات في الثانية
    });

    sensor.addEventListener('reading', () => {
        console.log(`Orientation: ${sensor.quaternion}`);
    });

    sensor.start();
} else {
    console.error("RelativeOrientationSensor is not supported in this browser.");
}
```
- **quaternion:** يعيد متجهات الاتجاه التي تمثل اتجاه الجهاز.
- **frequency:** يحدد عدد مرات تحديث البيانات في الثانية.

## الأمثلة
### مثال أساسي
```javascript
if ('RelativeOrientationSensor' in window) {
    const sensor = new RelativeOrientationSensor();

    sensor.addEventListener('reading', () => {
        console.log(`Orientation: ${sensor.quaternion}`);
    });

    sensor.start();
} else {
    console.log("المستشعر غير مدعوم.");
}
```

### مثال مع ضبط التردد
```javascript
if ('RelativeOrientationSensor' in window) {
    const sensor = new RelativeOrientationSensor({ frequency: 30 });

    sensor.addEventListener('reading', () => {
        console.log(`Orientation: ${sensor.quaternion}`);
    });

    sensor.start();
} else {
    alert("المستشعر غير مدعوم في هذا المتصفح.");
}
```

## الشرح
- **المشاكل الشائعة:** يجب على المطورين التأكد من أن المستشعر مدعوم في المتصفح المستخدم قبل محاولة استخدامه.
- **الإذونات:** يجب على المستخدم منح إذن الوصول إلى مستشعرات الجهاز، وفي حالة عدم السماح، لن تعمل واجهة برمجة التطبيقات.
- **التوافق:** ليس جميع المتصفحات تدعم مستشعر الاتجاه النسبي، لذا يجب اختبار التطبيق في بيئات مختلفة.

## ملخص لجملة واحدة
مستشعر الاتجاه النسبي في JavaScript يوفر واجهة للوصول إلى بيانات اتجاه الجهاز، مما يسهل تطوير تطبيقات تفاعلية تعتمد على الحركة.