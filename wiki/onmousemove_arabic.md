<!--
Meta Description: # استخدام "onmousemove" في JavaScript: دليلك الشامل ## الملخص تعتبر خاصية "onmousemove" في JavaScript حدثًا يتيح للمطورين تتبع حركة مؤشر الماوس على صف...
Meta Keywords: onmousemove, html, الماوس, event, javascript
-->

# استخدام "onmousemove" في JavaScript: دليلك الشامل

## الملخص
تعتبر خاصية "onmousemove" في JavaScript حدثًا يتيح للمطورين تتبع حركة مؤشر الماوس على صفحة الويب. يُستخدم هذا الحدث لتوفير تفاعلات ديناميكية وتجارب مستخدم محسّنة.

## التوثيق
### الغرض
"onmousemove" هو حدث يُستخدم في JavaScript لتحديد موقع مؤشر الماوس على الشاشة. يتم تفعيله في كل مرة يتحرك فيها الماوس داخل عنصر معين. يمكن استخدامه لإجراء عمليات مثل تغيير محتوى الصفحة، أو تحريك عناصر، أو تفاعل مع المستخدم.

### الاستخدام
يمكن استخدام "onmousemove" بعدة طرق، لكن الطريقة الأكثر شيوعًا هي من خلال إضافة مستمع للحدث إلى عنصر HTML. يمكن القيام بذلك باستخدام خاصية HTML مباشرة أو عبر JavaScript.

#### الصيغة الأساسية:
```javascript
element.onmousemove = function(event) {
    // كود يتم تنفيذه عند تحريك الماوس
};
```

### تفاصيل
- **العنصر**: يمكن تطبيق "onmousemove" على أي عنصر HTML مثل `<div>`, `<canvas>`, أو `<body>`.
- **الكائن event**: يحتوي الكائن event على معلومات حول الحدث، بما في ذلك موقع الماوس على الشاشة.
- **الأداء**: ينبغي الحذر عند استخدام "onmousemove" لأنه يمكن أن يؤدي إلى استدعاءات كثيرة جدًا، مما يؤثر على أداء الصفحة.

## الأمثلة
### مثال 1: تغيير نص عند تحريك الماوس
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال onmousemove</title>
</head>
<body>
    <h1 id="text">حرّك الماوس هنا</h1>
    <script>
        const textElement = document.getElementById('text');
        document.onmousemove = function(event) {
            textElement.innerText = `X: ${event.clientX}, Y: ${event.clientY}`;
        };
    </script>
</body>
</html>
```

### مثال 2: تغيير لون الخلفية
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تغيير لون الخلفية</title>
</head>
<body>
    <div style="height: 100vh; text-align: center; line-height: 100vh;">
        حرّك الماوس داخل هذا القسم
    </div>
    <script>
        document.onmousemove = function(event) {
            document.body.style.backgroundColor = `rgb(${event.clientX % 255}, ${event.clientY % 255}, 150)`;
        };
    </script>
</body>
</html>
```

## الشرح
### الأخطاء الشائعة
- **الأداء**: إذا تم تنفيذ عمليات ثقيلة داخل حدث "onmousemove"، فقد يتسبب ذلك في بطء الصفحة. يُفضل استخدام تقنيات مثل "throttling" أو "debouncing" لتقليل عدد مرات استدعاء الدالة.
- **تحديد العنصر**: تأكد من أن العنصر الذي تنوي استخدامه يدعم هذا الحدث؛ ليس كل العناصر تدعم "onmousemove".
- **تجاهل الأحداث الأخرى**: تأكد من معالجة الأحداث المختلفة مثل "onmouseleave" أو "onmouseenter" إذا كنت بحاجة إلى تفاعلات أكثر تعقيدًا.

## ملخص جملة واحدة
خاصية "onmousemove" في JavaScript تسمح بتتبع حركة الماوس داخل العناصر، مما يتيح تفاعلات ديناميكية مع المستخدم.