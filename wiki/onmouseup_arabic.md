<!--
Meta Description: # حدث onmouseup في JavaScript: فهم واستخدام حدث تحرير زر الماوس ## ملخص حدث `onmouseup` في JavaScript هو حدث يُستخدم للتعامل مع تحرير زر الماوس. يتم ت...
Meta Keywords: onmouseup, الماوس, حدث, تحرير, على
-->

# حدث onmouseup في JavaScript: فهم واستخدام حدث تحرير زر الماوس

## ملخص
حدث `onmouseup` في JavaScript هو حدث يُستخدم للتعامل مع تحرير زر الماوس. يتم تفعيله عند رفع زر الماوس بعد الضغط عليه، مما يتيح للمطورين تنفيذ إجراءات معينة بناءً على هذا التفاعل.

## الوثائق
### الغرض
يُستخدم حدث `onmouseup` للتعرف على متى يقوم المستخدم بتحرير زر الماوس. يمكن استخدامه في تطبيقات الويب لتحسين تفاعل المستخدم، مثل تنفيذ مهام معينة عند رفع زر الماوس، مثل إسقاط العناصر أو إنهاء عمليات السحب والإفلات.

### الاستخدام
يتم إضافة حدث `onmouseup` إلى عنصر HTML باستخدام JavaScript أو HTML. يمكن استخدامه مع أي عنصر يمكن التفاعل معه، مثل الأزرار، الصور، أو مناطق معينة في صفحة الويب.

### الصيغة
```javascript
element.onmouseup = function(event) {
    // الكود الذي ينفذ عند تحرير زر الماوس
};
```

### ملاحظات إضافية
- يمكن استخدام `addEventListener` بدلاً من تعيين الحدث مباشرةً، مما يعطي مزيدًا من المرونة.
- يمكن استخدام `event.button` لتحديد أي زر تم تحريره (0: الزر الأيسر، 1: الزر الأوسط، 2: الزر الأيمن).

## الأمثلة
### مثال 1: استخدام onmouseup مع زر
```html
<button id="myButton">اضغط هنا</button>
<script>
    document.getElementById("myButton").onmouseup = function() {
        alert("تم تحرير الزر!");
    };
</script>
```

### مثال 2: استخدام onmouseup مع عنصر صورة
```html
<img id="myImage" src="example.jpg" alt="صورة" style="width:200px;height:200px;">
<script>
    document.getElementById("myImage").onmouseup = function() {
        console.log("تم تحرير زر الماوس على الصورة.");
    };
</script>
```

### مثال 3: استخدام addEventListener
```html
<div id="myDiv" style="width:100px;height:100px;background-color:lightblue;"></div>
<script>
    document.getElementById("myDiv").addEventListener("mouseup", function() {
        console.log("تم تحرير زر الماوس على المربع.");
    });
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم العمل كما هو متوقع**: تأكد من أن العنصر الذي تحاول إضافة حدث `onmouseup` له موجود بالفعل في DOM.
- **تداخل الأحداث**: إذا كان لديك أحداث أخرى مثل `onmousedown` أو `onclick` على نفس العنصر، تأكد من أن هذه الأحداث لا تتداخل أو تؤثر سلبًا على سلوك `onmouseup`.

### ملاحظات إضافية
- يعتبر `onmouseup` جزءًا من مجموعة أحداث الماوس، التي تشمل أيضًا `onmousedown` و`onclick`.
- تأكد من اختبار سلوك `onmouseup` عبر مختلف المتصفحات لضمان توافقية عالية.

## ملخص جملة واحدة
يُستخدم حدث `onmouseup` في JavaScript للتفاعل مع تحرير زر الماوس، مما يسمح بتنفيذ إجراءات محددة استجابة لتفاعلات المستخدم.