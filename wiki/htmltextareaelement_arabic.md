<!--
Meta Description: # HTMLTextAreaElement في JavaScript: دليل شامل ## ملخص تعتبر HTMLTextAreaElement واجهة برمجية تمثل عنصر النص المتعدد الأسطر (textarea) في HTML، مما يت...
Meta Keywords: textarea, النص, htmltextareaelement, javascript, html
-->

# HTMLTextAreaElement في JavaScript: دليل شامل

## ملخص
تعتبر HTMLTextAreaElement واجهة برمجية تمثل عنصر النص المتعدد الأسطر (textarea) في HTML، مما يتيح للمطورين التعامل مع محتويات هذا العنصر عبر JavaScript بشكل سهل وفعال.

## الوثائق
### الغرض
HTMLTextAreaElement هو عنصر HTML يُستخدم لإنشاء منطقة نص متعددة الأسطر، حيث يمكن للمستخدم إدخال نص طويل، مثل التعليقات أو الملاحظات.

### الاستخدام
يمكن الوصول إلى HTMLTextAreaElement في JavaScript عبر DOM باستخدام `document.getElementById` أو `document.querySelector` أو أي طرق أخرى للوصول إلى العناصر في الوثيقة. 

### التفاصيل
- **الخصائص**: 
  - `value`: تمثل النص المدخل في textarea.
  - `rows`: تحدد عدد الصفوف (الأسطر) الظاهرة.
  - `cols`: تحدد عدد الأعمدة (الأحرف) الظاهرة.
  - `placeholder`: نص تلميحي يظهر داخل textarea عندما يكون فارغًا.
  - `disabled`: تحدد ما إذا كان العنصر معطلاً أم لا.
  
- **الطرق**: 
  - `select()`: يحدد النص داخل textarea.
  - `setCustomValidity()`: يسمح بتحديد رسالة خطأ مخصصة للتحقق من صحة الإدخال.

## أمثلة
### إنشاء textarea والوصول إلى محتواه
```html
<textarea id="myTextarea" rows="4" cols="50" placeholder="اكتب هنا..."></textarea>
<script>
    const textarea = document.getElementById('myTextarea');
    textarea.value = "مرحبا بالعالم!";
    console.log(textarea.value); // سيطبع "مرحبا بالعالم!"
</script>
```

### استخدام select لتحديد النص
```html
<textarea id="myTextarea" rows="4" cols="50">حدد هذا النص!</textarea>
<button onclick="selectText()">تحديد النص</button>
<script>
    function selectText() {
        const textarea = document.getElementById('myTextarea');
        textarea.select();
    }
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من وجود العنصر**: تأكد من أن العنصر موجود في DOM قبل محاولة الوصول إليه عبر JavaScript.
- **عدم التعامل مع الأحداث**: استخدام الأحداث مثل `oninput` أو `onchange` بشكل صحيح لضمان الاستجابة للتغييرات التي يجريها المستخدم.

### ملاحظات إضافية
- يمكن أن يحتوي textarea على خصائص CSS مخصصة لضبط الشكل والمظهر.
- تأكد من استخدام `rows` و`cols` بشكل صحيح لضبط حجم textarea وفق احتياجاتك.

## ملخص من جملة واحدة
HTMLTextAreaElement هو واجهة برمجية تتيح للمطورين التحكم في عناصر textarea في HTML بسهولة عبر JavaScript.