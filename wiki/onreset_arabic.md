<!--
Meta Description: # onreset في جافا سكريبت: إعادة تعيين النماذج ## ملخص يُستخدم حدث `onreset` في JavaScript لتعقب وتفعيل إجراءات معينة عند إعادة تعيين نموذج (form) في ص...
Meta Keywords: إعادة, تعيين, onreset, النموذج, form
-->

# onreset في جافا سكريبت: إعادة تعيين النماذج

## ملخص
يُستخدم حدث `onreset` في JavaScript لتعقب وتفعيل إجراءات معينة عند إعادة تعيين نموذج (form) في صفحة الويب. يُعتبر هذا الحدث مفيدًا في التعامل مع نماذج الإدخال، حيث يسمح بتنفيذ تعليمات خاصة عند استعادة النموذج إلى حالته الأصلية.

## الوثائق
### الغرض
`onreset` هو حدث يُطلق عندما يتم استدعاء طريقة `reset()` على نموذج. يتيح للمطورين إمكانية تنفيذ كود JavaScript عند إعادة تعيين النموذج، مما يسهل إدارة التفاعلات الخاصة بالمستخدم.

### الاستخدام
يمكن استخدام `onreset` بشكل مباشر في عنصر النموذج داخل HTML أو من خلال JavaScript. عند استخدامه في HTML، يمكن تعيينه كخاصية للعنصر `<form>`. في JavaScript، يمكن إضافة مستمع للحدث باستخدام `addEventListener`.

#### مثال على استخدام `onreset` في HTML:
```html
<form onreset="myFunction()">
  <input type="text" name="name" placeholder="أدخل اسمك">
  <input type="submit" value="إرسال">
  <input type="reset" value="إعادة تعيين">
</form>
```

#### مثال على استخدام `onreset` في JavaScript:
```javascript
document.querySelector('form').addEventListener('reset', function() {
    alert('تم إعادة تعيين النموذج');
});
```

## أمثلة
### مثال 1: إعادة تعيين النموذج مع رسالة تنبيه
```html
<form id="myForm">
  <input type="text" name="name" placeholder="أدخل اسمك">
  <input type="reset" value="إعادة تعيين">
</form>

<script>
document.getElementById('myForm').onreset = function() {
    alert('تم إعادة تعيين النموذج');
};
</script>
```

### مثال 2: إعادة تعيين النموذج وتحديث واجهة المستخدم
```html
<form id="myForm">
  <input type="text" name="email" placeholder="أدخل بريدك الإلكتروني">
  <input type="reset" value="إعادة تعيين">
</form>

<script>
document.getElementById('myForm').addEventListener('reset', function() {
    document.body.style.backgroundColor = 'white';
});
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم إضافة مستمع الحدث**: قد يؤدي عدم إضافة مستمع لـ `onreset` إلى عدم تنفيذ الكود عند إعادة تعيين النموذج.
- **تجاهل تأثير إعادة تعيين**: يجب الانتباه إلى أن إعادة تعيين النموذج يعيد جميع الحقول إلى القيم الافتراضية، مما قد يتسبب في فقدان بيانات مهمة إن لم يتم حفظها مسبقًا.

### ملاحظات إضافية
- يمكن استخدام `event.preventDefault()` في الحالات التي تحتاج فيها إلى منع إعادة تعيين النموذج عند تنفيذ شروط معينة.
- يعتبر `onreset` مفيدًا بشكل خاص في النماذج التي تحتوي على حقول متعددة وتحتاج إلى تعيينها بسرعة.

## ملخص من سطر واحد
حدث `onreset` في JavaScript يُستخدم لتنفيذ إجراءات معينة عند إعادة تعيين نموذج، مما يسهل إدارة التفاعلات مع المستخدم.