<!--
Meta Description: # MouseEvent في JavaScript: دليل شامل ## الملخص MouseEvent هو كائن في JavaScript يمثل الأحداث الناتجة عن تفاعل المستخدم مع الماوس، مثل النقر، الحركة، ...
Meta Keywords: mouseevent, javascript, كائن, يمكن, الحدث
-->

# MouseEvent في JavaScript: دليل شامل

## الملخص
MouseEvent هو كائن في JavaScript يمثل الأحداث الناتجة عن تفاعل المستخدم مع الماوس، مثل النقر، الحركة، والضغط.

## الوثائق
### الغرض
يستخدم كائن MouseEvent للتفاعل مع الأحداث المتعلقة بالماوس في واجهات المستخدم. يمكن أن يتضمن ذلك أحداث مثل النقر، التحريك، الضغط، والإفلات، مما يسمح للمطورين بالاستجابة لتصرفات المستخدم وتحسين تجربة الاستخدام.

### الاستخدام
لإنشاء MouseEvent، يمكن استخدام الدالة `MouseEvent()`، حيث يمكنك تحديد نوع الحدث والخصائص الأخرى. على سبيل المثال، يمكنك إنشاء حدث نقر جديد على النحو التالي:

```javascript
const clickEvent = new MouseEvent('click', {
    bubbles: true,
    cancelable: true,
    clientX: 100,
    clientY: 200
});
```

### التفاصيل
يحتوي كائن MouseEvent على مجموعة من الخصائص المهمة، منها:
- `type`: نوع الحدث (مثل "click" أو "mousemove").
- `bubbles`: تشير إلى ما إذا كان الحدث يمكن أن ينفجر.
- `cancelable`: تشير إلى ما إذا كان يمكن إلغاء الحدث.
- `clientX` و`clientY`: تعطي إحداثيات موقع الماوس بالنسبة لنافذة العرض.

## الأمثلة
### مثال 1: استجابة لحدث النقر
```javascript
document.getElementById('myButton').addEventListener('click', function(event) {
    console.log('Button clicked at:', event.clientX, event.clientY);
});
```

### مثال 2: إنشاء حدث مخصص
```javascript
const myDiv = document.getElementById('myDiv');
const event = new MouseEvent('click', { bubbles: true });
myDiv.dispatchEvent(event);
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من خصائص الحدث**: قد ينسى المطورون التحقق من خصائص كائن MouseEvent، مما قد يؤدي إلى سلوك غير متوقع.
- **عدم إدارة الأحداث بشكل صحيح**: عدم إزالة أحداث الاستماع قد يؤدي إلى تسرب الذاكرة.

### ملاحظات إضافية
- تأكد من أن الكود يعمل في بيئات متعددة، حيث يمكن أن تختلف سلوكيات الأحداث بين المتصفحات.
- استخدام `preventDefault()` لإلغاء سلوك افتراضي للحدث إذا لزم الأمر.

## ملخص بجملة واحدة
MouseEvent هو كائن في JavaScript يمكّنك من التعامل مع أحداث الماوس، مما يسهل تفاعل المستخدم مع واجهات الويب.