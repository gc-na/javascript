<!--
Meta Description: # "onhashchange" في جافا سكريبت: معالجة تغييرات عنوان URL ## ملخص تعتبر خاصية `onhashchange` في جافا سكريبت آلية فعالة للتفاعل مع تغييرات جزء الهاش (#...
Meta Keywords: onhashchange, الهاش, window, hash, location
-->

# "onhashchange" في جافا سكريبت: معالجة تغييرات عنوان URL

## ملخص
تعتبر خاصية `onhashchange` في جافا سكريبت آلية فعالة للتفاعل مع تغييرات جزء الهاش (#) في عنوان URL. تُستخدم هذه الخاصية للاستجابة لتغييرات الهاش في الصفحة دون الحاجة إلى إعادة تحميلها، مما يُساهم في تحسين تجربة المستخدم في التطبيقات ذات الصفحة الواحدة (SPA).

## الوثائق
تُعرّف خاصية `onhashchange` كحدث يتم تفعيله عندما يتغير جزء الهاش في عنوان URL للصفحة. يمكن استخدامها لتشغيل دالة معينة في كل مرة يتغير فيها الهاش، مما يُساعد في إدارة حالة التطبيق أو تغيير المحتوى المعروض للمستخدم.

### الغرض
- استجابة فورية لتغييرات الهاش.
- تعزيز التفاعل وتحسين تجربة المستخدم.
- تطبيق أساليب برمجة SPA.

### الاستخدام
يمكن استخدام `onhashchange` عن طريق تعيين دالة إلى الخاصية `window.onhashchange`. إليك كيفية القيام بذلك:

```javascript
window.onhashchange = function() {
    console.log("تم تغيير الهاش إلى: " + window.location.hash);
};
```

### التفاصيل
- يتم تفعيل الحدث `onhashchange` عندما يتم تغيير الهاش في URL سواءً عن طريق استخدام `history.pushState` أو `history.replaceState` أو عن طريق تعديل `window.location.hash` مباشرة.
- يجب ملاحظة أن هذا الحدث لا يتم تفعيله عند تحميل الصفحة لأول مرة، وإنما فقط عند تغييرات لاحقة.
- يمكن استخدام `window.location.hash` للحصول على القيمة الحالية للهاش.

## أمثلة
### مثال أساسي
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <title>مثال onhashchange</title>
    <script>
        window.onhashchange = function() {
            document.getElementById("output").innerText = "الهاش الحالي: " + window.location.hash;
        };
    </script>
</head>
<body>
    <h1>تغيير الهاش</h1>
    <div id="output">الهاش الحالي: لا شيء</div>
    <a href="#section1">الانتقال إلى القسم 1</a>
    <a href="#section2">الانتقال إلى القسم 2</a>
</body>
</html>
```

### مثال متقدم
```javascript
let data = {
    section1: "محتوى القسم 1",
    section2: "محتوى القسم 2"
};

window.onhashchange = function() {
    let hash = window.location.hash.substring(1); // إزالة علامة الـ #
    document.getElementById("content").innerText = data[hash] || "المحتوى غير متوفر";
};

// تعيين قيمة افتراضية عند تحميل الصفحة
window.onload = function() {
    if (!window.location.hash) {
        window.location.hash = "section1"; // تعيين الهاش الافتراضي
    }
};
```

## الشرح
### المشاكل الشائعة
- **عدم التفعيل عند التحميل الأول**: يجب أن تكون واعيًا أن `onhashchange` لا يعمل عند تحميل الصفحة لأول مرة، بل يتفاعل فقط مع التغييرات اللاحقة.
- **عدم دعم بعض المتصفحات القديمة**: تأكد من اختبار الكود في المتصفحات التي تنوي دعمها، حيث أن بعض المتصفحات القديمة قد لا تدعم `onhashchange`.

### ملاحظات إضافية
- يُفضل استخدام `window.location.hash` مع `onhashchange` لضمان التوافق والمرونة.
- تأكد من معالجة أي حالات خاصة أو استثناءات قد تنشأ عند التعامل مع الهاش.

## ملخص من سطر واحد
تتيح خاصية `onhashchange` في جافا سكريبت معالجة تغييرات الهاش في عنوان URL بسهولة، مما يُحسن من تفاعل المستخدم مع التطبيق.