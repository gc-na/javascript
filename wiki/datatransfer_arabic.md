<!--
Meta Description: # DataTransfer في جافا سكريبت: إدارة البيانات في عمليات السحب والإفلات ## ملخص `DataTransfer` هو كائن في جافا سكريبت يُستخدم لإدارة البيانات أثناء عمل...
Meta Keywords: البيانات, datatransfer, event, السحب, والإفلات
-->

# DataTransfer في جافا سكريبت: إدارة البيانات في عمليات السحب والإفلات

## ملخص
`DataTransfer` هو كائن في جافا سكريبت يُستخدم لإدارة البيانات أثناء عمليات السحب والإفلات (Drag and Drop) في واجهات المستخدم. يُتيح هذا الكائن للمطورين نقل البيانات بين العناصر المختلفة بطريقة مرنة وسهلة.

## الوثائق
### الغرض
كائن `DataTransfer` يُستخدم لتخزين البيانات التي يتم نقلها خلال عملية السحب والإفلات، مما يُساعد في نقل البيانات بين العناصر المختلفة في واجهة المستخدم.

### الاستخدام
يمكن الوصول إلى كائن `DataTransfer` عبر أحداث السحب والإفلات، مثل `dragstart`, `dragover`, و `drop`. يوفر هذا الكائن عدة خصائص وطرق للتعامل مع البيانات.

### الخصائص
- **dataTransfer.effectAllowed**: تُحدد التأثيرات المسموح بها (مثل `copy`, `move`).
- **dataTransfer.items**: يُمثل قائمة العناصر المنقولة.
- **dataTransfer.setData(format, data)**: تُستخدم لتعيين البيانات بتنسيق معين.
- **dataTransfer.getData(format)**: تُستخدم لاسترجاع البيانات بتنسيق معين.

### الطرق
- `setData(format, data)`: تعيين البيانات بتنسيق محدد.
- `getData(format)`: الحصول على البيانات بتنسيق معين.
- `dropEffect`: تُحدد التأثير الذي يحدث عند إسقاط البيانات.

## أمثلة
### مثال 1: استخدام `setData` و `getData`
```javascript
// إعداد حدث السحب
element.addEventListener('dragstart', function(event) {
    event.dataTransfer.setData('text/plain', 'Hello World');
});

// إعداد حدث الإسقاط
targetElement.addEventListener('drop', function(event) {
    event.preventDefault();
    const data = event.dataTransfer.getData('text/plain');
    console.log(data); // سيعرض "Hello World"
});
```

### مثال 2: تحديد التأثير المسموح
```javascript
element.addEventListener('dragstart', function(event) {
    event.dataTransfer.effectAllowed = 'move';
});
```

## الشرح
### العوائق الشائعة
- **عدم استخدام `event.preventDefault()`**: يجب على المطورين استخدام هذه الطريقة في أحداث إسقاط البيانات لمنع السلوك الافتراضي، مثل فتح الروابط.
- **تنسيقات البيانات**: يجب التأكد من أن التنسيقات المستخدمة في `setData` و `getData` متطابقة؛ مثلاً، إذا قمت بتعيين البيانات بتنسيق `text/plain`، يجب استرجاعها بنفس التنسيق.

### ملاحظات إضافية
- يمكن أن يدعم `DataTransfer` أنواع بيانات متعددة، مثل النصوص والصور والملفات.
- يتم استخدام `DataTransfer` بشكل شائع في تطبيقات الويب التفاعلية لتحسين تجربة المستخدم.

## ملخص جملة واحدة
`DataTransfer` في جافا سكريبت هو كائن مركزي لإدارة البيانات في عمليات السحب والإفلات، مما يُسهل على المطورين التعامل مع نقل البيانات بين العناصر.