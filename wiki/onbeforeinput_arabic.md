<!--
Meta Description: # الحدث onbeforeinput في JavaScript: الدليل الشامل ## ملخص يعد الحدث `onbeforeinput` في JavaScript حدثًا مهمًا يُستخدم لتحديد سلوك إدخال المستخدم في ع...
Meta Keywords: onbeforeinput, الحدث, الإدخال, event, يتم
-->

# الحدث onbeforeinput في JavaScript: الدليل الشامل

## ملخص
يعد الحدث `onbeforeinput` في JavaScript حدثًا مهمًا يُستخدم لتحديد سلوك إدخال المستخدم في عناصر النماذج. يتم تفعيله قبل إجراء أي تغييرات في محتوى حقل الإدخال.

## التوثيق
### الغرض
يهدف الحدث `onbeforeinput` إلى توفير وسيلة للمطورين للتفاعل مع إدخالات المستخدم قبل أن يتم تطبيقها على الحقول. يُمكن استخدامه للتحقق من صحة المدخلات أو لتنفيذ إجراءات معينة استنادًا إلى ما يُدخله المستخدم.

### الاستخدام
يتم استخدام `onbeforeinput` في عناصر الإدخال مثل `<input>` و `<textarea>`. يتم تعيينه كخاصية من خصائص العنصر، ويمكن أيضًا استخدامه كحدث في JavaScript.

### التفاصيل
- **الحدث**: `onbeforeinput`
- **التنسيق**: يمكن تعيينه كخاصية مباشرة في العنصر أو عبر `addEventListener`.
- **المدخلات**: يتلقى الحدث كائن الحدث (event object) الذي يحتوي على معلومات حول الإدخال الذي سيتم تطبيقه.

## أمثلة
### المثال 1: استخدام onbeforeinput للتحقق من المدخلات
```html
<input type="text" id="myInput" onbeforeinput="validateInput(event)">
<script>
function validateInput(event) {
    const invalidCharacters = /[^a-zA-Z0-9]/;
    if (invalidCharacters.test(event.data)) {
        event.preventDefault(); // منع الإدخال الغير صالح
    }
}
</script>
```

### المثال 2: استخدام onbeforeinput مع addEventListener
```html
<textarea id="myTextarea"></textarea>
<script>
const textarea = document.getElementById('myTextarea');
textarea.addEventListener('beforeinput', function(event) {
    console.log('تم إدخال البيانات: ', event.data);
});
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم فهم توقيت الحدث**: حيث يتم تفعيل `onbeforeinput` قبل أن يتم إدخال البيانات، لذا يجب الحرص على عدم محاولة الوصول إلى قيمة الإدخال بعد الحدث.
- **تجاهل منع الإدخال**: إذا كان هناك حاجة لمنع الإدخال بناءً على شرط معين، يجب استخدام `event.preventDefault()` بشكل صحيح.

### ملاحظات إضافية
- قد لا يتم دعم `onbeforeinput` في جميع المتصفحات، لذا يُفضل التحقق من توافق المتصفح.
- يمكن استخدام `onbeforeinput` مع الأحداث الأخرى مثل `input` و`change` للحصول على سلوك أكثر تعقيدًا.

## ملخص جملة واحدة
الحدث `onbeforeinput` في JavaScript يُمكن المطورين من التحكم في إدخال المستخدم قبل تطبيقه على حقول الإدخال.