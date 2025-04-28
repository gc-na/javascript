<!--
Meta Description: # الحدث "onselect" في JavaScript: كيفية استخدامه وتأثيره ## الملخص يعتبر حدث "onselect" في JavaScript من الأحداث المهمة التي تُستخدم للكشف عن تحديد ال...
Meta Keywords: onselect, النص, html, الحدث, حدث
-->

# الحدث "onselect" في JavaScript: كيفية استخدامه وتأثيره

## الملخص
يعتبر حدث "onselect" في JavaScript من الأحداث المهمة التي تُستخدم للكشف عن تحديد النص داخل عناصر الإدخال، مما يتيح للمطورين التفاعل مع المستخدمين بشكل أكثر فعالية.

## الوثائق
### الوصف
يُستخدم حدث "onselect" في JavaScript لاستجابة الأحداث عندما يقوم المستخدم بتحديد نص داخل عنصر إدخال، مثل حقل نصي أو منطقة نصية. يحدث هذا الحدث بعد أن يتم تحديد النص، مما يتيح لك تنفيذ إجراءات معينة بناءً على هذا التحديد.

### الاستخدام
يمكن استخدام حدث "onselect" عن طريق إضافة خاصية `onselect` إلى عنصر الإدخال في HTML. يُمكن ربط هذا الحدث بدالة JavaScript تقوم بتحديد ما يجب أن يحدث عند تحديد النص.

#### التركيب
```html
<input type="text" onselect="yourFunction()">
```

### التفاصيل
- **الدعم:** يتم دعم حدث "onselect" في جميع المتصفحات الحديثة.
- **الاستجابة:** يمكن استخدامه مع عناصر الإدخال (`<input>`، `<textarea>`) فقط.
- **التخصيص:** يمكنك تخصيص وظائف مختلفة بناءً على النص المحدد.

## الأمثلة
### مثال بسيط
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال على onselect</title>
</head>
<body>

<input type="text" onselect="showSelectedText()" value="حدد هذا النص">
<p id="output"></p>

<script>
function showSelectedText() {
    const selectedText = window.getSelection().toString();
    document.getElementById("output").innerText = "النص المحدد: " + selectedText;
}
</script>

</body>
</html>
```

### مثال مع textarea
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال على onselect في textarea</title>
</head>
<body>

<textarea onselect="showSelectedText()" rows="5" cols="30">حدد النص هنا</textarea>
<p id="output"></p>

<script>
function showSelectedText() {
    const selectedText = window.getSelection().toString();
    document.getElementById("output").innerText = "النص المحدد: " + selectedText;
}
</script>

</body>
</html>
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود تحديد**: إذا لم يتم تحديد أي نص عند تنفيذ الحدث، فقد يؤدي ذلك إلى عدم ظهور أي نتيجة.
- **عدم معرفة السياق**: يجب التأكد من أن النص المحدد ينتمي بالفعل إلى العنصر الذي تم تنفيذه عليه الحدث.
  
### ملاحظات إضافية
- قد لا يتم تفعيل الحدث "onselect" في بعض العناصر غير النصية مثل الأزرار أو الروابط.
- يمكن دمج حدث "onselect" مع أحداث أخرى مثل "onclick" أو "onfocus" لتحسين تجربة المستخدم.

## ملخص بجملة واحدة
حدث "onselect" في JavaScript يُستخدم للكشف عن تحديد النص داخل عناصر الإدخال مما يتيح تفاعلات مخصصة مع المستخدم.