<!--
Meta Description: # HTMLInputElement في JavaScript: كل ما تحتاج معرفته ## الملخص HTMLInputElement هو واجهة تمثل عنصر الإدخال في مستند HTML، حيث تُستخدم في JavaScript لل...
Meta Keywords: الإدخال, htmlinputelement, javascript, document, checkbox
-->

# HTMLInputElement في JavaScript: كل ما تحتاج معرفته

## الملخص
HTMLInputElement هو واجهة تمثل عنصر الإدخال في مستند HTML، حيث تُستخدم في JavaScript للتفاعل مع حقول الإدخال المختلفة مثل النصوص، الأزرار، والاختيارات.

## الوثائق
### الغرض
HTMLInputElement هو جزء من DOM (Document Object Model) يُستخدم لتحديد خصائص وسلوك عناصر الإدخال في مستندات HTML. يتيح لك هذا الكائن التفاعل مع الحقول، قراءة القيم، وتغيير سلوكها.

### الاستخدام
يمكنك الوصول إلى كائن HTMLInputElement عبر استدعاء `document.getElementById` أو `document.querySelector` أو غيرها من طرق البحث عن العناصر. بعد الحصول على الكائن، يمكنك تعديل خصائصه مثل القيمة (value) والنوع (type) والحالة (disabled) وغيرها.

### الخصائص الأساسية
- **value**: تمثل القيمة الحالية لعنصر الإدخال.
- **type**: تحدد نوع الإدخال، مثل "text"، "checkbox"، "radio"، وغيرها.
- **checked**: تُستخدم مع عناصر الإدخال من النوع "checkbox" أو "radio" للتحقق مما إذا كانت مختارة أم لا.
- **disabled**: تعيين هذه الخاصية إلى true يجعل عنصر الإدخال غير قابل للتفاعل.

## الأمثلة
### مثال 1: تغيير قيمة حقل نصي
```javascript
const inputField = document.getElementById('myInput');
inputField.value = 'مرحبا بالعالم';
```

### مثال 2: التحقق من عنصر إدخال checkbox
```javascript
const checkbox = document.getElementById('myCheckbox');
if (checkbox.checked) {
    console.log('تم تحديد المربع');
} else {
    console.log('لم يتم تحديد المربع');
}
```

### مثال 3: تعطيل عنصر إدخال
```javascript
const inputField = document.getElementById('myInput');
inputField.disabled = true; // جعل الحقل غير قابل للتفاعل
```

## الشرح
### الأخطاء الشائعة
- **نسيان إضافة حدث**: قد تنسى إضافة مستمع الحدث (event listener) لتفاعل مع المستخدم.
- **عدم التحقق من الحالة**: عند استخدام عناصر checkbox أو radio، تأكد من التحقق من خاصية `checked` قبل اتخاذ الإجراءات.

### ملاحظات إضافية
- تأكد من أن لديك معرفات عناصر فريدة في HTML لتفادي أي تعارضات.
- قد تختلف خصائص HTMLInputElement باختلاف نوع الإدخال، لذا يجب مراجعة الوثائق لكل نوع.

## ملخص من سطر واحد
HTMLInputElement هو الكائن الذي يمثل عناصر الإدخال في HTML، مما يسمح لك بالتفاعل مع حقول الإدخال بسهولة باستخدام JavaScript.