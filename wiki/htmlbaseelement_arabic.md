<!--
Meta Description: # HTMLBaseElement في JavaScript: دليل شامل ## ملخص تعتبر `HTMLBaseElement` واحدة من العناصر الأساسية في HTML، حيث تُستخدم لتحديد قاعدة URL للروابط الن...
Meta Keywords: html, href, base, الروابط, head
-->

# HTMLBaseElement في JavaScript: دليل شامل

## ملخص
تعتبر `HTMLBaseElement` واحدة من العناصر الأساسية في HTML، حيث تُستخدم لتحديد قاعدة URL للروابط النسبية في المستندات. تتيح هذه الميزة للمطورين التحكم في كيفية ارتباط الموارد بالمستندات، مما يسهل عملية إدارة الروابط.

## الوثائق
### الغرض
`HTMLBaseElement` هي واجهة تمثل عنصر `<base>` في HTML. يُستخدم هذا العنصر لتحديد عنوان أساسي يُستخدم كمرجع للروابط النسبية الموجودة في الوثيقة.

### الاستخدام
يتم استخدام عنصر `<base>` داخل قسم `<head>` من HTML. يمكن أن يحتوي على خاصيتين رئيسيتين:
- `href`: تحدد URL الأساسية المستخدمة للروابط النسبية.
- `target`: تحدد كيفية فتح الروابط (مثل `_blank` لفتحها في نافذة جديدة).

### التفاصيل
```html
<head>
  <base href="https://example.com/" target="_blank">
</head>
```
- **`href`**: إذا كان لديك روابط نسبية مثل `<a href="page.html">`, فسيتم اعتبار الرابط كـ `https://example.com/page.html`.
- **`target`**: تحدد سلوك فتح الروابط. القيمة الافتراضية هي `_self`، مما يعني فتح الرابط في نفس النافذة. 

## الأمثلة
### مثال بسيط
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <base href="https://example.com/">
    <title>مثال على HTMLBaseElement</title>
</head>
<body>
    <a href="about.html">حول</a>
    <a href="contact.html">اتصل بنا</a>
</body>
</html>
```
في هذا المثال، ستؤدي الروابط إلى:
- `https://example.com/about.html`
- `https://example.com/contact.html`

### مثال مع خاصية `target`
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <base href="https://example.com/" target="_blank">
    <title>مثال على HTMLBaseElement مع الهدف</title>
</head>
<body>
    <a href="about.html">حول</a>
</body>
</html>
```
في هذا المثال، عند النقر على الرابط، سيتم فتح الصفحة في نافذة جديدة.

## الشرح
### نقاط يجب الانتباه إليها
- يجب أن يكون عنصر `<base>` موجودًا في قسم `<head>`، وإذا تم استخدامه بشكل غير صحيح، فقد يؤدي إلى روابط غير صحيحة.
- لا يمكن استخدام أكثر من عنصر `<base>` في نفس الوثيقة.
- عدم تحديد `href` أو `target` سيؤدي إلى سلوك غير متوقع بالنسبة للروابط النسبية.

### ملاحظات إضافية
- عند استخدام `base` مع JavaScript، يجب أن تكون حذرًا لأن العناصر الديناميكية قد لا تستجيب كما هو متوقع إذا تم تغيير الروابط بعد تحميل الصفحة.
- `base` تعمل فقط على الروابط النسبية، لذا تأكد من اختبار الروابط في سياق المستند الكامل.

## ملخص جملة واحدة
`HTMLBaseElement` هو عنصر HTML يستخدم لتحديد عنوان أساسي للروابط النسبية في المستند، مما يسهل إدارة الروابط.