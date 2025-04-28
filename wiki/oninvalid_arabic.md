<!--
Meta Description: # التعامل مع الحدث oninvalid في JavaScript ## ملخص يُستخدم الحدث `oninvalid` في JavaScript للتحكم في سلوك العناصر المدخلة (input elements) عندما تفشل ...
Meta Keywords: الحدث, oninvalid, input, javascript, form
-->

# التعامل مع الحدث oninvalid في JavaScript

## ملخص
يُستخدم الحدث `oninvalid` في JavaScript للتحكم في سلوك العناصر المدخلة (input elements) عندما تفشل في التحقق من الصحة (validation). يساعد هذا الحدث المطورين على تقديم تجربة مستخدم أفضل من خلال التعامل مع الأخطاء بشكل مخصص.

## الوثائق
### الغرض
الحدث `oninvalid` يتم تفعيله عندما يقوم المستخدم بإدخال بيانات غير صحيحة في نموذج (form) HTML. يمكن استخدامه لإظهار رسائل خطأ مخصصة أو تنفيذ إجراءات معينة عند فشل تحقق البيانات.

### الاستخدام
يمكن ربط الحدث `oninvalid` بأي عنصر إدخال (input element) في HTML باستخدام خاصية `oninvalid` أو من خلال استخدام `addEventListener` في JavaScript. 

#### الشكل العام:
```html
<input type="text" required oninvalid="handleInvalid()">
```

أو باستخدام JavaScript:
```javascript
document.querySelector('input').addEventListener('invalid', function(event) {
    // التعامل مع الحالة هنا
});
```

### التفاصيل
- **نوع الحدث**: `oninvalid` هو حدث يحدث عندما يفشل عنصر إدخال في التحقق من الصحة.
- **العناصر المدعومة**: يمكن أن يُستخدم مع عناصر الإدخال المختلفة مثل `<input>`, `<textarea>`, و `<select>`.
- **التحقق من الصحة**: يتطلب استخدام `required` أو خصائص التحقق الأخرى مثل `pattern` أو `min` / `max` لتفعيل هذا الحدث.

## الأمثلة
### مثال أساسي
```html
<form>
    <input type="text" required oninvalid="alert('هذا الحقل مطلوب!');">
    <input type="submit" value="إرسال">
</form>
```

### مثال مع JavaScript
```html
<form>
    <input type="email" required id="email">
    <input type="submit" value="إرسال">
</form>

<script>
    document.getElementById('email').addEventListener('invalid', function(event) {
        event.preventDefault(); // منع الإرسال الافتراضي
        alert('يرجى إدخال بريد إلكتروني صالح!');
    });
</script>
```

## الشرح
### المشاكل الشائعة
- **عدم تشغيل الحدث**: إذا لم يتم استخدام خصائص التحقق من الصحة مثل `required`، فلن يتم تفعيل الحدث `oninvalid`.
- **تجاوز السلوك الافتراضي**: عند التعامل مع الحدث، تأكد من استخدام `event.preventDefault()` لمنع السلوك الافتراضي للنموذج إذا كنت ترغب في عرض رسالة مخصصة.

### ملاحظات إضافية
- يعد `oninvalid` جزءًا من واجهة برمجة التطبيقات للتحقق من صحة النموذج (Form Validation API) في HTML5، لذا تأكد من أن المتصفح يدعم هذه الميزة.
- يمكن استخدام `setCustomValidity()` لتخصيص رسالة الخطأ المعروضة عند فشل تحقق البيانات.

## ملخص في جملة
الحدث `oninvalid` في JavaScript يُستخدم لمعالجة الأخطاء في إدخال البيانات، مما يسمح للمطورين بتقديم رسائل مخصصة وتحسين تجربة المستخدم.