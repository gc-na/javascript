<!--
Meta Description: # NetworkInformation في JavaScript: دليل شامل ## ملخص تُعد واجهة `NetworkInformation` جزءًا من واجهة برمجة التطبيقات (API) الخاصة بالشبكات في JavaScri...
Meta Keywords: الاتصال, connection, networkinformation, معلومات, واجهة
-->

# NetworkInformation في JavaScript: دليل شامل

## ملخص
تُعد واجهة `NetworkInformation` جزءًا من واجهة برمجة التطبيقات (API) الخاصة بالشبكات في JavaScript، وتوفر معلومات حول حالة الاتصال الشبكي للجهاز. يساعد المطورين في فهم جودة الاتصال وسرعته، مما يسمح بتحسين تجربة المستخدم.

## الوثائق
### الغرض
تتيح واجهة `NetworkInformation` الوصول إلى معلومات الشبكة الحالية. يمكن للمطورين استخدامها لمراقبة تغيرات حالة الاتصال، مثل الانتقال بين الشبكات المختلفة أو التغييرات في جودة الاتصال.

### الاستخدام
يمكن الوصول إلى واجهة `NetworkInformation` من خلال الكائن `navigator`. يتم استخدامه بشكل أساسي للحصول على معلومات حول الاتصال الحالي، مثل نوع الشبكة وسرعة الاتصال.

#### الخصائص الأساسية
- **`navigator.connection`**: يعيد كائن من نوع `NetworkInformation` يحتوي على تفاصيل الاتصال.

#### الطرق
تتضمن الطرق المتاحة في `NetworkInformation`:
- **`addEventListener`**: للاستماع إلى تغييرات حالة الاتصال.
- **`removeEventListener`**: لإزالة مستمعي الأحداث.

## الأمثلة
### مثال 1: الحصول على معلومات الاتصال
```javascript
if ('connection' in navigator) {
    const connection = navigator.connection;
    console.log('نوع الاتصال:', connection.effectiveType);
    console.log('سرعة الاتصال:', connection.downlink, 'ميغابت في الثانية');
}
```

### مثال 2: الاستماع لتغييرات الاتصال
```javascript
if ('connection' in navigator) {
    const connection = navigator.connection;

    const updateConnectionStatus = () => {
        console.log('تم تحديث حالة الاتصال:', connection.effectiveType);
    };

    connection.addEventListener('change', updateConnectionStatus);
}
```

## الشرح
### الفخاخ الشائعة
- **عدم دعم المتصفح**: ليست جميع المتصفحات تدعم واجهة `NetworkInformation`. يجب التحقق من توافرها قبل استخدامها.
- **تغيرات غير متوقعة**: قد يحدث أن تتغير حالة الاتصال بشكل مفاجئ، لذا يُفضل استخدام أحداث التغيير لضمان الحصول على معلومات دقيقة.

### ملاحظات إضافية
- يوفر `NetworkInformation` معلومات مفيدة لتحسين تجربة المستخدم، خاصة في التطبيقات التي تتطلب اتصالاً جيدًا.
- يمكن استخدام المعلومات المتاحة لتخصيص المحتوى أو تحسين الأداء بناءً على نوع الاتصال.

## ملخص بعبارة واحدة
تتيح واجهة `NetworkInformation` في JavaScript الوصول إلى معلومات قيمة حول حالة الشبكة وسرعة الاتصال، مما يساعد على تحسين تجربة المستخدم في التطبيقات.