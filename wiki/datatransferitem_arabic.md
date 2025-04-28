<!--
Meta Description: # DataTransferItem في JavaScript: دليل شامل ## ملخص DataTransferItem هو كائن يُستخدم في واجهة برمجة التطبيقات الخاصة بنقل البيانات (Data Transfer API)...
Meta Keywords: datatransferitem, كائن, مثل, event, item
-->

# DataTransferItem في JavaScript: دليل شامل

## ملخص
DataTransferItem هو كائن يُستخدم في واجهة برمجة التطبيقات الخاصة بنقل البيانات (Data Transfer API) في متصفح الويب، حيث يوفر معلومات حول العناصر التي تم نقلها أو سحبها.

## الوثائق
### الغرض
يُستخدم كائن DataTransferItem لتوفير تفاصيل حول العناصر المُضافة إلى كائن DataTransfer، مثل الملفات والنصوص. يسمح للمطورين بمعالجة البيانات المرسلة عبر عمليات السحب والإفلات.

### الاستخدام
يمكن الوصول إلى كائن DataTransferItem من خلال كائن DataTransfer، والذي يتم إنشاؤه أثناء أحداث السحب (drag events). يتم استخدامه عادة في أحداث مثل `dragstart` و `drop`.

### التفاصيل
- **الخصائص**: يحتوي DataTransferItem على خصائص مثل `kind` (نوع العنصر، مثل ملف أو نص) و `type` (نوع MIME للبيانات).
- **الطرق**: يمكن استخدام الطرق مثل `getAsFile()` للحصول على ملف، أو `getAsString()` للحصول على نص.

## الأمثلة
### مثال أساسي لاستخدام DataTransferItem
```javascript
document.addEventListener('dragover', function(event) {
    event.preventDefault();
});

document.addEventListener('drop', function(event) {
    event.preventDefault();
    const items = event.dataTransfer.items;
    
    for (let i = 0; i < items.length; i++) {
        const item = items[i];
        
        if (item.kind === 'file') {
            const file = item.getAsFile();
            console.log('File name: ' + file.name);
        } else if (item.kind === 'string') {
            item.getAsString(function(text) {
                console.log('Dropped text: ' + text);
            });
        }
    }
});
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام `event.preventDefault()`**: يجب استخدام هذه الدالة لمنع السلوك الافتراضي للمتصفح أثناء عمليات السحب والإفلات.
- **عدم التحقق من نوع العنصر**: من الضروري التحقق من نوع العنصر (مثل ملف أو نص) قبل محاولة معالجته، لتجنب الأخطاء.

### ملاحظات إضافية
- يُفضل استخدام DataTransferItem في تطبيقات الويب التفاعلية التي تتطلب سحب وإفلات البيانات.
- تأكد من معالجة جميع أنواع البيانات بشكل صحيح لتجنب أي مشكلات في الأداء.

## ملخص جملة واحدة
DataTransferItem هو كائن في JavaScript يُستخدم لتوفير معلومات حول العناصر المُضافة إلى كائن DataTransfer أثناء عمليات السحب والإفلات.