<!--
Meta Description: # حدث ondragover في JavaScript: دليل شامل ## ملخص حدث `ondragover` هو حدث في JavaScript يتم استخدامه في سياق واجهات المستخدم لتحسين تجربة السحب والإفل...
Meta Keywords: event, ondragover, drop, حدث, العنصر
-->

# حدث ondragover في JavaScript: دليل شامل

## ملخص
حدث `ondragover` هو حدث في JavaScript يتم استخدامه في سياق واجهات المستخدم لتحسين تجربة السحب والإفلات (Drag and Drop). يتم تفعيله عندما يتم سحب عنصر ما فوق عنصر آخر.

## الوثائق
### الغرض
يستخدم حدث `ondragover` لتحديد سلوك العنصر المستهدف عند سحب عنصر فوقه. بشكل افتراضي، لا يمكن إسقاط العناصر في متصفح الويب، ولكن يمكن استخدام هذا الحدث لمنع هذا السلوك الافتراضي.

### الاستخدام
يمكن استخدام `ondragover` في عناصر HTML، مثل `<div>` أو `<span>`. يتم تعيين وظيفة JavaScript لهذا الحدث لتحسين تفاعل المستخدم.

### تفاصيل
- **النوع**: حدث DOM
- **الحدث**: يحدث عند سحب عنصر فوق عنصر آخر.
- **السلوك الافتراضي**: يجب منع السلوك الافتراضي للسماح بالإفلات (drop).

### كيفية الاستخدام
لتعريف حدث `ondragover`، يمكنك استخدام الكود التالي:

```html
<div id="drop-zone" ondragover="allowDrop(event)" ondrop="drop(event)">
    اسحب العنصر هنا
</div>
```

وفي ملف JavaScript:

```javascript
function allowDrop(event) {
    event.preventDefault(); // منع السلوك الافتراضي
}

function drop(event) {
    event.preventDefault(); // منع السلوك الافتراضي
    const data = event.dataTransfer.getData("text");
    event.target.appendChild(document.getElementById(data)); // إضافة العنصر المسحوب
}
```

## الأمثلة
### مثال أساسي
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <title>مثال ondragover</title>
    <style>
        #drop-zone {
            width: 300px;
            height: 200px;
            border: 2px dashed #ccc;
            text-align: center;
            line-height: 200px;
            margin: 20px;
        }
    </style>
</head>
<body>

<div id="drop-zone" ondragover="allowDrop(event)" ondrop="drop(event)">
    اسحب العنصر هنا
</div>

<div id="draggable" draggable="true" ondragstart="event.dataTransfer.setData('text', event.target.id)">
    اسحبني
</div>

<script>
function allowDrop(event) {
    event.preventDefault();
}

function drop(event) {
    event.preventDefault();
    const data = event.dataTransfer.getData("text");
    event.target.appendChild(document.getElementById(data));
}
</script>

</body>
</html>
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام `event.preventDefault()`**: قد يؤدي ذلك إلى عدم إمكانية إسقاط العنصر. يجب دائمًا منع السلوك الافتراضي لتمكين وظيفة السحب والإفلات.
- **عدم تحديد العنصر القابل للسحب**: تأكد من أن العنصر الذي تريد سحبه لديه الخاصية `draggable` مضبوطة على `true`.

### ملاحظات إضافية
- تأكد من أن الأحداث الأخرى مثل `ondrop` و`ondragenter` و`ondragleave` مهيأة بشكل صحيح لتحقيق أفضل تجربة للمستخدم.
- يمكن استخدام `ondragover` مع أي عنصر HTML وليس فقط العناصر القابلة للإفلات.

## ملخص بسيط
حدث `ondragover` في JavaScript يسمح لك بتحديد سلوك العناصر عندما يتم سحب عناصر أخرى فوقها، مما يعزز تجربة السحب والإفلات في واجهات المستخدم.