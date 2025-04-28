<!--
Meta Description: # حدث SubmitEvent في جافا سكريبت: الدليل الشامل ## ملخص حدث `SubmitEvent` في جافا سكريبت هو حدث يُستخدم للإشارة إلى أن نموذجًا (Form) قد تم إرساله. يت...
Meta Keywords: submitevent, form, إرسال, event, حدث
-->

# حدث SubmitEvent في جافا سكريبت: الدليل الشامل

## ملخص
حدث `SubmitEvent` في جافا سكريبت هو حدث يُستخدم للإشارة إلى أن نموذجًا (Form) قد تم إرساله. يتم استخدامه عادةً في سياقات النماذج لتسهيل معالجة البيانات قبل أو بعد إرسال النموذج.

## الوثائق
### الغرض
`SubmitEvent` هو نوع خاص من الأحداث يُفعل عند إرسال نموذج. يُمكن استخدامه للتعامل مع البيانات المُدخلة قبل إرسالها إلى الخادم أو لتنفيذ إجراءات معينة عند إرسال النموذج.

### الاستخدام
يتم استخدام حدث `SubmitEvent` عادةً مع النماذج في HTML. يمكن التقاط هذا الحدث باستخدام مراكز الأحداث (Event listeners) لتطبيق وظائف معينة مثل التحقق من صحة البيانات أو منع الإرسال في حالة وجود أخطاء.

### التفاصيل
يمكن أن يتم إنشاء `SubmitEvent` باستخدام البنية التالية:

```javascript
const event = new SubmitEvent(type, eventInit);
```

- **type**: نوع الحدث (عادةً "submit").
- **eventInit**: كائن اختياري يحتوي على إعدادات إضافية للحدث مثل `bubbles` و`cancelable`.

### كيفية التعامل مع حدث SubmitEvent
لتعريف حدث `SubmitEvent`، يمكن استخدام الكود التالي:

```javascript
const form = document.querySelector('form');

form.addEventListener('submit', function(event) {
    // منع الإرسال الافتراضي للنموذج
    event.preventDefault();
    console.log('تم إرسال النموذج!');
});
```

## أمثلة
### مثال 1: التعامل مع إرسال نموذج بسيط

```html
<form id="myForm">
    <input type="text" name="username" required>
    <button type="submit">إرسال</button>
</form>

<script>
    const form = document.getElementById('myForm');
    form.addEventListener('submit', function(event) {
        event.preventDefault(); // منع الإرسال
        console.log('تم إرسال النموذج بنجاح!');
    });
</script>
```

### مثال 2: استخدام SubmitEvent مع بيانات إضافية

```html
<form id="myForm">
    <input type="text" name="username" required>
    <button type="submit">إرسال</button>
</form>

<script>
    const form = document.getElementById('myForm');

    form.addEventListener('submit', function(event) {
        event.preventDefault(); // منع الإرسال

        const submitEvent = new SubmitEvent('submit', {
            bubbles: true,
            cancelable: true
        });

        // يمكنك التعامل مع البيانات هنا
        console.log('تم إنشاء حدث SubmitEvent:', submitEvent);
    });
</script>
```

## الشرح
### المزالق الشائعة
1. **عدم منع الإرسال الافتراضي**: إذا لم يتم استدعاء `event.preventDefault()`، سيتم إرسال النموذج إلى الخادم، مما قد يؤدي إلى إعادة تحميل الصفحة.
2. **عدم التحقق من صحة البيانات**: تأكد من التحقق من صحة البيانات قبل إرسال النموذج لتفادي الأخطاء.
3. **استخدام SubmitEvent في بيئات غير متوافقة**: تأكد من أن المتصفح يدعم `SubmitEvent`، حيث قد لا تتوفر بعض الميزات في المتصفحات القديمة.

### ملاحظات إضافية
- يمكن استخدام `SubmitEvent` في التطبيقات التي تعتمد على JavaScript بشكل كبير مثل التطبيقات أحادية الصفحة (SPA).
- يجب الانتباه إلى أن `SubmitEvent` ليس مدعومًا في جميع المتصفحات، لذا تحقق من التوافق عند تطبيقه.

## ملخص من سطر واحد
حدث `SubmitEvent` في جافا سكريبت يشير إلى إرسال نموذج ويتيح لك تنفيذ إجراءات مخصصة قبل أو بعد الإرسال.