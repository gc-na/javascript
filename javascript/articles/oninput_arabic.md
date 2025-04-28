<!--
Meta Description: # الحدث oninput في جافا سكريبت: دليل شامل ## ملخص يعتبر الحدث `oninput` في جافا سكريبت من الأحداث المهمة التي تُستخدم للتفاعل مع مدخلات المستخدم في عن...
Meta Keywords: oninput, الحدث, مثل, يتم, input
-->

# الحدث oninput في جافا سكريبت: دليل شامل

## ملخص
يعتبر الحدث `oninput` في جافا سكريبت من الأحداث المهمة التي تُستخدم للتفاعل مع مدخلات المستخدم في عناصر النماذج مثل حقل النص، مما يتيح تحديثات فورية عند إدخال البيانات.

## التوثيق
### الهدف
الحدث `oninput` يُستخدم للاستجابة للتغييرات التي تطرأ على عناصر الإدخال، مثل حقول النصوص، حيث يتم تنفيذه في كل مرة يتم فيها تغيير محتوى الحقل.

### الاستخدام
يتم استخدام `oninput` عن طريق إضافته كخاصية لعناصر الإدخال في HTML أو عبر JavaScript. يُمكن تعيين دالة معينة للتنفيذ عند حدوث هذا الحدث.

#### الصيغة الأساسية:
```html
<input type="text" oninput="myFunction()">
```

#### عبر JavaScript:
```javascript
const inputField = document.getElementById('myInput');
inputField.oninput = function() {
    // الكود الذي سيتم تنفيذه
};
```

### التفاصيل
- **الحدث**: `oninput` يُفعّل في كل مرة يتم فيها إدخال أو حذف نص، مما يجعله مثالياً لتطبيقات مثل البحث الفوري أو التحقق من صحة البيانات.
- **الدعم**: مدعوم في جميع المتصفحات الحديثة.
- **الفرق مع الأحداث الأخرى**: يختلف `oninput` عن `onchange` حيث أن الأخير يُنفذ فقط بعد فقدان التركيز عن العنصر، بينما الأول يُنفذ فوراً مع كل إدخال.

## الأمثلة
### مثال 1: استخدام `oninput` مع حقل نصي
```html
<input type="text" id="myInput" oninput="updateText()">
<p id="output"></p>

<script>
function updateText() {
    const input = document.getElementById('myInput').value;
    document.getElementById('output').innerText = input;
}
</script>
```

### مثال 2: التحقق من صحة الإدخال
```html
<input type="text" id="emailInput" oninput="validateEmail()">
<p id="emailMessage"></p>

<script>
function validateEmail() {
    const emailInput = document.getElementById('emailInput').value;
    const message = document.getElementById('emailMessage');
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

    if (regex.test(emailInput)) {
        message.innerText = 'البريد الإلكتروني صحيح';
    } else {
        message.innerText = 'يرجى إدخال بريد إلكتروني صحيح';
    }
}
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم التفاعل مع العناصر المناسبة**: تأكد من أنك تستخدم `oninput` مع عناصر الإدخال فقط مثل `<input>` و`<textarea>`.
- **تجاوز الأداء**: عند استخدام `oninput` في الحقول التي تستدعي عمليات ثقيلة، مثل استعلامات الشبكة، قد يؤدي ذلك إلى أداء ضعيف. استعمل تقنيات مثل "التأخير" لتقليل عدد الاستدعاءات.

### ملاحظات إضافية
- يتم تنفيذ `oninput` في كل مرة يتم فيها إدخال شيء جديد، لذا تأكد من كتابة الكود بطريقة تحافظ على الأداء.
- فكر في استخدام `debounce` إذا كنت تستخدم `oninput` في تطبيقات تعتمد على الشبكة، لتقليل عدد الطلبات.

## ملخص جملة واحدة
يعتبر الحدث `oninput` في جافا سكريبت وسيلة فعالة للاستجابة الفورية لتغيرات مدخلات المستخدم في عناصر النماذج.