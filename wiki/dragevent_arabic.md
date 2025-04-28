<!--
Meta Description: # DragEvent في JavaScript: دليل شامل ## الملخص يُعتبر DragEvent في JavaScript واحدًا من الأحداث المتعلقة بالسحب والإفلات، حيث يتيح للمطورين تنفيذ تفاع...
Meta Keywords: السحب, event, dragevent, يتم, javascript
-->

# DragEvent في JavaScript: دليل شامل

## الملخص
يُعتبر DragEvent في JavaScript واحدًا من الأحداث المتعلقة بالسحب والإفلات، حيث يتيح للمطورين تنفيذ تفاعلات سحب العناصر عبر واجهة المستخدم.

## الوثائق
### الغرض
تُستخدم DragEvent لتوفير معلومات حول أحداث السحب والإفلات في المتصفح. يتم إطلاق هذا الحدث عندما يتم سحب عنصر ما، مما يتيح للمطورين التعامل مع التفاعلات المرتبطة بالسحب.

### الاستخدام
يتضمن الحدث DragEvent عدة خصائص وطرق مفيدة مثل:
- **properties**:
  - `dataTransfer`: كائن يُستخدم لنقل البيانات بين العناصر.
  - `clientX` و `clientY`: إحداثيات الموقع حيث يتم سحب العنصر.
  
- **طرق**:
  - `preventDefault()`: تمنع التصرف الافتراضي للحدث.
  
### تفاصيل
يتم استخدام DragEvent في عدة مواقف، مثل:
- سحب العناصر داخل واجهة المستخدم.
- سحب العناصر بين النوافذ أو التطبيقات.
- دعم السحب والإفلات لتحسين تجربة المستخدم.

يتم إطلاق DragEvent في عدة مراحل من عملية السحب، بما في ذلك:
- `dragstart`: عند بدء السحب.
- `drag`: أثناء عملية السحب.
- `dragend`: عند انتهاء عملية السحب.

## الأمثلة
### مثال أساسي
```javascript
const draggableElement = document.getElementById('draggable');
draggableElement.addEventListener('dragstart', (event) => {
    event.dataTransfer.setData('text/plain', event.target.id);
});
```

### مثال على الإنهاء
```javascript
const dropZone = document.getElementById('dropzone');
dropZone.addEventListener('dragover', (event) => {
    event.preventDefault(); // يسمح بالإفلات
});

dropZone.addEventListener('drop', (event) => {
    const data = event.dataTransfer.getData('text/plain');
    const element = document.getElementById(data);
    dropZone.appendChild(element);
});
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام `event.preventDefault()`**: إذا لم يتم استدعاء هذه الوظيفة أثناء حدث `dragover`، فلن يُسمح بالإفلات.
- **فقدان البيانات عند السحب**: يجب التأكد من استخدام `dataTransfer` بشكل صحيح لتجنب فقدان البيانات أثناء عملية السحب.

### ملاحظات إضافية
- تأكد من أن العناصر القابلة للسحب تحتوي على خاصية `draggable="true"` ليتمكن المستخدمون من سحبها.
- يمكن أن تؤثر أنماط CSS على سلوك السحب والإفلات، لذا يجب اختبار التصميم بشكل جيد.

## ملخص بعبارة واحدة
DragEvent في JavaScript هو حدث يتيح للمطورين تنفيذ تفاعلات السحب والإفلات بشكل سلس وفعال.