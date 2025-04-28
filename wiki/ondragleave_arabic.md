<!--
Meta Description: # حدث ondragleave في جافا سكريبت: دليل شامل ## ملخص يُستخدم حدث `ondragleave` في جافا سكريبت لاستجابة العناصر عندما يغادر الكائن المسحوب منطقة معينة. ...
Meta Keywords: ondragleave, dropzone, الحدث, حدث, div
-->

# حدث ondragleave في جافا سكريبت: دليل شامل

## ملخص
يُستخدم حدث `ondragleave` في جافا سكريبت لاستجابة العناصر عندما يغادر الكائن المسحوب منطقة معينة. يعد هذا الحدث جزءًا من واجهة سحب وإفلات (Drag and Drop) في متصفح الويب، مما يسمح بتعزيز تفاعلية التطبيقات على الويب.

## الوثائق
### الغرض
يهدف حدث `ondragleave` إلى تفعيل وظيفة معينة عندما يغادر الكائن المسحوب منطقة هدف السحب. يُعد هذا الحدث مفيدًا في تحسين تجربة المستخدم من خلال إظهار استجابة مرئية أو تنفيذ إجراءات محددة بناءً على تفاعل المستخدم.

### الاستخدام
يتم استخدام حدث `ondragleave` مع عناصر HTML مثل `div` أو `section`، ويمكن إضافته باستخدام خاصية HTML أو من خلال JavaScript. يمكن أن يتضمن هذا الحدث وظائف مثل تغيير لون الخلفية أو عرض رسالة توضح أن الكائن لم يعد داخل المنطقة المحددة.

### التفاصيل
- **التوقيع**: `element.ondragleave = function(event) { ... }`
- **المعاملات**:
  - `event`: كائن الحدث الذي يحتوي على معلومات حول الحدث، مثل موقع الماوس والكائنات المعنية.

## أمثلة
### مثال 1: تغيير لون الخلفية عند مغادرة العنصر
```html
<div id="dropZone" style="width: 200px; height: 200px; background-color: lightblue;">
    اسحب هنا
</div>

<script>
    const dropZone = document.getElementById('dropZone');

    dropZone.ondragleave = function() {
        dropZone.style.backgroundColor = 'lightcoral';
    };
</script>
```

### مثال 2: عرض رسالة عند مغادرة العنصر
```html
<div id="dropZone" style="width: 200px; height: 200px; background-color: lightgreen;">
    اسحب هنا
</div>
<p id="message"></p>

<script>
    const dropZone = document.getElementById('dropZone');
    const message = document.getElementById('message');

    dropZone.ondragleave = function() {
        message.textContent = 'لقد غادرت المنطقة!';
    };
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود منطقة هدف مناسبة**: تأكد من أن العنصر الذي ترغب في استخدام `ondragleave` عليه هو عنصر قابل للسحب.
- **عدم التعامل مع الأحداث بشكل صحيح**: تأكد من إضافة وظيفة `ondragleave` بشكل صحيح، وأن العنصر مستعد لاستقبال أحداث السحب.

### ملاحظات إضافية
- يمكن دمج `ondragleave` مع أحداث أخرى مثل `ondragenter` و`ondragover` لتحسين تفاعل المستخدم.
- يعتمد التفاعل على إعدادات المتصفح، لذا من المهم اختبار سلوك الحدث عبر مختلف المتصفحات.

## ملخص بجملة واحدة
يُستخدم حدث `ondragleave` في جافا سكريبت لتفعيل استجابة عند مغادرة كائن مسحوب منطقة هدف السحب.