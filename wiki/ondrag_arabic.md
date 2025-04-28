<!--
Meta Description: # حدث "ondrag" في JavaScript: الاستخدام والتطبيقات ## ملخص يعتبر حدث "ondrag" في JavaScript من الأحداث الهامة التي تتعلق بسحب العناصر (Drag and Drop) ...
Meta Keywords: ondrag, event, حدث, على, يتم
-->

# حدث "ondrag" في JavaScript: الاستخدام والتطبيقات

## ملخص
يعتبر حدث "ondrag" في JavaScript من الأحداث الهامة التي تتعلق بسحب العناصر (Drag and Drop) في واجهات المستخدم. هذا الحدث يُمكّن المطورين من إضافة تفاعلات ديناميكية لعناصر الويب، مما يسهل على المستخدمين سحب وإفلات المحتويات بطريقة سلسة.

## الوثائق
### الغرض
يستخدم حدث "ondrag" للتفاعل مع عمليات السحب. يتم استدعاء هذا الحدث عندما يبدأ المستخدم في سحب عنصر ما. يُعتبر هذا الحدث جزءًا من واجهة برمجة التطبيقات (API) الخاصة بالسحب والإفلات في HTML5.

### الاستخدام
يمكن استخدام حدث "ondrag" على أي عنصر HTML قابل للسحب. يتم تعيينه عادةً على العنصر الذي تريد أن يتم سحبه. يجب أن يتم تفعيل خاصية `draggable` على العنصر لجعله قابلاً للسحب.

### التفاصيل
- **الخصائص**: 
  - `event.target`: العنصر الذي يتم سحبه.
  - `event.dataTransfer`: كائن يستخدم لنقل البيانات بين العناصر.
  
- **التوافق**: 
  - مدعوم في معظم المتصفحات الحديثة مثل Chrome وFirefox وSafari وEdge.

## أمثلة
### مثال 1: استخدام "ondrag"
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال على حدث ondrag</title>
    <style>
        #drag1 {
            width: 100px;
            height: 100px;
            background-color: blue;
            color: white;
            text-align: center;
            line-height: 100px;
            cursor: move;
        }
    </style>
</head>
<body>

<div id="drag1" draggable="true" ondrag="event.preventDefault(); console.log('يتم سحب العنصر!');">اسحبني</div>

<script>
    document.getElementById("drag1").ondrag = function(event) {
        console.log("تم بدء السحب");
    };
</script>

</body>
</html>
```

### مثال 2: استخدام "ondrag" مع بيانات إضافية
```html
<script>
    document.getElementById("drag1").ondragstart = function(event) {
        event.dataTransfer.setData("text/plain", event.target.id);
    };
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم تعيين خاصية `draggable`**: يجب التأكد من تعيين خاصية `draggable="true"` على العنصر المراد سحبه. بدون هذه الخاصية، لن يعمل الحدث.
- **عدم استخدام `event.preventDefault()`**: في بعض السياقات، قد تحتاج إلى منع السلوك الافتراضي للمتصفح (مثل فتح رابط) باستخدام `event.preventDefault()`.

### ملاحظات إضافية
- يُفضل استخدام أحداث أخرى مثل "ondragover" و "ondrop" جنبًا إلى جنب مع "ondrag" لتحقيق وظائف سحب وإفلات متكاملة.
- يُوصى بتجربة الكود في بيئات مختلفة للتحقق من التوافق.

## ملخص جملة واحدة
حدث "ondrag" في JavaScript يُستخدم لتفعيل تفاعل سحب العناصر في واجهات المستخدم، مما يعزز تجربة المستخدم بشكل كبير.