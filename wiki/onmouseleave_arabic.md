<!--
Meta Description: # حدث onmouseleave في JavaScript: فهم وتطبيق ## ملخص حدث `onmouseleave` هو حدث في JavaScript يُستخدم للكشف عن متى يترك مؤشر الفأرة عنصرًا معينًا في صف...
Meta Keywords: onmouseleave, حدث, javascript, div, عنصر
-->

# حدث onmouseleave في JavaScript: فهم وتطبيق

## ملخص
حدث `onmouseleave` هو حدث في JavaScript يُستخدم للكشف عن متى يترك مؤشر الفأرة عنصرًا معينًا في صفحة الويب. يُعتبر هذا الحدث جزءًا من الأحداث المتعلقة بالفأرة في DOM (نموذج كائن المستند).

## الوثائق
يهدف حدث `onmouseleave` إلى تحسين تفاعل المستخدم على صفحات الويب من خلال استجابة فورية عندما يغادر المستخدم عنصرًا معينًا. يمكن استخدام هذا الحدث لإجراء تغييرات مرئية، مثل تغيير لون الخلفية أو إخفاء الاقتراحات.

### الاستخدام
يمكن إضافة حدث `onmouseleave` إلى أي عنصر HTML. يتم ذلك عادةً عبر خاصية `onmouseleave` في JavaScript أو من خلال إضافة مستمع حدث باستخدام `addEventListener`.

#### الصيغة الأساسية
```javascript
element.onmouseleave = function() {
    // كود لتشغيله عند مغادرة المؤشر العنصر
};
```

أو باستخدام `addEventListener`:
```javascript
element.addEventListener('mouseleave', function() {
    // كود لتشغيله عند مغادرة المؤشر العنصر
});
```

## أمثلة
### مثال 1: تغيير لون الخلفية
```html
<div id="myDiv" style="width: 200px; height: 200px; background-color: blue;">
    مرر الفأرة فوقي
</div>

<script>
    var div = document.getElementById('myDiv');

    div.onmouseleave = function() {
        div.style.backgroundColor = 'red';
    };
</script>
```

### مثال 2: إخفاء نص
```html
<p id="myText">هذا نص سيختفي عند مغادرة المؤشر.</p>

<script>
    var text = document.getElementById('myText');

    text.onmouseleave = function() {
        text.style.display = 'none';
    };
</script>
```

## الشرح
### المشكلات الشائعة
- **تداخل الأحداث**: إذا كان لديك أحداث أخرى متعلقة بالفأرة مثل `onmouseenter` أو `onmouseover`، قد يؤدي ذلك إلى سلوك غير متوقع. تأكد من التعامل مع الأحداث بطريقة مناسبة.
- **أداء الصفحات**: تجنب إضافة العديد من مستمعي الأحداث على عناصر متعددة في نفس الوقت، حيث يمكن أن يؤثر ذلك على أداء الصفحة.

### ملاحظات إضافية
- **دعم المتصفحات**: يعمل `onmouseleave` بشكل جيد في جميع المتصفحات الحديثة، ولكن قد تحتاج إلى التحقق من التوافق مع الإصدارات الأقدم.
- **تأثيرات الرسوم المتحركة**: يمكن دمج `onmouseleave` مع مكتبات الرسوم المتحركة لتحقيق تأثيرات بصرية مذهلة.

## ملخص من جملة واحدة
يعتبر حدث `onmouseleave` في JavaScript وسيلة فعالة للتفاعل مع المستخدم عند مغادرتهم عنصرًا معينًا في صفحة الويب.