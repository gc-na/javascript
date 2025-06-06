<!--
Meta Description: # onauxclick في JavaScript: دليل شامل ## ملخص `onauxclick` هو حدث في JavaScript يُستخدم لمعالجة نقرات الفأرة عند استخدام الأزرار الإضافية، مثل الأزرار...
Meta Keywords: onauxclick, الأزرار, javascript, حدث, ستخدم
-->

# onauxclick في JavaScript: دليل شامل

## ملخص
`onauxclick` هو حدث في JavaScript يُستخدم لمعالجة نقرات الفأرة عند استخدام الأزرار الإضافية، مثل الأزرار التي تُستخدم في الماوسات المتقدمة (مثل زر العجلة أو الأزرار الجانبية).

## الوثائق
### الغرض
يُستخدم حدث `onauxclick` للاستجابة لنقرات الأزرار الإضافية في الماوس، مما يوفر للمطورين وسيلة للتفاعل مع واجهات المستخدم بطريقة أكثر تفاعلية.

### الاستخدام
يمكنك إضافة حدث `onauxclick` إلى أي عنصر HTML، مثل الأزرار أو الصور، باستخدام JavaScript أو مباشرة في HTML. 

#### التركيب
```html
<element onauxclick="functionName(event)">...</element>
```

أو باستخدام JavaScript:
```javascript
element.addEventListener('auxclick', function(event) {
    // معالجة الحدث
});
```

### التفاصيل
- **الأزرار المدعومة**: يُستخدم `onauxclick` مع أي من الأزرار الإضافية للماوس، مثل الزر الأوسط (العجلة) أو الأزرار الجانبية.
- **الحدث**: يُعطي `onauxclick` كائن الحدث `event` الذي يحتوي على معلومات حول النقر، مثل نوع الزر الذي تم الضغط عليه.
- **التوافق**: يدعم معظم المتصفحات الحديثة، لكن يُفضل التحقق من التوافق مع المتصفح المستهدف.

## أمثلة
### مثال 1: استخدام `onauxclick` مع زر
```html
<button onauxclick="alert('تم النقر على الزر باستخدام زر إضافي!')">انقر هنا</button>
```

### مثال 2: إضافة حدث باستخدام JavaScript
```html
<button id="myButton">انقر هنا</button>

<script>
    document.getElementById('myButton').addEventListener('auxclick', function(event) {
        alert('تم النقر باستخدام زر إضافي: ' + event.button);
    });
</script>
```

## الشرح
### المشاكل الشائعة
- **عدم الاستجابة**: قد لا تعمل `onauxclick` كما هو متوقع على بعض الأجهزة أو المتصفحات التي لا تدعم الأزرار الإضافية للماوس.
- **عدم التوافق**: تحقق من أن المتصفح الذي تستخدمه يدعم هذا الحدث، حيث قد تكون هناك اختلافات في التنفيذ.

### ملاحظات إضافية
- يُفضل استخدام `onmousedown` أو `onclick` مع الأحداث الأكثر شيوعاً، حيث يُعتبر `onauxclick` أقل استخدامًا.
- تأكد من اختبار تطبيقك على عدة أنواع من الماوسات للتأكد من عمل الحدث كما هو متوقع.

## ملخص جملة واحدة
`onauxclick` هو حدث JavaScript يُستخدم للاستجابة لنقرات الأزرار الإضافية في الماوس، مما يُعزز تفاعلية واجهات المستخدم.