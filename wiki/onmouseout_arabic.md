<!--
Meta Description: # حدث onmouseout في JavaScript: الفهم والاستخدام ## ملخص يعتبر حدث `onmouseout` في JavaScript من الأحداث المهمة التي تُستخدم للكشف عن خروج المؤشر من ع...
Meta Keywords: onmouseout, html, javascript, width, استخدام
-->

# حدث onmouseout في JavaScript: الفهم والاستخدام

## ملخص
يعتبر حدث `onmouseout` في JavaScript من الأحداث المهمة التي تُستخدم للكشف عن خروج المؤشر من عنصر معين في الصفحة. يُساعد هذا الحدث في تحسين التفاعل بين المستخدم والواجهة، مما يتيح إمكانية إضافة تأثيرات تفاعلية على العناصر.

## الوثائق
يتم استخدام حدث `onmouseout` عندما يغادر مؤشر الفأرة عنصرًا معينًا. يمكن ربطه بالعناصر في HTML مثل الأزرار، الصور، أو أي عنصر آخر يحتاج إلى تفاعل. عند تنفيذ هذا الحدث، يمكن تنفيذ دالة معينة أو مجموعة من التعليمات البرمجية.

### الاستخدام
يمكن استخدام `onmouseout` مباشرة في HTML أو عبر JavaScript. إليك كيفية استخدامه:

### في HTML:
```html
<div onmouseout="myFunction()">مرر الماوس هنا لمشاهدة التأثير</div>
```

### في JavaScript:
```javascript
const myElement = document.getElementById("myElement");
myElement.onmouseout = function() {
    console.log("المؤشر خرج من العنصر");
};
```

## أمثلة
### مثال 1: تغيير لون النص عند الخروج
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال onmouseout</title>
    <style>
        #myDiv {
            width: 200px;
            height: 100px;
            background-color: lightblue;
            text-align: center;
            line-height: 100px;
            font-size: 20px;
        }
    </style>
</head>
<body>
    <div id="myDiv" onmouseout="this.style.color='black'">مرر الماوس هنا</div>
    
    <script>
        const myDiv = document.getElementById("myDiv");
        myDiv.onmouseover = function() {
            this.style.color = 'red';
        };
    </script>
</body>
</html>
```

### مثال 2: إخفاء صورة عند الخروج
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال onmouseout</title>
</head>
<body>
    <img id="myImage" src="image.jpg" alt="صورة" width="300" onmouseout="this.style.display='none'">
    <p>مرر الماوس عن الصورة ثم اخرج منها.</p>
</body>
</html>
```

## الشرح
### الأخطاء الشائعة
- **عدم الربط الصحيح**: إذا لم يتم ربط الحدث بشكل صحيح مع العنصر، فلن يتم تنفيذه. تأكد من أن العنصر موجود في DOM عندما يتم ربط الحدث.
- **الأداء**: يمكن أن يتسبب استخدام `onmouseout` في بعض الأحيان في أداء غير جيد إذا تم استخدامه على عناصر كبيرة أو مع وظائف معقدة، لذا يُفضل استخدامه بحذر.

### ملاحظات إضافية
- تأكد من استخدام `onmouseleave` إذا كنت تريد تجاهل الأحداث التي تحدث على العناصر الفرعية للعنصر المستهدف. 
- يمكن استخدام `event.relatedTarget` للتحقق من العنصر الذي تم الانتقال إليه.

## ملخص بجملة واحدة
يعتبر حدث `onmouseout` في JavaScript أداة فعالة للكشف عن خروج المؤشر من عنصر، مما يتيح تحسين التفاعل في واجهة المستخدم.